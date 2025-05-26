:original_name: en-us_topic_0046809840.html

.. _en-us_topic_0046809840:

VPC Peering Connection Usage Examples
=====================================

A VPC peering connection is a networking connection between two VPCs in the same region and enables them to communicate. :ref:`Table 1 <en-us_topic_0046809840__table18339193642913>` lists different scenarios of using VPC peering connections.

.. _en-us_topic_0046809840__table18339193642913:

.. table:: **Table 1** VPC peering connection usage examples

   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Location                | CIDR Block                                    | Description                                                                                                                                    | Usage Example                                                                                                     |
   +=========================+===============================================+================================================================================================================================================+===================================================================================================================+
   | VPCs in the same region | -  VPC CIDR blocks do not overlap.            | You can create VPC peering connections to connect entire CIDR blocks of VPCs. Then, all resources in the VPCs can communicate with each other. | -  :ref:`Peering Two or More VPCs <en-us_topic_0046809840__section1450741418179>`                                 |
   |                         | -  Subnet CIDR blocks of VPCs do not overlap. |                                                                                                                                                | -  :ref:`Peering One Central VPC with Multiple VPCs <en-us_topic_0046809840__section51284316142>`                 |
   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | VPCs in the same region | -  VPC CIDR blocks overlap.                   | You can create VPC peering connections to connect specific subnets or ECSs from different VPCs.                                                | -  :ref:`Peering Two VPCs with Overlapping CIDR Blocks <en-us_topic_0046809840__section6703221192012>`            |
   |                         | -  Some subnet CIDR blocks overlap.           |                                                                                                                                                | -  :ref:`Peering ECSs in a Central VPC with ECSs in Two Other VPCs <en-us_topic_0046809840__section654114220445>` |
   |                         |                                               | -  To connect specific subnets from two VPCs, the subnet CIDR blocks cannot overlap.                                                           |                                                                                                                   |
   |                         |                                               | -  To connect specific ECSs from two VPCs, each ECS must have a unique private IP address.                                                     |                                                                                                                   |
   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | VPCs in the same region | -  VPC CIDR blocks overlap.                   | VPC peering connections are not usable.                                                                                                        | -  :ref:`Invalid VPC Peering Connections <en-us_topic_0046809840__section0306616175518>`                          |
   |                         | -  All subnet CIDR blocks overlap.            |                                                                                                                                                |                                                                                                                   |
   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0046809840__section1450741418179:

Peering Two or More VPCs
------------------------

-  Two VPCs peered together: :ref:`Figure 1 <en-us_topic_0046809840__fig465519155457>` shows the networking diagram of a VPC peering connection that connects VPC-A and VPC-B.

   .. _en-us_topic_0046809840__fig465519155457:

   .. figure:: /_static/images/en-us_image_0000001865662841.png
      :alt: **Figure 1** Networking diagram (IPv4)

      **Figure 1** Networking diagram (IPv4)

   .. table:: **Table 2** Peering relationships (IPv4)

      =========================== ======================= ========= ========
      Peering Relationship        Peering Connection Name Local VPC Peer VPC
      =========================== ======================= ========= ========
      VPC-A is peered with VPC-B. Peering-AB              VPC-A     VPC-B
      =========================== ======================= ========= ========

   .. table:: **Table 3** VPC route tables (IPv4)

      +-------------+---------------+------------+------------+---------------------------------------------------------------------------------------------+
      | Route Table | Destination   | Next Hop   | Route Type | Description                                                                                 |
      +=============+===============+============+============+=============================================================================================+
      | rtb-VPC-A   | 10.0.0.0/16   | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop. |
      +-------------+---------------+------------+------------+---------------------------------------------------------------------------------------------+
      | rtb-VPC-B   | 172.16.0.0/16 | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop. |
      +-------------+---------------+------------+------------+---------------------------------------------------------------------------------------------+

