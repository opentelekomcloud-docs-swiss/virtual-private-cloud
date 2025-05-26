:original_name: vpc_Concepts_0005.html

.. _vpc_Concepts_0005:

Security Group
==============

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted. After a security group is created, you can configure access rules that will apply to all cloud resources added to this security group.

Like whitelists, security group rules work as follows:

-  Inbound rules control incoming traffic to instances in the security group.

   If an inbound request matches the source in an inbound security group rule with **Action** set to **Allow**, the request is allowed and other requests are denied.

   By default, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rules control outgoing traffic from instances in the security group.

   If the destination of an outbound security group rule with **Action** set to **Allow** is 0.0.0.0/0, all outbound requests are allowed.

   0.0.0.0/0 represents all IPv4 addresses.
