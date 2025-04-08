:original_name: vpc_faq_0005.html

.. _vpc_faq_0005:

Can Subnets Communicate with Each Other?
========================================

-  Subnets in the same VPC can communicate with each other by default.
-  VPCs are isolated from each other. Subnets from different VPCs cannot communicate with each other. You can use a VPC peering connection to enable communication between VPCs in the same region.

.. note::

   If subnets have firewalls associated, firewall rules should allow communication between the subnets.
