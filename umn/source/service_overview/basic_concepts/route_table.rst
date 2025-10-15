:original_name: en-us_topic_0038263963.html

.. _en-us_topic_0038263963:

Route Table
===========

Route Tables
------------

A route table contains a set of routes that are used to determine where network traffic from your subnets in a VPC is directed. Each subnet must be associated with a route table. A subnet can only be associated with one route table, but you can associate multiple subnets with the same route table.

Both IPv4 and IPv6 routes are supported.


.. figure:: /_static/images/en-us_image_0000001865662949.png
   :alt: **Figure 1** Route tables

   **Figure 1** Route tables

-  Default route table: When you create a VPC, the system automatically generates a default route table for the VPC. If you create a subnet in the VPC, the subnet automatically associates with the default route table. The default route table ensures that subnets in a VPC can communicate with each other.

   -  You can add routes to, delete routes from, and modify routes in the default route table, but cannot delete the table.
   -  When you create a VPC endpoint, VPN or Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified.

-  Custom route table: If you do not want to use the default route table, you can create a custom route table and associate it with the subnet. Custom route tables can be deleted if they are no longer required.

Route
-----

You can add routes to default and custom route tables and configure the destination type, destination, next hop type, and next hop in the routes to determine where network traffic is directed. Routes are classified into system routes and custom routes.

-  System routes: These routes are automatically added by the system and cannot be modified or deleted.

   After a route table is created, the system automatically adds the following system routes to the route table, so that instances in a VPC can communicate with each other.

   -  Routes whose destination is 100.64.0.0/10 or 198.19.128.0/20.

   -  Routes whose destination is a subnet CIDR block.

      If you enable IPv6 when creating a subnet, the system automatically assigns an IPv6 CIDR block to the subnet. Then, you can view IPv6 routes in its route table. Example destinations of subnet CIDR blocks are as follows:

      -  IPv4: 192.168.2.0/24
      -  IPv6: 2407:c080:802:be7::/64

      .. note::

         In addition to the preceding system routes, the system automatically adds a route whose destination is 127.0.0.0/8. This is the local loopback address.

-  Custom routes: These are routes that you can add, modify, and delete. The destination of a custom route cannot overlap with that of a system route.

   You can add a custom route and configure the destination, next hop type, and next hop in the route to determine where network traffic is directed. :ref:`Table 1 <en-us_topic_0038263963__en-us_topic_0121831807_table1727714140542>` lists the supported types of next hops.

   You cannot add two routes with the same destination to a VPC route table even if their next hop types are different. The route priority depends on the destination. According to the longest match routing rule, the destination with a higher matching degree is preferentially selected for packet forwarding.

   .. _en-us_topic_0038263963__en-us_topic_0121831807_table1727714140542:

   .. table:: **Table 1** Next hop type

      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop Type          | Description                                                                                                                                                  | Supported Route Table  |
      +========================+==============================================================================================================================================================+========================+
      | Server                 | Traffic intended for the destination is forwarded to an ECS in the VPC.                                                                                      | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Extension NIC          | Traffic intended for the destination is forwarded to the extended network interface of an ECS in the VPC.                                                    | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | VPN connection         | Traffic intended for the destination is forwarded to a VPN gateway.                                                                                          | Custom route table     |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Direct Connect gateway | Traffic intended for the destination is forwarded to a Direct Connect gateway.                                                                               | Custom route table     |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | VPC peering connection | Traffic intended for the destination is forwarded to a VPC peering connection.                                                                               | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Virtual IP address     | Traffic intended for the destination is forwarded to a virtual IP address and then sent to active and standby ECSs to which the virtual IP address is bound. | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

   .. note::

      If you specify the destination when creating a resource, a system route is delivered. If you do not specify a destination when creating a resource, a custom route that can be modified or deleted is delivered.

      When you create a VPN connection or a Direct Connect gateway, you need to specify the remote subnet, that is, the destination of a route. In this case, the system delivers this system route. Do not modify the route destination on the **Route Tables** page. If you do, the destination will be inconsistent with the configured remote subnet. To modify the route destination, go to the specific resource page and modify the remote subnet, then the route destination will be changed accordingly.
