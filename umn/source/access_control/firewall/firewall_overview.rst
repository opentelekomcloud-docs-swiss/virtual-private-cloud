:original_name: acl_0001.html

.. _acl_0001:

Firewall Overview
=================

A firewall is an optional layer of security for your subnets. After you associate one or more subnets with a firewall, you can control traffic in and out of the subnets.

For details, see :ref:`Figure 1 <acl_0001__fig9582182315479>`.

.. _acl_0001__fig9582182315479:

.. figure:: /_static/images/en-us_image_0000001818982946.png
   :alt: **Figure 1** Security groups and firewalls

   **Figure 1** Security groups and firewalls

Similar to security groups, firewalls control access to subnets and add an additional layer of defense to your subnets. Security groups only have the "allow" rules, but firewalls have both "allow" and "deny" rules. You can use firewalls together with security groups to implement comprehensive and fine-grained access control.

:ref:`Differences Between Security Groups and Firewalls <en-us_topic_0052003963>` summarizes the basic differences between security groups and firewalls.

Firewall Basics
---------------

-  Your VPC does not come with a firewall, but you can create a firewall and associate it with a VPC subnet if required. By default, each firewall denies all inbound traffic to and outbound traffic from the associated subnet until you add rules.

-  You can associate a firewall with multiple subnets. However, a subnet can only be associated with one firewall at a time.

-  Each newly created firewall is in the **Inactive** state until you associate subnets with it.

-  Firewalls use connection tracking to track traffic to and from instances. Changes to inbound and outbound rules do not take effect immediately for the existing traffic.

   If you add, modify, or delete a firewall rule, or associate or disassociate a subnet with or from a firewall, all the inbound and outbound persistent connections will not be disconnected. New rules will only be applied for the new connections.

.. important::

   After a persistent connection is disconnected, new connections will not be established immediately until the timeout period of connection tracking expires. For example, after an ICMP persistent connection is disconnected, a new connection will be established and a new rule will be applied when the timeout period (30s) expires.

   -  The timeout period of connection tracking varies by protocol. The timeout period of a TCP connection in the established state is 600s, and that of an ICMP connection is 30s. For other protocols, if packets are received in both inbound and outbound directions, the connection tracking timeout period is 180s. If packets are received only in one direction, the connection tracking timeout period is 30s.
   -  The timeout period of TCP connections varies by connection status. The timeout period of a TCP connection in the established state is 600s, and that of a TCP connection in the FIN-WAIT state is 30s.

.. _acl_0001__section99541345213:

Default Firewall Rules
----------------------

By default, each firewall has preset rules that allow the following packets:

-  Packets whose source and destination are in the same subnet.

-  Broadcast packets with the destination 255.255.255.255/32, which is used to configure host startup information.

-  Multicast packets with the destination 224.0.0.0/24, which is used by routing protocols.

-  Metadata packets with the destination 169.254.169.254/32 and TCP port number 80, which is used to obtain metadata.

-  Packets from CIDR blocks that are reserved for public services (for example, packets with the destination 100.125.0.0/16).

-  A firewall denies all traffic in and out of a subnet excepting the preceding packets. :ref:`Table 1 <acl_0001__table1034601475112>` shows the default rules. You cannot modify or delete the default rules.

   .. _acl_0001__table1034601475112:

   .. table:: **Table 1** Default firewall rules

      +-----------+----------+--------+----------+-----------+-------------+------------------------------+
      | Direction | Priority | Action | Protocol | Source    | Destination | Description                  |
      +===========+==========+========+==========+===========+=============+==============================+
      | Inbound   | \*       | Deny   | All      | 0.0.0.0/0 | 0.0.0.0/0   | Denies all inbound traffic.  |
      +-----------+----------+--------+----------+-----------+-------------+------------------------------+
      | Outbound  | \*       | Deny   | All      | 0.0.0.0/0 | 0.0.0.0/0   | Denies all outbound traffic. |
      +-----------+----------+--------+----------+-----------+-------------+------------------------------+

How Traffic Matches Firewall Rules
----------------------------------

-  Each firewall rule has a priority value where a smaller value corresponds to a higher priority. Any time two rules conflict, the rule with the higher priority is the one that gets applied. The rule whose priority value is an asterisk (*) has the lowest priority.
-  If multiple firewall rules conflict, only the rule with the highest priority takes effect. If you need a rule to take effect before or after a specific rule, you can insert that rule before or after the specific rule.

Application Scenarios
---------------------

-  If the application layer needs to provide services for users, traffic must be allowed to reach the application layer from all IP addresses. However, you also need to prevent illegal access from malicious users.

   Solution: You can add firewall rules to deny access from suspect IP addresses.

-  How can I isolate ports with identified vulnerabilities? For example, how do I isolate port 445 that can be exploited by WannaCry worm?

   Solution: You can add firewall rules to deny access traffic from a specific port and protocol, for example, TCP port 445.

-  No defense is required for the east-west traffic between subnets, but access control is required for north-south traffic.

   Solution: You can add firewall rules to protect north-south traffic.

-  For frequently accessed applications, a security rule sequence may need to be adjusted to improve performance.

   Solution: A firewall allows you to adjust the rule sequence so that frequently used rules are applied before other rules.

Configuration Procedure
-----------------------

:ref:`Figure 2 <acl_0001__fig1643183218163>` shows the procedure for configuring a firewall.

.. _acl_0001__fig1643183218163:

.. figure:: /_static/images/en-us_image_0000001818982962.png
   :alt: **Figure 2** firewall configuration procedure

   **Figure 2** firewall configuration procedure

#. Create a firewall by following the steps described in :ref:`Creating a Firewall <en-us_topic_0051746698>`.
#. Add firewall rules by following the steps described in :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`.
#. Associate subnets with the firewall by following the steps described in :ref:`Associating Subnets with a Firewall <en-us_topic_0051746700>`. After subnets are associated with the firewall, the subnets will be protected by the configured firewall rules.

Notes and Constraints
---------------------

-  By default, each account can have up to 200 firewalls in a region.
-  A firewall can contain no more than 20 rules in one direction, or performance will deteriorate.
