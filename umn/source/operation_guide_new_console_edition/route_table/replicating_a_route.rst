:original_name: vpc_route_0013.html

.. _vpc_route_0013:

Replicating a Route
===================

Scenarios
---------

You can replicate a created route as required.

Notes and Constraints
---------------------

-  The routes delivered by the VPN service to the default route table cannot be replicated.
-  The routes delivered to the default route table by the Direct Connect service that is enabled by call or email cannot be replicated.
-  Black hole routes cannot be replicated.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the route table list, locate the row that contains the target route table and click **Replicate Route** in the **Operation** column.

#. Select the target route table and then the route to be replicated as prompted.

   The routes listed on the page are those that do not exist in the target route table. You can select one or more routes to replicate to the target route table.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
