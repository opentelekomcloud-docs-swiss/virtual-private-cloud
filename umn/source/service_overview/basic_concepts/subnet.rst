:original_name: en-us_topic_0030969424.html

.. _en-us_topic_0030969424:

Subnet
======

A subnet is a unique CIDR block with a range of IP addresses in a VPC. All resources in a VPC must be deployed on subnets.

-  By default, all instances in different subnets of the same VPC can communicate with each other. If you have a VPC with two subnets in it, they can communicate with each other by default.

-  After a subnet is created, its CIDR block cannot be modified. Subnets in the same VPC cannot overlap.

   A subnet mask can be between the netmask of its VPC CIDR block and /29 netmask. If a VPC CIDR block is 10.0.0.0/16, its subnet mask can be between 16 and 29.

   For example, if the CIDR block of VPC-A is 10.0.0.0/16, you can specify 10.0.0.0/24 for subnet A01, 10.0.1.0/24 for subnet A02, and 10.0.3.0/24 for subnet A03.

   .. note::

      By default, you can create a maximum of 100 subnets in each region. If this cannot meet your service requirements, request a quota increase by referring to :ref:`What Is a Quota? <vpc_faq_0051>`
