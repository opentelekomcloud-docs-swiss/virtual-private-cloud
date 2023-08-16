:original_name: vpc_Concepts_0005.html

.. _vpc_Concepts_0005:

Security Group
==============

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted. After a security group is created, you can create various access rules for the security group, these rules will apply to all cloud resources added to this security group.

Like whitelists, security group rules work as follows:

-  Inbound rules control incoming traffic to instances in the security group. If an inbound request matches the source in an inbound security group rule with **Action** set to **Allow**, the request is allowed.

   Unless otherwise specified, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rules control outgoing traffic from instances in the security group. If the destination of an outbound security group rule with **Action** set to **Allow** is 0.0.0.0/0, all outbound requests are allowed.

   0.0.0.0/0 represents all IPv4 addresses.

:ref:`Table 1 <vpc_concepts_0005__en-us_topic_0118498944_en-us_topic_0118534002_table102261597217>` shows the inbound and outbound rules in security group sg-AB.

.. _vpc_concepts_0005__en-us_topic_0118498944_en-us_topic_0118534002_table102261597217:

.. table:: **Table 1** Rules in security group sg-AB

   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Action | Protocol & Port | Source/Destination        | Description                                                                                                                          |
   +===========+========+=================+===========================+======================================================================================================================================+
   | Inbound   | Allow  | All             | Source: sg-AB             | This rule allows ECSs in the security group to communicate with each other.                                                          |
   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | TCP: 22         | Source: 0.0.0.0/0         | This rule allows all IPv4 addresses to access ECSs in the security group over SSH port 22 for remotely logging in to Linux ECSs.     |
   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | TCP: 3389       | Source: 0.0.0.0/0         | This rule allows all IPv4 addresses to access ECSs in the security group over RDP port 3389 for remotely logging in to Windows ECSs. |
   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | TCP: 80         | Source: 10.5.6.30/32      | This rule allows IP address 10.5.6.30 to access ECSs in the security group over port 80.                                             |
   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | All             | Destination: 0.0.0.0/0    | This rule allows access from ECSs in the security group to any IPv4 address over any port.                                           |
   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | TCP: 80         | Destination: 10.7.6.51/32 | This rule allows access from ECSs in the security group to IP address 10.7.6.51 over port 80.                                        |
   +-----------+--------+-----------------+---------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
