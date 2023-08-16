:original_name: vpc_route_0006.html

.. _vpc_route_0006:

Adding a Custom Route
=====================

Scenarios
---------

Each route table contains a default system route, which indicates that ECSs in a VPC can communicate with each other. You can add custom routes as required to forward the traffic destined for the destination to the specified next hop.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Route Tables**.

#. In the route table list, click the name of the route table to which you want to add a route.

#. Click **Add Route** and set parameters as prompted.

   You can click **+** to add more routes.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+
      | Parameter             | Description                                                                                                                                                       | Example Value                |
      +=======================+===================================================================================================================================================================+==============================+
      | Destination           | The destination CIDR block.                                                                                                                                       | IPv4: 192.168.0.0/16         |
      |                       |                                                                                                                                                                   |                              |
      |                       | The destination of each route must be unique. The destination cannot overlap with any subnet CIDR block in the VPC.                                               | IPv6: 2407:c080:802:aba::/64 |
      |                       |                                                                                                                                                                   |                              |
      |                       | The destination can be an IPv4 or IPv6 CIDR block.                                                                                                                |                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+
      | Next Hop Type         | Set the type of the next hop. For details about the supported resource types, see :ref:`Table 1 <route_0001__en-us_topic_0121831807_table1727714140542>`.         | ECS                          |
      |                       |                                                                                                                                                                   |                              |
      |                       | .. note::                                                                                                                                                         |                              |
      |                       |                                                                                                                                                                   |                              |
      |                       |    When you add a custom route to or modify a custom route in a default route table, the next hop type cannot be set to VPN connection or Direct Connect gateway. |                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+
      | Next Hop              | Set the next hop. The resources in the drop-down list box are displayed based on the selected next hop type.                                                      | ecs-001                      |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+
      | Description           | Supplementary information about the route. This parameter is optional.                                                                                            | ``-``                        |
      |                       |                                                                                                                                                                   |                              |
      |                       | The route description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                         |                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
