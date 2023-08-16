:original_name: vpc_route_0007.html

.. _vpc_route_0007:

Associating a Subnet with a Route Table
=======================================

Scenarios
---------

After a route table is associated with a subnet, the routes in the route table control the routing for the subnet and apply to all cloud resources in the subnet. Determine the impact on services before performing this operation.

Notes and Constraints
---------------------

A subnet can only be associated with one route table.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the route table list, locate the row that contains the target route table and click **Associate Subnet** in the **Operation** column.

#. Select the subnet to be associated.


   .. figure:: /_static/images/en-us_image_0173155870.png
      :alt: **Figure 1** Associate Subnet

      **Figure 1** Associate Subnet

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
