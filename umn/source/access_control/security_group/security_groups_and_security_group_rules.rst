:original_name: en-us_topic_0073379079.html

.. _en-us_topic_0073379079:

Security Groups and Security Group Rules
========================================

Security Groups
---------------

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted. After a security group is created, you can configure access rules that will apply to all cloud resources added to this security group.

If you have not created any security groups yet, the system automatically creates a default security group for you and associates it with the instance (such as an ECS) when you create it. For details about the default security group, see :ref:`Default Security Group and Its Rules <securitygroup_0003>`.

Security Group Basics
---------------------

-  Security groups are stateful. If you send a request from your instance and the outbound traffic is allowed, the response traffic for that request is allowed to flow in regardless of inbound security group rules. Similarly, if inbound traffic is allowed, responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules.

-  Security groups use connection tracking to track traffic to and from instances. If an inbound rule is modified, the modified rule immediately takes effect for the existing traffic. Changes to outbound security group rules do not affect existing persistent connections and take effect only for new connections.

   If you add, modify, or delete a security group rule, or add or remove an instance to or from a security group, the inbound connections of all instances in the security group will be automatically cleared.

   -  The existing inbound persistent connections will be disconnected. All the new connections will match the new rules.
   -  The existing outbound persistent connections will not be disconnected, and the original rule will still be applied. All the new connections will match the new rules.

.. important::

   After a persistent connection is disconnected, new connections will not be established immediately until the timeout period of connection tracking expires. For example, after an ICMP persistent connection is disconnected, a new connection will be established and a new rule will be applied when the timeout period (30s) expires.

   -  The timeout period of connection tracking varies by protocol. The timeout period of a TCP connection in the established state is 600s, and that of an ICMP connection is 30s. For other protocols, if packets are received in both inbound and outbound directions, the connection tracking timeout period is 180s. If packets are received only in one direction, the connection tracking timeout period is 30s.
   -  The timeout period of TCP connections varies by connection status. The timeout period of a TCP connection in the established state is 600s, and that of a TCP connection in the FIN-WAIT state is 30s.

Security Group Rules
--------------------

A security group has inbound and outbound rules to control traffic that is allowed to reach or leave the instances associated with the security group. You can specify protocol, port, source/destination for a security group rule. :ref:`Table 1 <en-us_topic_0073379079__table1919155115499>` describes key information about a security group rule.

.. _en-us_topic_0073379079__table1919155115499:

.. table:: **Table 1** Security group rule information

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                            |
   +===================================+========================================================================================================================================================================================================================+
   | Protocol & Port                   | Network protocol type and port range.                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                        |
   |                                   | -  Network protocol: the protocol that is used to match traffic. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, or more.                                                                             |
   |                                   | -  Port range: the destination port that is used to match traffic. The value ranges from 1 to 65535.                                                                                                                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Source (Inbound)                  | The source in an inbound rule is used to match the IP address or address range of an external request. The source can be:                                                                                              |
   |                                   |                                                                                                                                                                                                                        |
   |                                   | -  IP address:                                                                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                        |
   |                                   |    -  Example IPv4 address: 192.168.10.10/32                                                                                                                                                                           |
   |                                   |    -  Example IPv6 address: 2002:50::44/128                                                                                                                                                                            |
   |                                   |    -  Example IPv4 address range: 192.168.52.0/24 All IPv4 addresses: 0.0.0.0/0                                                                                                                                        |
   |                                   |    -  Example IPv6 address range: 2407:c080:802:469::/64 All IPv6 addresses: ::/0                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                        |
   |                                   | -  Security group: You can select another security group in the same region under the current account as the source.                                                                                                   |
   |                                   |                                                                                                                                                                                                                        |
   |                                   |    For example, instance A is in security group A and instance B is in security group B. If security group A has a rule with **Source** set to security group B, access from instance B is allowed to instance A.      |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Destination (Outbound)            | The destination in an outbound rule is used to match the IP address or address range of an internal request. The destination can be:                                                                                   |
   |                                   |                                                                                                                                                                                                                        |
   |                                   | -  IP address:                                                                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                        |
   |                                   |    -  Example IPv4 address: 192.168.10.10/32                                                                                                                                                                           |
   |                                   |    -  Example IPv6 address: 2002:50::44/128                                                                                                                                                                            |
   |                                   |    -  Example IPv4 address range: 192.168.52.0/24 All IPv4 addresses: 0.0.0.0/0                                                                                                                                        |
   |                                   |    -  Example IPv6 address range: 2407:c080:802:469::/64 All IPv6 addresses: ::/0                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                        |
   |                                   | -  Security group: You can select another security group in the same region under the current account as the destination.                                                                                              |
   |                                   |                                                                                                                                                                                                                        |
   |                                   |    For example, instance A is in security group A and instance B is in security group B. If security group A has a rule with **Destination** set to security group B, access from instance A is allowed to instance B. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Like whitelists, security group rules work as follows:

