:original_name: vpc_0002.html

.. _vpc_0002:

IPv4 and IPv6 Dual-Stack Network
================================

What Is an IPv4/IPv6 Dual-Stack Network?
----------------------------------------

IPv4 and IPv6 dual-stack allows your resources, such as ECSs, to use both IPv4 and IPv6 addresses for private and public network communications. For example, if ECSs use the IPv4/IPv6 dual-stack network:

-  ECSs can communicate with each other using private IPv4 addresses.
-  ECSs can communicate with the Internet after they are bound with EIPs.
-  ECSs can communicate with each other using IPv6 addresses.
-  ECSs can communicate with the Internet after their IPv6 addresses are added to shared bandwidths.

.. note::

   If you select **Enable** for **IPv6 CIDR Block** when creating a subnet, an IPv6 CIDR block will be automatically assigned to the subnet.

   Basic operations on IPv4 and IPv6 dual-stack networks are the same as those on IPv4 networks, except some parameters. Check the console pages for details.

Notes and Constraints
---------------------

-  Only certain ECS specifications support IPv6 networks and can use IPv4/IPv6 dual-stack networks. You need to select such ECSs in supported regions.

   To check which ECSs support IPv6:

   -  On the ECS console: Click **Create ECS**. On the displayed page, view the ECS specifications.

      If there is the **IPv6** parameter with the value of **Yes**, the ECS specifications support IPv6.

IPv6 Application Scenarios
--------------------------

If your ECS supports IPv6, you can use the IPv4/IPv6 dual-stack network. :ref:`Table 1 <vpc_0002__table20563744105916>` shows the example application scenarios.

.. _vpc_0002__table20563744105916:

.. table:: **Table 1** Application scenarios of IPv4/IPv6 dual stack

   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Application Scenario       | Description                                                                                                                         | Requirement                                                 | IPv4 or IPv6 Subnet | ECS                                                                                                                                              |
   +============================+=====================================================================================================================================+=============================================================+=====================+==================================================================================================================================================+
   | Private IPv4 communication | Your applications on ECSs need to communicate with other systems (such as databases) through private networks using IPv4 addresses. | -  IPv6 is not enabled for the VPC subnet.                  | IPv4 CIDR Block     | **Private IPv4 address**: used for private IPv4 communication.                                                                                   |
   |                            |                                                                                                                                     | -  No EIPs have been bound to the ECSs.                     |                     |                                                                                                                                                  |
   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Public IPv4 communication  | Your applications on ECSs need to communicate with other systems (such as databases) through public IPv4 addresses.                 | -  IPv6 is not enabled for the VPC subnet.                  | IPv4 CIDR Block     | -  **Private IPv4 address**: used for private IPv4 communication.                                                                                |
   |                            |                                                                                                                                     | -  EIPs have been bound to the ECSs.                        |                     | -  **Public IPv4 address**: used for public IPv4 communication.                                                                                  |
   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Private IPv6 communication | Your applications on ECSs need to communicate with other systems (such as databases) through private IPv6 addresses.                | -  IPv6 has been enabled for the VPC subnet.                | -  IPv4 CIDR Block  | -  **Private IPv4 address + IPv4 EIP**: Bind an IPv4 EIP to the instance to allow public IPv4 communication.                                     |
   |                            |                                                                                                                                     | -  The network has been configured for the ECSs as follows: | -  IPv6 CIDR block  | -  **Private IPv4 address**: Do not bind any IPv4 EIP to the instance and use only the private IPv4 address to allow private IPv4 communication. |
   |                            |                                                                                                                                     |                                                             |                     | -  **IPv6 address**: Do not configure shared bandwidth for the IPv6 address to allow private IPv6 communication.                                 |
   |                            |                                                                                                                                     |    -  **VPC and Subnet**: IPv6-enabled subnet and VPC.      |                     |                                                                                                                                                  |
   |                            |                                                                                                                                     |    -  **Shared Bandwidth**: Selected **Do not configure**.  |                     |                                                                                                                                                  |
   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Public IPv6 communication  | An IPv6 network is required for the ECS to access the IPv6 service on the Internet.                                                 | -  IPv6 has been enabled for the VPC subnet.                | -  IPv4 CIDR Block  | -  **Private IPv4 address + IPv4 EIP**: Bind an IPv4 EIP to the instance to allow public IPv4 communication.                                     |
   |                            |                                                                                                                                     | -  The network has been configured for the ECSs as follows: | -  IPv6 CIDR block  | -  **Private IPv4 address**: Do not bind any IPv4 EIP to the instance and use only the private IPv4 address to allow private IPv4 communication. |
   |                            |                                                                                                                                     |                                                             |                     |                                                                                                                                                  |
   |                            |                                                                                                                                     |    -  **VPC and Subnet**: IPv6-enabled subnet and VPC.      |                     | -  **IPv6 address + shared bandwidth**: Allow both private IPv6 communication and public IPv6 communication.                                     |
   |                            |                                                                                                                                     |    -  **Shared Bandwidth**: Selected a shared bandwidth.    |                     |                                                                                                                                                  |
   +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Application scenarios of IPv6 EIPs

   +-------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Application Scenario                      | Description                                                                                                    | Subnet          | ECS                                                                                              |
   +===========================================+================================================================================================================+=================+==================================================================================================+
   | Public communication using IPv6 addresses | Your applications deployed on ECSs need to provide services accessible from the Internet using IPv6 addresses. | IPv4 CIDR block | -  Private IPv4 address                                                                          |
   |                                           |                                                                                                                |                 | -  IPv4 EIP (with IPv6 function enabled): used for public communication using IPv4 and IPv6 EIPs |
   +-------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------------------------------------------------+

