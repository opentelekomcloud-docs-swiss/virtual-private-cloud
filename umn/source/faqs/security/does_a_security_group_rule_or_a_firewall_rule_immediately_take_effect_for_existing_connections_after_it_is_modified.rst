:original_name: vpc_faq_0074.html

.. _vpc_faq_0074:

Does a Security Group Rule or a Firewall Rule Immediately Take Effect for Existing Connections After It Is Modified?
====================================================================================================================

-  Security groups are stateful. Responses to outbound traffic are allowed to go in to the instance regardless of inbound security group rules, and vice versa. Security groups use connection tracking to track traffic to and from instances. If a security group rule is added, deleted, or modified, or an instance in the security group is created or deleted, the connection tracking for all instances in the security group will be automatically cleared. In this case, the inbound or outbound traffic of the instance will be considered to be new connections, which need to match the inbound or outbound security group rules to ensure that the rules take effect immediately and ensure the security of incoming traffic.
-  A modified firewall rule will not immediately take effect for its existing connections. It takes about 120 seconds for the new rule to take effect, and traffic will be interrupted during this period. To ensure that the traffic is immediately interrupted after the rule is changed, it is recommended that you configure security group rules.