-  Inbound rules control incoming traffic to instances in the security group.

   If an inbound request matches the source in an inbound security group rule, the request is allowed and other requests are denied.

   By default, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rules control outgoing traffic from instances in the security group.

   If the destination of an outbound security group rule is 0.0.0.0/0, all outbound requests are allowed.

   0.0.0.0/0 represents all IPv4 addresses.

   ::/0 represents all IPv6 addresses.

:ref:`Table 2 <en-us_topic_0073379079__table102261597217>` uses custom security group sg-AB as an example to describe its inbound and outbound rules in detail.

.. _en-us_topic_0073379079__table102261597217:

.. table:: **Table 2** Rules in security group sg-AB

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

.. important::

   -  After a port is enabled in a security group rule, ensure that the port in the instance is also enabled to ensure normal network communication.
   -  Generally, instances in the same security group can communicate with each other by default. If instances in the same security group cannot communicate with each other, the possible causes are as follows:

      -  The inbound rule for communication between instances in the same security group is deleted.

      -  Different VPCs cannot communicate with each other. The instances belong to the same security group but different VPCs.

         You can use :ref:`VPC peering connections <en-us_topic_0046655036>` to connect VPCs in different regions.

Security Group Configuration Process
------------------------------------


.. figure:: /_static/images/en-us_image_0000001865662813.png
   :alt: **Figure 1** Security group configuration process

   **Figure 1** Security group configuration process

.. table:: **Table 3** Security group configuration process description

   +-----------------+--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+
   | No.             | Step                                 | Description                                                                                                                                                                                                                                                          | Reference                                                                                       |
   +=================+======================================+======================================================================================================================================================================================================================================================================+=================================================================================================+
   | 1               | Create a security group.             | When creating a security group, you can select a template, such **General-purpose web server** or **All ports open**. A template contains preset security group rules. For details, see :ref:`Security group templates <en-us_topic_0013748715__table117828131111>`. | :ref:`Creating a Security Group <en-us_topic_0013748715>`                                       |
   +-----------------+--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+
   | 2               | Configure security group rules.      | After a security group is created, if its rules cannot meet your service requirements, you can add new rules to the security group or modify original rules.                                                                                                         | :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`                                    |
   |                 |                                      |                                                                                                                                                                                                                                                                      |                                                                                                 |
   |                 |                                      |                                                                                                                                                                                                                                                                      | :ref:`Fast-Adding Security Group Rules <securitygroup_0004>`                                    |
   +-----------------+--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+
   | 3               | Add instances to the security group. | When you create an instance, the system automatically adds the instance to a security group for protection.                                                                                                                                                          | :ref:`Adding an Instance to or Removing an Instance from a Security Group <securitygroup_0017>` |
   |                 |                                      |                                                                                                                                                                                                                                                                      |                                                                                                 |
   |                 |                                      | If one security group cannot meet your requirements, you can add an instance to multiple security groups.                                                                                                                                                            |                                                                                                 |
   +-----------------+--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+

Security Group Constraints
--------------------------

-  By default, you can create a maximum of 100 security groups in your cloud account.
-  By default, you can add up to 50 security group rules to a security group.