Basic Operations
----------------

**Creating an IPv6 Subnet**

Create an IPv6 subnet by following the instructions in :ref:`Creating a Subnet for the VPC <en-us_topic_0013748726>`. Select **Enable** for **IPv6 CIDR Block**. An IPv6 CIDR block will be automatically assigned to the subnet. IPv6 cannot be disabled after the subnet is created.

To disable this function, call the API by referring to `Updating Subnet Information <https://docs.sc.otc.t-systems.com/virtual-private-cloud/api-ref/apis/subnet/updating_subnet_information.html#vpc-subnet01-0004>`__.

**Viewing In-Use IPv6 Addresses**

In the subnet list, click the subnet name. On the displayed page, view in-use IPv4 and IPv6 addresses on the **IP Addresses** tab.

**Adding a Security Group Rule (IPv6)**

Add a security group rule with **Type** set to **IPv6** and **Source** or **Destination** set to an IPv6 address or IPv6 CIDR block.

Adding an IPv6 Firewall Rule

Add a firewall rule with **Type** set to **IPv6** and **Source** or **Destination** set to an IPv6 address or IPv6 CIDR block.

**Adding a Route (IPv6)**

Add a route with **Destination** and **Next Hop** set to an IPv4 or IPv6 CIDR block. For details about how to add a route, see :ref:`Adding a Custom Route <vpc_route01_0006>`. If the destination is an IPv6 CIDR block, the next hop can only be an IP address in the same VPC as the IPv6 CIDR block.

.. note::

   If the destination is an IPv6 CIDR block, the next hop type can only be an ECS, extension NIC, or virtual IP address. The next hop must also have IPv6 addresses.

**Assigning an IPv6 Virtual IP Address**

Assign a virtual IPv4 or IPv6 address by referring to :ref:`Assigning a Virtual IP Address <vpc_vip_0002>`.

.. note::

   Each virtual IPv6 address can only be bound to one dual-stack network interface.

**Dynamically Assigning IPv6 Addresses**

After an ECS is created successfully, you can view the assigned IPv6 address on the ECS details page. You can also log in to the ECS and run the **ifconfig** command to view the assigned IPv6 address.

If an IPv6 address fails to be automatically assigned or the selected image does not support the function of automatic IPv6 address assignment, manually obtain the IPv6 address by referring to section "Dynamically Assigning IPv6 Addresses" in *Elastic Cloud Server User Guide*.

.. note::

   If an ECS is created from a public image:

   Before enabling dynamic IPv6 address assignment for a Linux public image, check whether IPv6 is supported and then check whether dynamic IPv6 address assignment has been enabled. Currently, all Linux public images support IPv6, and dynamic IPv6 address assignment is enabled for Ubuntu 16 by default. You do not need to configure dynamic IPv6 address assignment for the Ubuntu 16 OS. For other Linux public images, you need to enable this function.
