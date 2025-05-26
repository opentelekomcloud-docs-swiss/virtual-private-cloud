:original_name: vpc_faq_0069.html

.. _vpc_faq_0069:

Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection?
========================================================================================

Symptom
-------

After a VPC peering connection is created, the local and peer VPCs cannot communicate with each other.

Troubleshooting
---------------

The issues here are described in order of how likely they are to occur.

.. table:: **Table 1** Possible causes and solutions

   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | No.                   | Possible Cause                                                                                         | Solution                                                                                                   |
   +=======================+========================================================================================================+============================================================================================================+
   | 1                     | Overlapping CIDR blocks of local and peer VPCs                                                         | Refer to :ref:`Overlapping CIDR Blocks of Local and Peer VPCs <vpc_faq_0069__section18800459153612>`.      |
   |                       |                                                                                                        |                                                                                                            |
   |                       | -  All their subnet CIDR blocks overlap.                                                               |                                                                                                            |
   |                       | -  Some of their subnet CIDR blocks overlap.                                                           |                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 2                     | Incorrect route configuration for the local and peer VPCs                                              | Refer to :ref:`Incorrect Route Configuration for Local and Peer VPCs <vpc_faq_0069__section582181993814>`. |
   |                       |                                                                                                        |                                                                                                            |
   |                       | -  No routes are added.                                                                                |                                                                                                            |
   |                       | -  Incorrect routes are added.                                                                         |                                                                                                            |
   |                       | -  Destinations of the routes overlap with that configured for Direct Connect or VPN connections.      |                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 3                     | Incorrect network configuration                                                                        | Refer to :ref:`Incorrect Network Configuration <vpc_faq_0069__section157663413717>`.                       |
   |                       |                                                                                                        |                                                                                                            |
   |                       | -  The security group rules of the ECSs that need to communicate deny inbound traffic from each other. |                                                                                                            |
   |                       | -  The firewall of the ECS NIC blocks traffic.                                                         |                                                                                                            |
   |                       | -  The firewall rules of the subnets connected by the VPC peering connection deny inbound traffic.     |                                                                                                            |
   |                       | -  Check the policy-based routing configuration of an ECS with multiple NICs.                          |                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 4                     | ECS network failure                                                                                    | Refer to :ref:`ECS Network Failure <vpc_faq_0069__section8357923710>`.                                     |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

.. _vpc_faq_0069__section18800459153612:

Overlapping CIDR Blocks of Local and Peer VPCs
----------------------------------------------

If the CIDR blocks of VPCs connected by a VPC peering connection overlap, the connection may not take effect due to route conflicts.

.. table:: **Table 2** Overlapping CIDR blocks of local and peer VPCs

   +---------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                                        | Description                                                                                                                                 | Solution                                                                                                                                                     |
   +=================================================================================+=============================================================================================================================================+==============================================================================================================================================================+
   | VPCs with overlapping CIDR blocks also include subnets that overlap.            | As shown in :ref:`Figure 1 <vpc_faq_0069__fig465519155457>`, the CIDR blocks of VPC-A and VPC-B overlap, and all their subnets overlap.     | VPC-A and VPC-B cannot be connected using a VPC peering connection.                                                                                          |
   |                                                                                 |                                                                                                                                             |                                                                                                                                                              |
   |                                                                                 | -  Overlapping CIDR blocks of VPC-A and VPC-B: 10.0.0.0/16                                                                                  | Replan the network.                                                                                                                                          |
   |                                                                                 | -  Overlapping CIDR blocks of Subnet-A01 in VPC-A and Subnet-B01 in VPC-B: 10.0.0.0/24                                                      |                                                                                                                                                              |
   |                                                                                 | -  Overlapping CIDR blocks of Subnet-A02 in VPC-A and Subnet-B02 in VPC-B: 10.0.1.0/24                                                      |                                                                                                                                                              |
   +---------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Two VPCs have overlapping CIDR blocks but some of their subnets do not overlap. | As shown in :ref:`Figure 2 <vpc_faq_0069__fig098452131910>`, the CIDR blocks of VPC-A and VPC-B overlap, and some of their subnets overlap. | -  A VPC peering connection cannot connect the entire VPCs,                                                                                                  |
   |                                                                                 |                                                                                                                                             |                                                                                                                                                              |
   |                                                                                 | -  Overlapping CIDR blocks of VPC-A and VPC-B: 10.0.0.0/16                                                                                  |    VPC-A and VPC-B.                                                                                                                                          |
   |                                                                                 | -  Overlapping CIDR blocks of Subnet-A01 in VPC-A and Subnet-B01 in VPC-B: 10.0.0.0/24                                                      |                                                                                                                                                              |
   |                                                                                 | -  CIDR blocks of Subnet-A02 in VPC-A and Subnet-B02 in VPC-B do not overlap.                                                               | -  A connection can connect their subnets (Subnet-A02 and Subnet-B02) that do not overlap. For details, see :ref:`Figure 3 <vpc_faq_0069__fig920231311415>`. |
   +---------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_faq_0069__fig465519155457:

