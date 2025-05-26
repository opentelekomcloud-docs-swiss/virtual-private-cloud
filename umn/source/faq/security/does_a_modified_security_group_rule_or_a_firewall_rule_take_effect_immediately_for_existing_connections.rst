:original_name: vpc_faq_0074.html

.. _vpc_faq_0074:

Does a Modified Security Group Rule or a Firewall Rule Take Effect Immediately for Existing Connections?
========================================================================================================

-  Security groups use connection tracking to track traffic to and from instances. If an inbound rule is modified, the modified rule immediately takes effect for the existing traffic. Changes to outbound security group rules do not affect existing persistent connections and take effect only for new connections.

   If you add, modify, or delete a security group rule, or add or remove an instance to or from a security group, the inbound connections of all instances in the security group will be automatically cleared.

   -  The existing inbound persistent connections will be disconnected. All the new connections will match the new rules.
   -  The existing outbound persistent connections will not be disconnected, and the original rule will still be applied. All the new connections will match the new rules.

-  Firewalls use connection tracking to track traffic to and from instances. Changes to inbound and outbound rules do not take effect immediately for the existing traffic.

   If you add, modify, or delete a firewall rule, or associate or disassociate a subnet with or from a firewall, all the inbound and outbound persistent connections will not be disconnected. New rules will only be applied for the new connections.

.. important::

   After a persistent connection is disconnected, new connections will not be established immediately until the timeout period of connection tracking expires. For example, after an ICMP persistent connection is disconnected, a new connection will be established and a new rule will apply when the timeout period (30s) expires.

   -  The timeout period of connection tracking varies by protocol. The timeout period of a TCP connection in the established state is 600s, and that of an ICMP connection is 30s. For other protocols, if packets are received in both inbound and outbound directions, the connection tracking timeout period is 180s. If packets are received only in one direction, the connection tracking timeout period is 30s.
   -  The timeout period of TCP connections varies by connection status. The timeout period of a TCP connection in the established state is 600s, and that of a TCP connection in the FIN-WAIT state is 30s.
