:original_name: vpc_faq_0006.html

.. _vpc_faq_0006:

What Subnet CIDR Blocks Are Available?
======================================

A subnet CIDR block must be included in its VPC CIDR block. Supported VPC CIDR blocks are **10.0.0.0/8-24**, **172.16.0.0/12-24**, and **192.168.0.0/16-24**. The allowed block size of a subnet is between the netmask of its VPC CIDR block and the /29 netmask.
