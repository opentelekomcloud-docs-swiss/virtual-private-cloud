:original_name: vpc_route_0010.html

.. _vpc_route_0010:

Deleting a Route Table
======================

Scenarios
---------

You can delete custom route tables but cannot delete the default route table.

Prerequisites
-------------

Before deleting a route table, ensure that no subnet has been associated with the custom route table. If there is an associated subnet, associate the subnet with another route table by clicking **Change Route Table** and then delete the custom route table.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Virtual Private Cloud**.
#. In the route table list, locate the row that contains the route table to be deleted and click **Delete** in the **Operation** column.
#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
