:original_name: vpc_route01_0007.html

.. _vpc_route01_0007:

Associating a Route Table with a Subnet
=======================================

Scenarios
---------

After a subnet is created, the system associates the subnet with the default route table of its VPC. If you want to use specific routes for a subnet, you can associate the subnet with a custom route table.

The custom route table associated with a subnet affects only the outbound traffic. The default route table determines the inbound traffic.

.. important::

   After a route table is associated with a subnet, the routes in the route table control the routing for the subnet and apply to all cloud resources in the subnet.

Notes and Constraints
---------------------

-  A subnet must have a route table associated and can only be associated with one route table.
-  A route table can be associated with multiple subnets.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. In the route table list, locate the row that contains the target route table and click **Associate Subnet** in the **Operation** column.

6. Select the subnet to be associated.


   .. figure:: /_static/images/en-us_image_0000001865662969.png
      :alt: **Figure 1** Associate Subnet

      **Figure 1** Associate Subnet

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983026.png
