:original_name: vpc_Concepts_0012.html

.. _vpc_Concepts_0012:

Virtual IP Address
==================

You can use either IP address to enable layer 2 and layer 3 communications in a VPC, access a different VPC using peering connections, and access cloud servers through EIPs, Direct Connect connections, and VPN connections.

You can bind a virtual IP address to ECSs deployed in the active/standby pair, and then bind an EIP to the virtual IP address. Virtual IP addresses can work together with Keepalived to ensure high availability and disaster recovery. If the active ECS is faulty, the standby ECS automatically takes over services from the active one.

Networking
----------

Virtual IP addresses are used for high availability and can work together with Keepalived to make active/standby ECS switchover possible. This way if one ECS goes down for some reason, the other one can take over and services continue uninterrupted. ECSs can be configured for HA or as load balancing clusters.

-  **Networking mode 1**: HA

   To improve service availability and eliminate single points of failure, you can deploy ECSs in the active/standby pair or deploy one active ECS and multiple standby ECSs. And then, you can bind the same virtual IP address to these ECSs. If the active ECS becomes faulty, a standby ECS takes over services from the active ECS and services continue uninterrupted.


   .. figure:: /_static/images/en-us_image_0209608153.png
      :alt: **Figure 1** Networking diagram of the HA mode

      **Figure 1** Networking diagram of the HA mode

   -  As shown in the above figure, bind a virtual IP address to two ECSs in the same subnet.
   -  Configure Keepalived for the two ECSs to work in the active/standby pair. Follow industry standards for configuring Keepalived. The details are not included here.

-  **Networking mode 2**: HA load balancing cluster

   If you want to build a high-availability load balancing cluster, use Keepalived and configure LVS nodes as direct routers.


   .. figure:: /_static/images/en-us_image_0209608154.png
      :alt: **Figure 2** HA load balancing cluster

      **Figure 2** HA load balancing cluster

   -  Bind a single virtual IP address to two ECSs.
   -  Configure the two ECSs as LVS nodes working as direct routers and use Keepalived to configure the nodes in the active/standby pair. The two ECSs will evenly forward requests to different backend servers.
   -  Configure two more ECSs as backend servers.
   -  Disable the source/destination check for the two backend servers.

   Follow industry standards for configuring Keepalived. The details are not included here.

Application Scenarios
---------------------

-  Accessing the virtual IP address through an EIP

   If your application has high availability requirements and needs to provide services through the Internet, it is recommended that you bind an EIP to a virtual IP address.

-  Using a VPN, Direct Connect, or VPC peering connection to access a virtual IP address

   To ensure high availability and access to the Internet, use a VPN for security and Direct Connect for a stable connection. A VPC peering connection is needed so that two VPCs in the same region can communicate with each other.