-  Multiple VPCs peered together: :ref:`Figure 2 <en-us_topic_0046809840__fig2032313286441>` shows the networking diagram of VPC peering connections that connect VPC-A, VPC-B, and VPC-C.

   .. _en-us_topic_0046809840__fig2032313286441:

   .. figure:: /_static/images/en-us_image_0000001818982906.png
      :alt: **Figure 2** Networking diagram (IPv4)

      **Figure 2** Networking diagram (IPv4)

   .. table:: **Table 4** Peering relationships (IPv4)

      =========================== ======================= ========= ========
      Peering Relationship        Peering Connection Name Local VPC Peer VPC
      =========================== ======================= ========= ========
      VPC-A is peered with VPC-B. Peering-AB              VPC-A     VPC-B
      VPC-A is peered with VPC-C. Peering-AC              VPC-A     VPC-C
      VPC-B is peered with VPC-C. Peering-BC              VPC-B     VPC-C
      =========================== ======================= ========= ========

   .. table:: **Table 5** VPC route tables (IPv4)

      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
      | Route Table | Destination    | Next Hop   | Route Type | Description                                                                                 |
      +=============+================+============+============+=============================================================================================+
      | rtb-VPC-A   | 10.0.0.0/16    | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop. |
      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 192.168.0.0/16 | Peering-AC | Custom     | Add a route with the CIDR block of VPC-C as the destination and Peering-AC as the next hop. |
      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
      | rtb-VPC-B   | 172.16.0.0/16  | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop. |
      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 192.168.0.0/16 | Peering-BC | Custom     | Add a route with the CIDR block of VPC-C as the destination and Peering-BC as the next hop. |
      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
      | rtb-VPC-C   | 172.16.0.0/16  | Peering-AC | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AC as the next hop. |
      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 10.0.0.0/16    | Peering-BC | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-BC as the next hop. |
      +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0046809840__section51284316142:

Peering One Central VPC with Multiple VPCs
------------------------------------------

:ref:`Figure 3 <en-us_topic_0046809840__fig724664185>` shows the networking diagram of VPC peering connections that connect VPC-B, VPC-C, VPC-D, VPC-E, VPC-F, VPC-G, and central VPC-A.

.. _en-us_topic_0046809840__fig724664185:

.. figure:: /_static/images/en-us_image_0000001818823110.png
   :alt: **Figure 3** Networking diagram (IPv4)

   **Figure 3** Networking diagram (IPv4)

.. table:: **Table 6** Peering relationships (IPv4)

   =========================== ======================= ========= ========
   Peering Relationship        Peering Connection Name Local VPC Peer VPC
   =========================== ======================= ========= ========
   VPC-A is peered with VPC-B. Peering-AB              VPC-A     VPC-B
   VPC-A is peered with VPC-C. Peering-AC              VPC-A     VPC-C
   VPC-A is peered with VPC-D. Peering-AD              VPC-A     VPC-D
   VPC-A is peered with VPC-E. Peering-AE              VPC-A     VPC-E
   VPC-A is peered with VPC-F. Peering-AF              VPC-A     VPC-F
   VPC-A is peered with VPC-G. Peering-AG              VPC-A     VPC-G
   =========================== ======================= ========= ========

.. table:: **Table 7** VPC route table details (IPv4)

   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | Route Table | Destination    | Next Hop   | Route Type | Description                                                                                 |
   +=============+================+============+============+=============================================================================================+
   | rtb-VPC-A   | 10.0.0.0/16    | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 192.168.0.0/16 | Peering-AC | Custom     | Add a route with the CIDR block of VPC-C as the destination and Peering-AC as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.2.0.0/16    | Peering-AD | Custom     | Add a route with the CIDR block of VPC-D as the destination and Peering-AD as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.3.0.0/16    | Peering-AE | Custom     | Add a route with the CIDR block of VPC-E as the destination and Peering-AE as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 172.17.0.0/16  | Peering-AF | Custom     | Add a route with the CIDR block of VPC-F as the destination and Peering-AF as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.4.0.0/16    | Peering-AG | Custom     | Add a route with the CIDR block of VPC-G as the destination and Peering-AG as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 172.16.0.0/16  | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-C   | 172.16.0.0/16  | Peering-AC | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AC as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-D   | 172.16.0.0/16  | Peering-AD | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AD as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-E   | 172.16.0.0/16  | Peering-AE | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AE as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-F   | 172.16.0.0/16  | Peering-AF | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AF as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-G   | 172.16.0.0/16  | Peering-AG | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AG as the next hop. |
   +-------------+----------------+------------+------------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0046809840__section6703221192012:

Peering Two VPCs with Overlapping CIDR Blocks
---------------------------------------------

As shown in :ref:`Figure 4 <en-us_topic_0046809840__fig06955277200>`, VPC-A and VPC-B have overlapping CIDR blocks, and their Subnet-A01 and Subnet-B01 also have overlapping CIDR blocks. In this case, a VPC peering connection can connect their Subnet-A02 and Subnet-B02 that do not overlap with each other.

.. _en-us_topic_0046809840__fig06955277200:

.. figure:: /_static/images/en-us_image_0000001865662833.png
   :alt: **Figure 4** Networking diagram (IPv4)

   **Figure 4** Networking diagram (IPv4)

.. table:: **Table 8** Peering relationships (IPv4)

   =========================== ======================= ========= ========
   Peering Relationship        Peering Connection Name Local VPC Peer VPC
   =========================== ======================= ========= ========
   VPC-A is peered with VPC-B. Peering-AB              VPC-A     VPC-B
   =========================== ======================= ========= ========

