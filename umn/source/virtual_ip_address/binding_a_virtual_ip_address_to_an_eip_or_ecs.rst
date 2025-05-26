:original_name: en-us_topic_0067802474.html

.. _en-us_topic_0067802474:

Binding a Virtual IP Address to an EIP or ECS
=============================================

Scenarios
---------

You can use a virtual IP address and an EIP together.

If you bind a virtual IP address to ECSs that work in active/standby pairs and bind an EIP to the virtual IP address, you can access the ECSs over the Internet.

Notes and Constraints
---------------------

-  A virtual IP address can only be bound to one EIP.
-  It is recommended that no more than eight virtual IP addresses be bound to an ECS.
-  A virtual IP address can be bound to up to ten ECSs.

   .. note::

      When a virtual IP address is bound to an ECS, the virtual IP address is also associated with the security group of the ECS. A virtual IP address can be associated with up to 10 security groups.

Binding a Virtual IP Address to an EIP or ECS on the Console
------------------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, click **Subnets**.

   The **Subnets** page is displayed.

#. Click the name with a hyperlink of the subnet that the virtual IP address belongs to.

   The subnet details page is displayed.

#. Click the **IP Addresses** tab.

   -  To bind a virtual IP address to an EIP, locate the row that contains the virtual IP address and click **Bind to EIP** in the **Operation** column.
   -  To bind a virtual IP address to an ECS, locate the row that contains the virtual IP address and click **More** > **Bind to Server** in the **Operation** column.

#. Select the EIP or ECS to be bound.

   .. note::

      -  If an ECS has multiple NICs, bind the virtual IP address to the primary NIC.
      -  An ECS NIC can have multiple virtual IP addresses bound.

#. Click **OK**.

   .. important::

      After a virtual IP address is bound to an ECS NIC, you need to manually configure the virtual IP address on the ECS. For details, see :ref:`Configuring a Virtual IP Address for an ECS <en-us_topic_0067802474__section480517024620>`.

.. _en-us_topic_0067802474__section480517024620:

Configuring a Virtual IP Address for an ECS
-------------------------------------------

Manually configure the virtual IP address bound to an ECS.

The following OSs are used as examples here. For other OSs, see the help documents on their official websites.

-  Linux: CentOS 7.2 64bit and Ubuntu 22.04 server 64bit
-  Windows: Windows Server

**Linux (CentOS 7.2 64bit is used as an example.)**

#. .. _en-us_topic_0067802474__li528316578916:

   Obtain the NIC that the virtual IP address is to be bound and the connection of the NIC:

   **nmcli connection**

   Information similar to the following is displayed:

   |image3|

   The command output in this example is described as follows:

   -  **eth0** in the **DEVICE** column indicates the NIC that the virtual IP address is to be bound.
   -  **Wired connection 1** in the **NAME** column indicates the connection of the NIC.

#. .. _en-us_topic_0067802474__li20283257695:

   Add the virtual IP address for the connection:

   **nmcli connection modify "**\ *Connection name of the NIC*\ **"** **+ipv4.addresses** *Virtual IP address*

   Configure the parameters as follows:

   -  *Connection name of the NIC*: The connection name of the NIC obtained in :ref:`1 <en-us_topic_0067802474__li528316578916>`. In this example, the connection name is **Wired connection 1**.
   -  *Virtual IP address*: Enter the virtual IP address to be added. If you add multiple virtual IP addresses at a time, separate every two with a comma (,).

   Example commands:

   -  Adding a single virtual IP address: **nmcli connection modify "Wired connection 1" +ipv4.addresses** **172.16.0.125**
   -  Adding multiple virtual IP addresses: **nmcli connection modify "Wired connection 1" +ipv4.addresses** **172.16.0.125,172.16.0.126**

#. .. _en-us_topic_0067802474__li11209933188:

   Make the configuration in :ref:`2 <en-us_topic_0067802474__li20283257695>` take effect:

   **nmcli connection up "**\ *Connection name of the NIC*\ **"**

   In this example, run the following command:

   **nmcli connection up "Wired connection 1"**

   Information similar to the following is displayed:

   |image4|

#. Check whether the virtual IP address has been bound:

   **ip a**

   Information similar to the following is displayed. In the command output, the virtual IP address 172.16.0.125 is bound to NIC eth0.

   |image5|

   .. note::

      To delete an added virtual IP address, perform the following steps:

      a. Delete the virtual IP address from the connection of the NIC:

         **nmcli connection modify "**\ *Connection name of the NIC*\ **"** **-ipv4.addresses** *Virtual IP address*

         To delete multiple virtual IP addresses at a time, separate every two with a comma (,). Example commands are as follows:

         -  Deleting a single virtual IP address: **nmcli connection modify "Wired connection 1" -ipv4.addresses** **172.16.0.125**
         -  Deleting multiple virtual IP addresses: **nmcli connection modify "Wired connection 1" -ipv4.addresses** **172.16.0.125,172.16.0.126**

      b. Make the deletion take effect by referring to :ref:`3 <en-us_topic_0067802474__li11209933188>`.

