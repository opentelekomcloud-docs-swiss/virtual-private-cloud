:original_name: vpc_route01_0010.html

.. _vpc_route01_0010:

Deleting a Route Table
======================

Scenarios
---------

This section describes how to delete a custom route table.

Notes and Constraints
---------------------

-  The default route table cannot be deleted.

-  A custom route table with a subnet associated cannot be deleted directly.

   If you want to delete such a route table, you can associate the subnet with another route table first by referring to :ref:`Changing the Route Table Associated with a Subnet <vpc_route01_0008>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**. The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. Locate the row that contains the route table you want to delete and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

6. Enter **DELETE** as prompted and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983042.png
