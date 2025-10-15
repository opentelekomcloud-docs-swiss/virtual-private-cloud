:original_name: vpc_peering_0006.html

.. _vpc_peering_0006:

Deleting Routes Configured for a VPC Peering Connection
=======================================================

Scenarios
---------

This section describes how to delete routes from the route tables of the local and peer VPCs connected by a VPC peering connection.

-  :ref:`Deleting Routes of a VPC Peering Connection Between VPCs in the Same Account <vpc_peering_0006__section26541722111813>`
-  :ref:`Deleting Routes of a VPC Peering Connection Between VPCs in Different Accounts <vpc_peering_0006__section47866392497>`

.. _vpc_peering_0006__section26541722111813:

Deleting Routes of a VPC Peering Connection Between VPCs in the Same Account
----------------------------------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **VPC Peering Connections**.

   The VPC peering connection list is displayed.

#. In the VPC peering connection list, click the name of the target VPC peering connection.

   The page showing the VPC peering connection details is displayed.

#. In the route list, locate the route and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

#. Confirm the information and click **OK**.

.. _vpc_peering_0006__section47866392497:

Deleting Routes of a VPC Peering Connection Between VPCs in Different Accounts
------------------------------------------------------------------------------

Only the account owner of a VPC in a VPC peering connection can delete the routes added for the connection.

#. .. _vpc_peering_0006__li4105938135810:

   Log in to the management console using the account of the local VPC and delete the route of the local VPC:

   a. Click |image3| in the upper left corner and select the desired region and project.

   b. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

      The **Virtual Private Cloud** page is displayed.

   c. In the navigation pane on the left, choose **Virtual Private Cloud** > **VPC Peering Connections**.

      The VPC peering connection list is displayed.

   d. In the VPC peering connection list, click the name of the target VPC peering connection.

      The page showing the VPC peering connection details is displayed.

   e. In the route list, locate the route and click **Delete** in the **Operation** column.

      A confirmation dialog box is displayed.

   f. Confirm the information and click **OK**.

#. Log in to the management console using the account of the peer VPC and delete the route of the peer VPC by referring to :ref:`1 <vpc_peering_0006__li4105938135810>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823058.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001865582593.png