**Linux (Ubuntu 22.04 server 64bit is used as an example.)**

For Ubuntu 22 or Ubuntu 20 ECSs, perform the following operations:

#. Obtain the NIC that the virtual IP address is to be bound:

   **ifconfig**

   Information similar to the following is displayed. In this example, the NIC bound to the virtual IP address is **eth0**.

   .. code-block::

      root@ecs-X-ubantu:~# ifconfig
      eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
              inet 172.16.0.210  netmask 255.255.255.0  broadcast 172.16.0.255
              inet6 fe80::f816:3eff:fe01:f1c3  prefixlen 64  scopeid 0x20<link>
              ether fa:16:3e:01:f1:c3  txqueuelen 1000  (Ethernet)
              RX packets 43915  bytes 63606486 (63.6 MB)
              RX errors 0  dropped 0  overruns 0  frame 0
              TX packets 3364  bytes 455617 (455.6 KB)
              TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
      ...

#. Switch to the **/etc/netplan** directory:

   **cd /etc/netplan**

#. .. _en-us_topic_0067802474__li1244016171484:

   Add a virtual IP address to the NIC.

   a. Open the configuration file **01-netcfg.yaml**:

      **vim 01-netcfg.yaml**

   b. Press **i** to enter the editing mode.

   c. In the NIC configuration area, add a virtual IP address.

      In this example, add a virtual IP address for **eth0**:

      **addresses:**

      **- 172.16.0.26/32**

      The file content is as follows:

      .. code-block::

         network:
             version: 2
             renderer: NetworkManager
             ethernets:
                 eth0:
                     dhcp4: true
                     addresses:
                     - 172.16.0.26/32
                 eth1:
                     dhcp4: true
                 eth2:
                     dhcp4: true
                 eth3:
                     dhcp4: true
                 eth4:
                     dhcp4: true

   d. Press **Esc**, enter **:wq!**, save the configuration, and exit.

#. .. _en-us_topic_0067802474__li1071922334218:

   Make the configuration in :ref:`3 <en-us_topic_0067802474__li1244016171484>` take effect:

   **netplan apply**

#. Check whether the virtual IP address has been bound:

   **ip a**

   Information similar to the following is displayed. In the command output, the virtual IP address 172.16.0.26 is bound to NIC eth0.

   .. code-block::

      root@ecs-X-ubantu:/etc/netplan# ip a
      ...
      2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
          link/ether fa:16:3e:01:f1:c3 brd ff:ff:ff:ff:ff:ff
          altname enp0s3
          altname ens3
          inet 172.16.0.26/32 scope global noprefixroute eth0
             valid_lft forever preferred_lft forever
          inet 172.16.0.210/24 brd 172.16.0.255 scope global dynamic noprefixroute eth0
             valid_lft 107999971sec preferred_lft 107999971sec
          inet6 fe80::f816:3eff:fe01:f1c3/64 scope link
             valid_lft forever preferred_lft forever

   .. note::

      To delete an added virtual IP address, perform the following steps:

      a. Open the configuration file **01-netcfg.yaml** and delete the virtual IP address of the corresponding NIC by referring to :ref:`3 <en-us_topic_0067802474__li1244016171484>`.
      b. Make the deletion take effect by referring to :ref:`4 <en-us_topic_0067802474__li1071922334218>`.

**Windows OS** **(Windows Server is used as an example here.)**

#. In **Control Panel**, click **Network and Sharing Center**, and click the corresponding local connection.

#. On the displayed page, click **Properties**.

#. On the **Network** tab page, select **Internet Protocol Version 4 (TCP/IPv4)**.

#. Click **Properties**.

#. Select **Use the following IP address** and set **IP address** to the private IP address of the ECS, for example, 10.0.0.101.


   .. figure:: /_static/images/en-us_image_0000001818823142.png
      :alt: **Figure 1** Configuring private IP address

      **Figure 1** Configuring private IP address

#. Click **Advanced**.

#. On the **IP Settings** tab, click **Add** in the **IP addresses** area.

   Add the virtual IP address, for example, 10.0.0.154.


   .. figure:: /_static/images/en-us_image_0000001818982934.png
      :alt: **Figure 2** Configuring virtual IP address

      **Figure 2** Configuring virtual IP address

#. Click **OK**.

#. In the **Start** menu, open the Windows command line window and run the following command to check whether the virtual IP address has been configured:

   **ipconfig /all**

   In the command output, **IPv4 Address** is the virtual IP address 10.0.0.154, indicating that the virtual IP address of the ECS NIC has been correctly configured.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582673.png
.. |image3| image:: /_static/images/en-us_image_0000001818982930.png
.. |image4| image:: /_static/images/en-us_image_0000001865582677.png
.. |image5| image:: /_static/images/en-us_image_0000001818823138.png
