:original_name: vpc_faq_0004.html

.. _vpc_faq_0004:

Which CIDR Blocks Are Available for the VPC Service?
====================================================

The following table lists the private CIDR blocks that you can specify when creating a VPC. Consider the following when selecting a VPC CIDR block:

-  Number of IP addresses: Reserve sufficient IP addresses in case of business growth.
-  IP address range: Avoid IP address conflicts if you need to connect a VPC to an on-premises data center or connect two VPCs.

:ref:`Table 1 <vpc_faq_0004__table3240172772213>` lists the supported VPC CIDR blocks.

.. _vpc_faq_0004__table3240172772213:

.. table:: **Table 1** VPC CIDR blocks

   +-------------------+-----------------------------+--------------------------------+
   | VPC CIDR Block    | IP Address Range            | Maximum Number of IP Addresses |
   +===================+=============================+================================+
   | 10.0.0.0/8-24     | 10.0.0.0-10.255.255.255     | 2^24-2=16777214                |
   +-------------------+-----------------------------+--------------------------------+
   | 172.16.0.0/12-24  | 172.16.0.0-172.31.255.255   | 2^20-2=1048574                 |
   +-------------------+-----------------------------+--------------------------------+
   | 192.168.0.0/16-24 | 192.168.0.0-192.168.255.255 | 2^16-2=65534                   |
   +-------------------+-----------------------------+--------------------------------+
