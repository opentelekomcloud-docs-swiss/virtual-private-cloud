:original_name: vpc_peering02_0001.html

.. _vpc_peering02_0001:

VPC Peering Connection Overview
===============================

What Is a VPC Peering Connection?
---------------------------------

A VPC peering connection is a networking connection between two VPCs and enables them to communicate using private IP addresses. The VPCs to be peered can be in the same account or different accounts, but must be in the same region.

-  You can use VPC peering connections to build networks in different scenarios. For details, see :ref:`VPC Peering Connection Usage Examples <vpc_peering02_0002>`.

:ref:`Figure 1 <vpc_peering02_0001__en-us_topic_0118498905_fig4721642193711>` shows an application scenario of VPC peering connections.

-  There are two VPCs (VPC-A and VPC-B) in region A that are not connected.
-  Service servers (ECS-A01 and ECS-A02) are in VPC-A, and database servers (RDS-B01 and RDS-B02) are in VPC-B. The service servers and database servers cannot communicate with each other.

-  You need to create a VPC peering connection (peering-AB) between VPC-A and VPC-B so the service servers and database servers can communicate with each other.

.. _vpc_peering02_0001__en-us_topic_0118498905_fig4721642193711:

.. figure:: /_static/images/en-us_image_0000001512591549.png
   :alt: **Figure 1** VPC peering connection network diagram

   **Figure 1** VPC peering connection network diagram

VPC Peering Connection Creation Process
---------------------------------------

A VPC peering connection can only connect VPCs in the same region.

-  If two VPCs are in the same account, the process of creating a VPC peering connection is shown in :ref:`Figure 2 <vpc_peering02_0001__en-us_topic_0118498905_en-us_topic_0000001154868962_fig10285152624918>`.

   For details about how to create a VPC peering connection, see :ref:`Creating a VPC Peering Connection with Another VPC in Your Account <en-us_topic_0046655037>`.

   .. _vpc_peering02_0001__en-us_topic_0118498905_en-us_topic_0000001154868962_fig10285152624918:

   .. figure:: /_static/images/en-us_image_0000001512701025.png
      :alt: **Figure 2** Process of creating a VPC peering connection between VPCs in the same account

      **Figure 2** Process of creating a VPC peering connection between VPCs in the same account

-  If two VPCs are in different accounts, the process of creating a VPC peering connection is shown in :ref:`Figure 3 <vpc_peering02_0001__en-us_topic_0118498905_fig16137161191713>`.

   For details about how to create a VPC peering connection, see :ref:`Creating a VPC Peering Connection with a VPC in Another Account <en-us_topic_0046655038>`.

   If account A initiates a request to create a VPC peering connection with a VPC in account B, the VPC peering connection takes effect only after account B accepts the request.

   .. _vpc_peering02_0001__en-us_topic_0118498905_fig16137161191713:

   .. figure:: /_static/images/en-us_image_0000001462622484.png
      :alt: **Figure 3** Process of creating a VPC peering connection between VPCs in different accounts

      **Figure 3** Process of creating a VPC peering connection between VPCs in different accounts

Notes and Constraints
---------------------

-  A VPC peering connection can only connect VPCs in the same region.
-  If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect.
-  A VPC cannot use EIPs of its peered VPC for Internet access. For example, if VPC A is peered with VPC B that has EIPs, VPC A cannot use EIPs in VPC B to access the Internet.
