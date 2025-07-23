:original_name: en-us_topic_0046655036.html

.. _en-us_topic_0046655036:

VPC Peering Connection Overview
===============================

What Is a VPC Peering Connection?
---------------------------------

A VPC peering connection is a networking connection that connects two VPCs for them to communicate using private IP addresses. The VPCs to be peered can be in the same account or different accounts, but must be in the same region.

-  You can use VPC peering connections to build networks in different scenarios. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`.

:ref:`Figure 1 <en-us_topic_0046655036__fig4721642193711>` shows an application scenario of VPC peering connections.

-  There are two VPCs (VPC-A and VPC-B) in region A that are not connected.
-  Service servers (ECS-A01 and ECS-A02) are in VPC-A, and database servers (RDS-B01 and RDS-B02) are in VPC-B. The service servers and database servers cannot communicate with each other.

-  You need to create a VPC peering connection (peering-AB) between VPC-A and VPC-B so the service servers and database servers can communicate with each other.

.. _en-us_topic_0046655036__fig4721642193711:

.. figure:: /_static/images/en-us_image_0000001818983018.png
   :alt: **Figure 1** VPC peering connection network diagram

   **Figure 1** VPC peering connection network diagram

VPC Peering Connection Creation Process
---------------------------------------

A VPC peering connection can only connect VPCs in the same region.

-  If two VPCs are in the same account, the process of creating a VPC peering connection is shown in :ref:`Figure 2 <en-us_topic_0046655036__en-us_topic_0000001154868962_fig10285152624918>`.

   For details about how to create a VPC peering connection, see :ref:`Creating a VPC Peering Connection to Connect Two VPCs in the Same Account <en-us_topic_0046655037>`.

   .. _en-us_topic_0046655036__en-us_topic_0000001154868962_fig10285152624918:

   .. figure:: /_static/images/en-us_image_0000001818823678.png
      :alt: **Figure 2** Process of creating a VPC peering connection between VPCs in the same account

      **Figure 2** Process of creating a VPC peering connection between VPCs in the same account

-  If two VPCs are in different accounts, the process of creating a VPC peering connection is shown in :ref:`Figure 3 <en-us_topic_0046655036__fig16137161191713>`.

   For details about how to create a VPC peering connection, see :ref:`Creating a VPC Peering Connection to Connect Two VPCs in Different Accounts <en-us_topic_0046655038>`.

   If account A initiates a request to create a VPC peering connection with a VPC in account B, the VPC peering connection takes effect only after account B accepts the request.

   .. _en-us_topic_0046655036__fig16137161191713:

   .. figure:: /_static/images/en-us_image_0000001865583217.png
      :alt: **Figure 3** Process of creating a VPC peering connection between VPCs in different accounts

      **Figure 3** Process of creating a VPC peering connection between VPCs in different accounts

Notes and Constraints
---------------------

-  A VPC peering connection can only connect VPCs in the same region.
-  If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect.
-  A VPC cannot use EIPs of its peered VPC for Internet access. For example, if VPC A is peered with VPC B that has EIPs, VPC A cannot use EIPs in VPC B to access the Internet.
