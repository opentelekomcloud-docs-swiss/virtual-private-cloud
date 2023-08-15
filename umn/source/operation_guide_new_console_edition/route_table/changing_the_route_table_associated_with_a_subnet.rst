:original_name: vpc_route_0008.html

.. _vpc_route_0008:

Changing the Route Table Associated with a Subnet
=================================================

Scenarios
---------

You can change the route table associated with the subnet to another one in the VPC. If the route table for a subnet is changed, routes in the new route table will apply to all cloud resources in the subnet. Determine the impact on services before performing this operation.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the route table list, click the name of the target route table.

#. On the **Associated Subnets** tab page, click **Change Route Table** in the **Operation** column and select a new route table as prompted.

#. Click **OK**.

   After the route table for a subnet is changed, routes in the new route table will apply to all cloud resources in the subnet.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
