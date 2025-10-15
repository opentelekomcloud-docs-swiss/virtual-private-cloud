:original_name: vpc010016.html

.. _vpc010016:

Supported VPC Operations
========================

With CTS, you can record operations performed on the VPC service for further query, audit, and backtracking purposes.

:ref:`Table 1 <vpc010016__table18198201795918>` lists the VPC operations that can be recorded by CTS.

.. _vpc010016__table18198201795918:

.. table:: **Table 1** VPC operations that can be recorded by CTS

   +----------------------------------------+----------------------+---------------------------+
   | Operation                              | Resource Type        | Trace                     |
   +========================================+======================+===========================+
   | Modifying a bandwidth                  | Bandwidth            | modifyBandwidth           |
   +----------------------------------------+----------------------+---------------------------+
   | Assigning an EIP                       | EIP                  | createEip                 |
   +----------------------------------------+----------------------+---------------------------+
   | Releasing an EIP                       | EIP                  | deleteEip                 |
   +----------------------------------------+----------------------+---------------------------+
   | Binding an EIP                         | EIP                  | bindEip                   |
   +----------------------------------------+----------------------+---------------------------+
   | Unbinding an EIP                       | EIP                  | unbindEip                 |
   +----------------------------------------+----------------------+---------------------------+
   | Assigning a private IP address         | Private IP address   | createPrivateIp           |
   +----------------------------------------+----------------------+---------------------------+
   | Releasing a private IP address         | Private IP address   | deletePrivateIp           |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a security group              | security_groups      | createSecurity-group      |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a security group              | security_groups      | updateSecurity-group      |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a security group              | security_groups      | deleteSecurity-group      |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a security group rule         | security-group-rules | createSecurity-group-rule |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a security group rule         | security-group-rules | updateSecurity-group-rule |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a security group rule         | security-group-rules | deleteSecurity-group-rule |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a subnet                      | Subnet               | createSubnet              |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a subnet                      | Subnet               | deleteSubnet              |
   +----------------------------------------+----------------------+---------------------------+
   | Modifying a subnet                     | Subnet               | modifySubnet              |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a VPC                         | VPC                  | createVpc                 |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a VPC                         | VPC                  | deleteVpc                 |
   +----------------------------------------+----------------------+---------------------------+
   | Modifying a VPC                        | VPC                  | modifyVpc                 |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a VPN                         | VPN                  | createVpn                 |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a VPN                         | VPN                  | deleteVpn                 |
   +----------------------------------------+----------------------+---------------------------+
   | Modifying a VPN                        | VPN                  | modifyVpn                 |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a router                      | routers              | createRouter              |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a router                      | routers              | updateRouter              |
   +----------------------------------------+----------------------+---------------------------+
   | Adding an interface to a router        | routers              | addRouterInterface        |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting an interface from a router    | routers              | removeRouterInterface     |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a port                        | ports                | createPort                |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a port                        | ports                | updatePort                |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a port                        | ports                | deletePort                |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a network                     | networks             | createNetwork             |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a network                     | networks             | updateNetwork             |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a network                     | networks             | deleteNetwork             |
   +----------------------------------------+----------------------+---------------------------+
   | Batch creating or deleting subnet tags | tag                  | batchUpdateTags           |
   +----------------------------------------+----------------------+---------------------------+
   | Batch creating or deleting VPC tags    | tag                  | batchUpdateVpcTags        |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a route table                 | routetables          | createRouteTable          |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a route table                 | routetables          | updateRouteTable          |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a route table                 | routetables          | deleteRouteTable          |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a VPC peering connection      | vpc-peerings         | createVpcPeerings         |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a VPC peering connection      | vpc-peerings         | updateVpcPeerings         |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a VPC peering connection      | vpc-peerings         | deleteVpcPeerings         |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a firewall group              | firewall-groups      | createFirewallGroup       |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a firewall group              | firewall-groups      | updateFirewallGroup       |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a firewall group              | firewall-groups      | deleteFirewallGroup       |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a firewall policy             | firewall-policies    | createFirewallPolicy      |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a firewall policy             | firewall-policies    | updateFirewallPolicy      |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a firewall policy             | firewall-policies    | deleteFirewallPolicy      |
   +----------------------------------------+----------------------+---------------------------+
   | Inserting a firewall rule              | firewall-policies    | insertFirewallPolicyRule  |
   +----------------------------------------+----------------------+---------------------------+
   | Removing a firewall rule               | firewall-policies    | removeFirewallPolicyRule  |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a firewall rule               | firewall-rules       | createFirewallRule        |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a firewall rule               | firewall-rules       | updateFirewallRule        |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a firewall rule               | firewall-rules       | deleteFirewallRule        |
   +----------------------------------------+----------------------+---------------------------+
   | Creating a flow log                    | flowlogs             | createFlowLog             |
   +----------------------------------------+----------------------+---------------------------+
   | Updating a flow log                    | flowlogs             | updateFlowLog             |
   +----------------------------------------+----------------------+---------------------------+
   | Deleting a flow log                    | flowlogs             | deleteFlowLog             |
   +----------------------------------------+----------------------+---------------------------+
