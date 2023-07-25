:original_name: en-us_topic_0030969424.html

.. _en-us_topic_0030969424:

Subnet
======

A subnet is a unique CIDR block with a range of IP addresses in a VPC. All resources in a VPC must be deployed on subnets.

-  By default, ECSs in all subnets of the same VPC can communicate with one another, but ECSs in different VPCs cannot.

   You can create VPC peering connections to enable ECSs in different VPCs but in the same region to communicate with one another. For details, see :ref:`VPC Peering Connection Overview <en-us_topic_0046655036>`.

-  After a subnet is created, its CIDR block cannot be modified.

   The subnets used to deploy your resources must reside within your VPC, and the subnet masks used to define them can be between the netmask of its VPC CIDR block and /29 netmask.

   -  10.0.0.0 - 10.255.255.255
   -  172.16.0.0 - 172.31.255.255
   -  192.168.0.0 - 192.168.255.255