.. figure:: /_static/images/en-us_image_0000001818982898.png
   :alt: **Figure 1** Networking diagram (IPv4)

   **Figure 1** Networking diagram (IPv4)

.. _vpc_faq_0069__fig098452131910:

.. figure:: /_static/images/en-us_image_0000001818983474.png
   :alt: **Figure 2** Networking diagram (IPv4)

   **Figure 2** Networking diagram (IPv4)

If CIDR blocks of VPCs overlap and some of their subnets overlap, you can create a VPC peering connection between their subnets with non-overlapping CIDR blocks. :ref:`Figure 3 <vpc_faq_0069__fig920231311415>` shows the networking diagram of connecting Subnet-A02 and Subnet-B02. :ref:`Table 3 <vpc_faq_0069__table45541823135611>` describes the routes required.

.. _vpc_faq_0069__fig920231311415:

.. figure:: /_static/images/en-us_image_0000001818823702.png
   :alt: **Figure 3** Networking diagram (IPv4)

   **Figure 3** Networking diagram (IPv4)

.. _vpc_faq_0069__table45541823135611:

.. table:: **Table 3** Routes required for the VPC peering connection between Subnet-A02 and Subnet-B02

   +-------------------+-------------+------------+--------------------------------------------------------------------------------------------------+
   | Route Table       | Destination | Next Hop   | Description                                                                                      |
   +===================+=============+============+==================================================================================================+
   | VPC-A route table | 10.0.2.0/24 | Peering-AB | Add a route with the CIDR block of Subnet-B02 as the destination and Peering-AB as the next hop. |
   +-------------------+-------------+------------+--------------------------------------------------------------------------------------------------+
   | VPC-B route table | 10.0.1.0/24 | Peering-AB | Add a route with the CIDR block of Subnet-A02 as the destination and Peering-AB as the next hop. |
   +-------------------+-------------+------------+--------------------------------------------------------------------------------------------------+

.. _vpc_faq_0069__section582181993814:

Incorrect Route Configuration for Local and Peer VPCs
-----------------------------------------------------

:ref:`Viewing Routes Configured for a VPC Peering Connection <vpc_peering_0004>`. :ref:`Table 4 <vpc_faq_0069__table513212558272>` lists the items that you need to check.

.. _vpc_faq_0069__table513212558272:

