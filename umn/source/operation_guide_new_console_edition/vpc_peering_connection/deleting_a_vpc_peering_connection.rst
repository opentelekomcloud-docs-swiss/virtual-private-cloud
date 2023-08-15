:original_name: vpc_peering_0003.html

.. _vpc_peering_0003:

Deleting a VPC Peering Connection
=================================

Scenarios
---------

This section describes how to delete a VPC peering connection.

Either owner of a VPC in a peering connection can delete the VPC peering connection in any state.

Notes and Constraints
---------------------

The owner of either VPC in a peering connection can delete the VPC peering connection at any time. Deleting a VPC peering connection will also delete all information about this connection, including the routes in the local and peer VPC route tables added for the connection.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under , click **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, click **VPC Peering**.

   The VPC peering connection list is displayed.

5. In the VPC peering connection list, locate the row that contains the target VPC peering connection and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

6. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
