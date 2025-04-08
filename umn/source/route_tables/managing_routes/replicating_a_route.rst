:original_name: vpc_route01_0013.html

.. _vpc_route01_0013:

Replicating a Route
===================

Scenarios
---------

This section describes how to replicate routes among all route tables of a VPC. VPC route tables include the default and custom route tables.

Notes and Constraints
---------------------

:ref:`Table 1 <vpc_route01_0013__en-us_topic_0121831807_table1727714140542>` shows whether routes of different types can be replicated to default or custom route tables.

For example, if the next hop type of a route is a server, this route can be replicated to both default or custom route tables. If the next hop type of a route is a Direct Connect gateway, the route cannot be replicated to the default route table, but can be replicated to a custom route table.

.. _vpc_route01_0013__en-us_topic_0121831807_table1727714140542:

.. table:: **Table 1** Route replication

   +------------------------+------------------------------------------+-----------------------------------------+
   | Next Hop Type          | Can Be Replicated to Default Route Table | Can Be Replicated to Custom Route Table |
   +========================+==========================================+=========================================+
   | Local                  | No                                       | No                                      |
   +------------------------+------------------------------------------+-----------------------------------------+
   | Server                 | Yes                                      | Yes                                     |
   +------------------------+------------------------------------------+-----------------------------------------+
   | Extension NIC          | Yes                                      | Yes                                     |
   +------------------------+------------------------------------------+-----------------------------------------+
   | Direct Connect gateway | No                                       | Yes                                     |
   +------------------------+------------------------------------------+-----------------------------------------+
   | VPC peering connection | Yes                                      | Yes                                     |
   +------------------------+------------------------------------------+-----------------------------------------+
   | Virtual IP address     | Yes                                      | Yes                                     |
   +------------------------+------------------------------------------+-----------------------------------------+

.. note::

   -  Black hole routes cannot be replicated.
   -  If the Direct Connect service is enabled by call or email, the routes delivered to the default route table cannot be replicated to a custom route table.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Route Tables**.

5. In the route table list, locate the row that contains the route table you want to replicate routes from and click **Replicate Route** in the **Operation** column.

6. Select the target route table that you want to replicate route to and the routes to be replicated as prompted.

   The listed routes are those that do not exist in the target route table. You can select one or more routes to replicate to the target route table.

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823270.png