.. table:: **Table 4** Route check items

   +------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                                                                                                                                                             | Solution                                                                                                                                                                         |
   +==================================================================================================================================================================+==================================================================================================================================================================================+
   | Check whether routes are added to the route tables of the local and peer VPCs.                                                                                   | If routes are not added, add routes by referring to:                                                                                                                             |
   |                                                                                                                                                                  |                                                                                                                                                                                  |
   |                                                                                                                                                                  | -  :ref:`Creating a VPC Peering Connection with Another VPC in Your Account <en-us_topic_0046655037>`                                                                            |
   +------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Check the destinations of routes added to the route tables of the local and peer VPCs.                                                                           | If the route destination is incorrect, change it.                                                                                                                                |
   |                                                                                                                                                                  |                                                                                                                                                                                  |
   | -  In the route table of the local VPC, check whether the route destination is the CIDR block, subnet CIDR block, or related private IP address of the peer VPC. |                                                                                                                                                                                  |
   | -  In the route table of the peer VPC, check whether the route destination is the CIDR block, subnet CIDR block, or related private IP address of the local VPC. |                                                                                                                                                                                  |
   +------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Destinations of the routes overlap with that configured for Direct Connect or VPN connections.                                                                   | Check whether any of the VPCs connected by the VPC peering connection also has a VPN or Direct Connect connection connected. If they do, check the destinations of their routes. |
   |                                                                                                                                                                  |                                                                                                                                                                                  |
   |                                                                                                                                                                  | If the destinations of the routes overlap, the VPC peering connection does not take effect. In this case, replan the network connection.                                         |
   +------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_faq_0069__section157663413717:

Incorrect Network Configuration
-------------------------------

#. Check whether the security group rules of the ECSs that need to communicate with each other are correctly configured. For details, see :ref:`Viewing the Security Group of an ECS <vpc_securitygroup_0011>`.

   -  If the ECSs are associated with the same security group, you do not need to check their rules.
   -  If the ECSs are in different security groups, you need to add inbound rules to allow access from the peer security group. For details, see :ref:`Security Group Configuration Examples <en-us_topic_0081124350>`.

#. Check whether the firewall of the ECS NIC blocks traffic.

   If the firewall blocks traffic, configure the firewall to allow inbound traffic.

#. Check whether firewall rules of the subnets connected by the VPC peering connection deny inbound traffic.

   If the firewall rules deny inbound traffic, configure the rules to allow the traffic.

#. If an ECS has more than one NIC, check whether correct policy-based routing has been configured for the ECS and packets with different source IP addresses match their own routes from each NIC.

   If an ECS has two NICs (eth0 and eth1):

   -  IP address of eth0: 192.168.1.10; Subnet gateway: 192.168.1.1
   -  IP address of eth1: 192.168.2.10; Subnet gateway: 192.168.2.1

   Command format:

   -  **ping -l** *IP address of eth0 Subnet gateway address of eth0*
   -  **ping -l** *IP address of eth1 Subnet gateway address of eth1*

   Run the following commands:

   -  **ping -I 192.168.1.10 192.168.1.1**
   -  **ping -I 192.168.2.10 192.168.2.1**

   If the network communication is normal, the routes of the NICs are correctly configured.

.. _vpc_faq_0069__section8357923710:

ECS Network Failure
-------------------

#. Log in to the ECS.
#. Check whether the ECS NIC has an IP address assigned.

   -  Linux ECS: Use the **ifconfig** or **ip address** command to view the IP address of the NIC.
   -  Windows ECS: In the search box, enter **cmd** and press **Enter**. In the displayed command prompt, run the **ipconfig** command.

#. Check whether the subnet gateway of the ECS can be pinged.

   a. In the ECS list, click the ECS name.

      The ECS details page is displayed.

   b. On the ECS details page, click the hyperlink of VPC.

      The **Virtual Private Cloud** page is displayed.

   c. In the VPC list, locate the target VPC and click the number in the **Subnets** column.

      The **Subnets** page is displayed.

   d. In the subnet list, click the subnet name.

      The subnet details page is displayed.

   e. Click the **IP Addresses** tab and view the gateway address of the subnet.

   f. Check whether the gateway communication is normal:

      **ping** *Subnet gateway address*

      Example command: **ping 172.17.0.1**
