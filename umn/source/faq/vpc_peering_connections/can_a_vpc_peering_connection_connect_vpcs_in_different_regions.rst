:original_name: faq_connection_0001.html

.. _faq_connection_0001:

Can a VPC Peering Connection Connect VPCs in Different Regions?
===============================================================

A VPC peering connection only can connect VPCs in the same region.

:ref:`Figure 1 <faq_connection_0001__en-us_topic_0118498905_fig4721642193711>` shows an application scenario of VPC peering connections.

-  There are two VPCs (VPC-A and VPC-B) in region A that are not connected.
-  Service servers (ECS-A01 and ECS-A02) are in VPC-A, and database servers (RDS-B01 and RDS-B02) are in VPC-B. The service servers and database servers cannot communicate with each other.

-  You need to create a VPC peering connection (peering-AB) between VPC-A and VPC-B so the service servers and database servers can communicate with each other.

.. _faq_connection_0001__en-us_topic_0118498905_fig4721642193711:

.. figure:: /_static/images/en-us_image_0000001818983018.png
   :alt: **Figure 1** VPC peering connection network diagram

   **Figure 1** VPC peering connection network diagram