.. table:: **Table 9** VPC route table details (IPv4)

   +-------------+-------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | Route Table | Destination | Next Hop   | Route Type | Description                                                                                      |
   +=============+=============+============+============+==================================================================================================+
   | rtb-VPC-A   | 10.0.2.0/24 | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-B02 as the destination and Peering-AB as the next hop. |
   +-------------+-------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 10.0.1.0/24 | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-A02 as the destination and Peering-AB as the next hop. |
   +-------------+-------------+------------+------------+--------------------------------------------------------------------------------------------------+

.. _en-us_topic_0046809840__section654114220445:

Peering ECSs in a Central VPC with ECSs in Two Other VPCs
---------------------------------------------------------

As shown in :ref:`Figure 5 <en-us_topic_0046809840__fig568511518481>`, VPC-B and VPC-C have overlapping CIDR blocks, and their Subnet-B01 and Subnet-C01 have overlapping CIDR blocks. You can only create a VPC peering connection between ECSs.

-  Use VPC peering connection Peering-AB to connect ECSs in Subnet-B01 and Subnet-A01.
-  Use VPC peering connection Peering-AC to connect ECSs in Subnet-C01 and Subnet-A01.

.. _en-us_topic_0046809840__fig568511518481:

.. figure:: /_static/images/en-us_image_0000001818823118.png
   :alt: **Figure 5** Networking diagram (IPv4)

   **Figure 5** Networking diagram (IPv4)

.. table:: **Table 10** Peering relationships (IPv4)

   +-----------------------------------------------------+-------------------------+-----------+----------+
   | Peering Relationship                                | Peering Connection Name | Local VPC | Peer VPC |
   +=====================================================+=========================+===========+==========+
   | ECS-A01-1 in VPC-A is peered with ECS-B01 in VPC-B. | Peering-AB              | VPC-A     | VPC-B    |
   +-----------------------------------------------------+-------------------------+-----------+----------+
   | ECS-A01-2 in VPC-A is peered with ECS-C01 in VPC-C. | Peering-AC              | VPC-A     | VPC-C    |
   +-----------------------------------------------------+-------------------------+-----------+----------+

.. table:: **Table 11** VPC route table details (IPv4)

   +-------------+-----------------+------------+------------+---------------------------------------------------------------------------------------------------------+
   | Route Table | Destination     | Next Hop   | Route Type | Description                                                                                             |
   +=============+=================+============+============+=========================================================================================================+
   | rtb-VPC-A   | 10.0.0.139/32   | Peering-AB | Custom     | Add a route with the private IP address of ECS-B01 as the destination and Peering-AB as the next hop.   |
   +-------------+-----------------+------------+------------+---------------------------------------------------------------------------------------------------------+
   |             | 10.0.0.71/32    | Peering-AC | Custom     | Add a route with the private IP address of ECS-C01 as the destination and Peering-AC as the next hop.   |
   +-------------+-----------------+------------+------------+---------------------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 172.16.0.111/32 | Peering-AB | Custom     | Add a route with the private IP address of ECS-A01-1 as the destination and Peering-AB as the next hop. |
   +-------------+-----------------+------------+------------+---------------------------------------------------------------------------------------------------------+
   | rtb-VPC-C   | 172.16.0.218/32 | Peering-AC | Custom     | Add a route with the private IP address of ECS-A01-2 as the destination and Peering-AC as the next hop. |
   +-------------+-----------------+------------+------------+---------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0046809840__section0306616175518:

Invalid VPC Peering Connections
-------------------------------

If VPCs with the same CIDR block also include subnets that overlap, VPC peering connections are not usable. VPC-A and VPC-B have the same CIDR block and their subnets have the same CIDR block. If a VPC peering connection is created between VPC-A and VPC-B, traffic cannot be routed between them because there are routes with the same destination.

In the rtb-VPC-A route table, the custom route for routing traffic from VPC-A to VPC-B and the local route have overlapping destinations. The local route has a higher priority and traffic will be forwarded within VPC-A and cannot reach VPC-B.


.. figure:: /_static/images/en-us_image_0000001818982898.png
   :alt: **Figure 6** Networking diagram (IPv4)

   **Figure 6** Networking diagram (IPv4)

.. table:: **Table 12** VPC route table details

   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
   | Route Table | Destination         | Next Hop   | Route Type | Description                                                                                 |
   +=============+=====================+============+============+=============================================================================================+
   | rtb-VPC-A   | 10.0.0.0/24         | Local      | System     | Local routes are added by the system for internal communication in a VPC.                   |
   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24         | Local      | System     |                                                                                             |
   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/16 (VPC-B) | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop. |
   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 10.0.0.0/24         | Local      | System     | Local routes are added by the system for internal communication in a VPC.                   |
   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24         | Local      | System     |                                                                                             |
   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/16 (VPC-A) | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop. |
   +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
