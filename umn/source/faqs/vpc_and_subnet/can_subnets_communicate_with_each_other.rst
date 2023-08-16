:original_name: vpc_faq_0005.html

.. _vpc_faq_0005:

Can Subnets Communicate with Each Other?
========================================

Subnets in the same VPC can communicate with each other, but subnets in different VPCs cannot communicate with each other by default. However, you can create VPC peering connections to enable subnets in different VPCs to communicate with each other.

.. note::

   If subnets have firewalls associated, firewall rules should allow communication between the subnets.
