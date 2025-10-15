:original_name: vpc_route_0004.html

.. _vpc_route_0004:

Configuring an SNAT Server
==========================

Scenarios
---------

Together with VPC route tables, you can configure SNAT on an ECS to enable other ECSs that have no EIPs bound in the same VPC to access the Internet through this ECS.

The configured SNAT takes effect for all subnets in a VPC.

Prerequisites
-------------

-  You have an ECS where SNAT is to be configured.
-  The ECS where SNAT is to be configured runs Linux.
-  The ECS where SNAT is to be configured has only one network interface.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. In the upper left corner of the page, click |image2|. In the service list, choose **Computing** > **Elastic Cloud Server**.

#. On the displayed page, locate the target ECS in the ECS list and click the ECS name to switch to the page showing ECS details.

#. On the displayed ECS details page, click the **Network Interfaces** tab.

#. Click the network interface's IP address to view details and disable **Source/Destination Check**.

   This prevents packet spoofing and improves system security. If SNAT is used, the SNAT server needs to forward packets. This mechanism prevents the packet sender from receiving returned packets. To change this behavior, you can disable the source/destination check for SNAT servers.

#. Bind an EIP.

   -  Bind an EIP to the private IP address of the ECS. For details, see :ref:`Assigning an EIP and Binding It to an ECS <en-us_topic_0013748738>`.
   -  Bind an EIP to the virtual IP address of the ECS. For details, see :ref:`Binding a Virtual IP Address to an EIP or ECS <en-us_topic_0067802474>`.

#. On the ECS console, use the remote login function to log in to the ECS where you plan to configure SNAT.

#. Run the following command and enter the password of user **root** to switch to user **root**:

   **su - root**

#. Run the following command to check whether the ECS can successfully connect to the Internet:

   .. note::

      Before running the command, you must disable the response iptables rule on the ECS where SNAT is configured and configure security group rules.

   **ping www.google.com**

   The ECS can access the Internet if the following information is displayed:

   .. code-block:: console

      [root@localhost ~]# ping www.google.com
      PING www.google.com (xxx.xxx.xxx.xxx) 56(84) bytes of data.
      64 bytes from xxx.xxx.xxx.xxx: icmp_seq=1 ttl=51 time=9.34 ms
      64 bytes from xxx.xxx.xxx.xxx: icmp_seq=2 ttl=51 time=9.11 ms
      64 bytes from xxx.xxx.xxx.xxx: icmp_seq=3 ttl=51 time=8.99 ms

#. Run the following command to check whether IP forwarding of the Linux OS is enabled:

   **cat /proc/sys/net/ipv4/ip_forward**

   In the command output, **1** indicates that IP forwarding is enabled, and **0** indicates that IP forwarding is disabled. The default value is **0**.

   -  If IP forwarding in Linux is enabled, go to step :ref:`14 <vpc_route_0004__en-us_topic_0212076959_li2168883919851>`.
   -  If IP forwarding in Linux is disabled, go to :ref:`12 <vpc_route_0004__en-us_topic_0212076959_li3948189019612>` to enable IP forwarding in Linux.

   Many OSs support packet routing. Before forwarding packets, OSs change source IP addresses in the packets to OS IP addresses. Therefore, the forwarded packets contain the IP address of the public sender so that the response packets can be sent back along the same path to the initial packet sender. This method is called SNAT. The OSs need to keep track of the packets where IP addresses have been changed to ensure that the destination IP addresses in the packets can be rewritten and that packets can be forwarded to the initial packet sender. To achieve these purposes, you need to enable the IP forwarding function and configure SNAT rules.

#. .. _vpc_route_0004__en-us_topic_0212076959_li3948189019612:

   Use the vi editor to open the **/etc/sysctl.conf** file, change the value of **net.ipv4.ip_forward** to **1**, and enter **:wq** to save the change and exit.

#. Run the following command to make the change take effect:

   **sysctl -p /etc/sysctl.conf**

#. .. _vpc_route_0004__en-us_topic_0212076959_li2168883919851:

   Configure the SNAT function.

   Run the following command to enable all ECSs on the network (for example, 192.168.1.0/24) to access the Internet using the SNAT function:

   **iptables -t nat -A POSTROUTING -o eth0 -s subnet -j SNAT --to nat-instance-ip**


   .. figure:: /_static/images/en-us_image_0000001818983066.png
      :alt: **Figure 1** Configuring SNAT

      **Figure 1** Configuring SNAT

   .. note::

      To ensure that the rule will not be lost after the restart, write the rule into the **/etc/rc.local** file.

      a. Switch to the **/etc/sysctl.conf** file:

         **vi /etc/rc.local**

      b. Perform :ref:`14 <vpc_route_0004__en-us_topic_0212076959_li2168883919851>` to configure SNAT.

      c. Save the configuration and exit:

         **:wq**

      d. Add the execution permissions for the **rc.local** file:

         **# chmod +x /etc/rc.local**

#. Check whether the configuration is successful. If information similar to :ref:`Figure 2 <vpc_route_0004__en-us_topic_0212076959_fig8358771201535>` (for example, 192.168.1.0/24) is displayed, the configuration was successful.

   **iptables -t nat --list**

   .. _vpc_route_0004__en-us_topic_0212076959_fig8358771201535:

   .. figure:: /_static/images/en-us_image_0000001818823278.png
      :alt: **Figure 2** Verifying configuration

      **Figure 2** Verifying configuration

#. Add a route. For details, see section :ref:`Adding a Custom Route <vpc_route01_0006>`.

   Set the destination to **0.0.0.0/0**, and the next hop to the private or virtual IP address of the ECS where SNAT is deployed. For example, the next hop is **192.168.1.4**.

After these operations are complete, if the network communication still fails, check your security group and firewall configuration to see whether required traffic is allowed.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582817.png
