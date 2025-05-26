:original_name: vpc_Concepts_0011.html

.. _vpc_Concepts_0011:

VPC Peering Connection
======================

A VPC peering connection is a networking connection that connects two VPCs for them to communicate using private IP addresses. The VPCs to be peered can be in the same account or different accounts, but must be in the same region.

-  You can use VPC peering connections to build networks in different scenarios. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`.

:ref:`Figure 1 <vpc_concepts_0011__en-us_topic_0046655036_fig4721642193711>` shows an application scenario of VPC peering connections.

-  There are two VPCs (VPC-A and VPC-B) in region A that are not connected.
-  Service servers (ECS-A01 and ECS-A02) are in VPC-A, and database servers (RDS-B01 and RDS-B02) are in VPC-B. The service servers and database servers cannot communicate with each other.

-  You need to create a VPC peering connection (peering-AB) between VPC-A and VPC-B so the service servers and database servers can communicate with each other.

.. _vpc_concepts_0011__en-us_topic_0046655036_fig4721642193711:

.. figure:: /_static/images/en-us_image_0000001818983018.png
   :alt: **Figure 1** VPC peering connection network diagram

   **Figure 1** VPC peering connection network diagram

For details about VPC peering connections, see :ref:`VPC Peering Connection <vpc_peering_0000>`.
