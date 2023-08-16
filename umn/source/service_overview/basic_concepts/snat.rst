:original_name: vpc_Concepts_0004.html

.. _vpc_Concepts_0004:

SNAT
====

In addition to services provided by the system, some ECSs need to access the Internet to obtain information or download software. You can bind EIPs to virtual NICs (ports) of ECSs to enable the ECSs to access the Internet. However, assigning an EIP to each ECS consumes IPv4 addresses, incurs additional costs, and may increase the attack surface for a virtual environment. Therefore, SNAT is introduced to enable multiple ECSs to share one EIP.

On a cloud platform, an EIP can be assigned to an ECS that serves as the SNAT router or gateway for other ECSs from the same subnet or VPC.
