:original_name: vpc_Concepts_0005.html

.. _vpc_Concepts_0005:

Security Group
==============

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted. After a security group is created, you can configure access rules that will apply to all cloud resources added to this security group.

Like whitelists, security group rules work as follows:

-  Inbound rules control incoming traffic to instances in the security group.

   If an inbound request matches the source in an inbound security group rule, the request is allowed and other requests are denied.

   By default, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rules control outgoing traffic from instances in the security group.

   If the destination of an outbound security group rule is 0.0.0.0/0, all outbound requests are allowed.

   0.0.0.0/0 represents all IPv4 addresses.

   ::/0 represents all IPv6 addresses.

:ref:`Table 1 <vpc_concepts_0005__en-us_topic_0118534002_table102261597217>` uses custom security group sg-AB as an example to describe its inbound and outbound rules in detail.

.. _vpc_concepts_0005__en-us_topic_0118534002_table102261597217:

.. table:: **Table 1** Rules in security group sg-AB

   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Type | Protocol & Port | Source/Destination     | Description                                                                                                                  |
   +===========+======+=================+========================+==============================================================================================================================+
   | Inbound   | IPv4 | All             | Source: sg-AB          | Allows ECSs in the security group to communicate with each other.                                                            |
   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 22         | Source: 0.0.0.0/0      | Allows all IPv4 addresses to access ECSs in the security group over port 22 (SSH) for remotely logging in to Linux ECSs.     |
   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 3389       | Source: 0.0.0.0/0      | Allows all IPv4 addresses to access ECSs in the security group over port 3389 (RDP) for remotely logging in to Windows ECSs. |
   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 80         | Source: 10.5.6.30/32   | Allows IP address 10.5.6.30 to access ECSs in the security group over port 80.                                               |
   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | IPv4 | All             | Destination: 0.0.0.0/0 | Allows access from ECSs in the security group to any IPv4 address over any port.                                             |
   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | IPv6 | All             | Destination: ::/0      | Allows access from ECSs in the security group to any IPv6 address over any port.                                             |
   +-----------+------+-----------------+------------------------+------------------------------------------------------------------------------------------------------------------------------+
