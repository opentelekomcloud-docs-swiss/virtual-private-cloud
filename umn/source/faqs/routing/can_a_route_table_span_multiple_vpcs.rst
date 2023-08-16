:original_name: vpc_faq_0062.html

.. _vpc_faq_0062:

Can a Route Table Span Multiple VPCs?
=====================================

A route table cannot span multiple VPCs.

A route table contains a set of routes that are used to determine where network traffic from your subnets in a VPC is directed. A VPC has a default route table and can have multiple custom route tables.

Each subnet in a VPC must be associated with a route table. A subnet can only be associated with one route table at a time, but you can associate multiple subnets in a VPC with the same route table.
