:original_name: vpc_vip02_0001.html

.. _vpc_vip02_0001:

Virtual IP Address Overview
===========================

What Is a Virtual IP Address?
-----------------------------

A virtual IP address can be shared among multiple ECSs. An ECS can have both private and virtual IP addresses, and you can access the ECS through either IP address. A virtual IP address has the same network access capabilities as a private IP address, including layer 2 and layer 3 communication in VPCs, access between VPCs using VPC peering connections, as well as access through EIPs, VPN connections, and Direct Connect connections.

You can bind ECSs deployed in active/standby mode with the same virtual IP address, and then bind an EIP to the virtual IP address. Virtual IP addresses can work together with Keepalived to ensure high availability and disaster recovery. If the active ECS is faulty, the standby ECS automatically takes over services from the active one.

Networking
----------

Virtual IP addresses are used for high availability and can work together with Keepalived to make active/standby ECS switchover possible. This way if one ECS goes down for some reason, the other one can take over and services continue uninterrupted. ECSs can be configured for HA or as load balancing clusters.

-  **Networking mode 1**: HA

   If you want to improve service availability and avoid single points of failure, you can deploy ECSs in the active/standby mode or deploy one active ECS and multiple standby ECSs. In this arrangement, the ECSs all use the same virtual IP address. If the active ECS becomes faulty, a standby ECS takes over services from the active ECS and services continue uninterrupted.


   .. figure:: /_static/images/en-us_image_0209608153.png
      :alt: **Figure 1** Networking diagram of the HA mode

      **Figure 1** Networking diagram of the HA mode

   -  In this configuration, a single virtual IP address is bound to two ECSs in the same subnet.
   -  Keepalived is then used to configure the two ECSs to work in the active/standby mode. Follow industry standards for configuring Keepalived. The details are not included here.

-  **Networking mode 2**: HA load balancing cluster

   If you want to build a high-availability load balancing cluster, use Keepalived and configure LVS nodes as direct routers.


   .. figure:: /_static/images/en-us_image_0209608154.png
      :alt: **Figure 2** HA load balancing cluster

      **Figure 2** HA load balancing cluster

   -  Bind a single virtual IP address to two ECSs.
   -  Configure the two ECSs as LVS nodes working as direct routers and use Keepalived to configure the nodes in the active/standby mode. The two ECSs will evenly forward requests to different backend servers.
   -  Configure two more ECSs as backend servers.
   -  Disable the source/destination check for the two backend servers.

   Follow industry standards for configuring Keepalived. The details are not included here.

Application Scenarios
---------------------

-  Accessing the virtual IP address through an EIP

   If your application has high availability requirements and needs to provide services through the Internet, it is recommended that you bind an EIP to a virtual IP address.

-  Using a VPN, Direct Connect, or VPC peering connection to access a virtual IP address

   To ensure high availability and access to the Internet, use a VPN for security and Direct Connect for a stable connection. The VPC peering connection is needed so that the VPCs in the same region can communicate with each other.

Precautions
-----------

-  Virtual IP addresses are not recommended when multiple NICs in the same subnet are configured on an ECS. It is too easy for there to be route conflicts on the ECS, which would cause communication failure using the virtual IP address.
-  IP forwarding must be disabled on the standby ECS. Perform the following operations to confirm whether the IP forwarding is disabled on the standby ECS:

   #. Log in to standby ECS and run the following command to check whether the IP forwarding is enabled:

      cat /proc/sys/net/ipv4/ip_forward

      In the command output, **1** indicates it is enabled, and **0** indicates it is disabled. The default value is **0**.

      -  If the command output is **1**, perform :ref:`2 <vpc_vip02_0001__en-us_topic_0118498951_en-us_topic_0206027322_en-us_topic_0095139658_li1473585332417>` and :ref:`3 <vpc_vip02_0001__en-us_topic_0118498951_en-us_topic_0206027322_en-us_topic_0095139658_li88984711254>` to disable the IP forwarding.
      -  If the command output is **0**, no further action is required.

   #. .. _vpc_vip02_0001__en-us_topic_0118498951_en-us_topic_0206027322_en-us_topic_0095139658_li1473585332417:

      Use the vi editor to open the **/etc/sysctl.conf** file, change the value of **net.ipv4.ip_forward** to **0**, and enter **:wq** to save the change and exit. You can also use the **sed** command to modify the configuration. A command example is as follows:

      sed -i '/net.ipv4.ip_forward/s/1/0/g' /etc/sysctl.conf

   #. .. _vpc_vip02_0001__en-us_topic_0118498951_en-us_topic_0206027322_en-us_topic_0095139658_li88984711254:

      Run the following command to make the change take effect:

      sysctl -p /etc/sysctl.conf

-  It is recommended that no more than eight virtual IP addresses be bound to an ECS.
-  A virtual IP address can be bound to up to 10 ECSs.

   .. note::

      If you bind a virtual IP address to an ECS, the virtual IP address is also associated with the security groups of the ECS. A virtual IP address can be associated with up to 10 security groups.
