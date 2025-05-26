:original_name: vpc_faq_0006.html

.. _vpc_faq_0006:

What Subnet CIDR Blocks Are Available?
======================================

A subnet is an IP address range from a VPC. The VPC service supports CIDR blocks 10.0.0.0/8-24, 172.16.0.0/12-24, and 192.168.0.0/16-24.

Subnets must reside within your VPC, and the subnet masks used to define them can be between the netmask of its VPC CIDR block and /29 netmask.
