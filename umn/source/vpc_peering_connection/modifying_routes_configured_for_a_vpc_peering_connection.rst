:original_name: vpc_peering_0007.html

.. _vpc_peering_0007:

Modifying Routes Configured for a VPC Peering Connection
========================================================

Scenarios
---------

This section describes how to modify the routes added for a VPC peering connection in the route tables of the local and peer VPCs.

-  :ref:`Modifying Routes of a VPC Peering Connection Between VPCs in the Same Account <vpc_peering_0007__section26541722111813>`
-  :ref:`Modifying Routes of a VPC Peering Connection Between VPCs in Different Accounts <vpc_peering_0007__section47866392497>`

You can follow the instructions provided in this section to modify routes based on your requirements.

.. _vpc_peering_0007__section26541722111813:

Modifying Routes of a VPC Peering Connection Between VPCs in the Same Account
-----------------------------------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, click **VPC Peering**.

   The VPC peering connection list is displayed.

#. In the VPC peering connection list, click the name of the target VPC peering connection.

   The page showing the VPC peering connection details is displayed.

#. Modify the route added to the route table of the local VPC:

   a. Click the **Local Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the local VPC is displayed.

   b. Locate the row that contains the route to be modified and click **Modify** in the **Operation** column.

      The **Modify Route** dialog box is displayed.

   c. Modify the route and click **OK**.

#. Modify the route added to the route table of the peer VPC:

   a. Click the **Peer Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   b. Locate the row that contains the route to be modified and click **Modify** in the **Operation** column.

      The **Modify Route** dialog box is displayed.

   c. Modify the route and click **OK**.

.. _vpc_peering_0007__section47866392497:

Modifying Routes of a VPC Peering Connection Between VPCs in Different Accounts
-------------------------------------------------------------------------------

Only the account owner of a VPC can modify the routes added for the connection.

#. .. _vpc_peering_0007__li4105938135810:

   Log in to the management console using the account of the local VPC and modify the route of the local VPC:

   a. Click |image3| in the upper left corner and select the desired region and project.

   b. Click |image4| in the upper left corner and choose > **Virtual Private Cloud**.

      The **Virtual Private Cloud** page is displayed.

   c. In the navigation pane on the left, click **VPC Peering**.

      The VPC peering connection list is displayed.

   d. In the VPC peering connection list, click the name of the target VPC peering connection.

      The page showing the VPC peering connection details is displayed.

   e. Modify the route added to the route table of the local VPC:

      #. Click the **Local Routes** tab and then click the **Route Tables** hyperlink.

         The **Summary** tab of the default route table for the local VPC is displayed.

      #. Locate the row that contains the route to be modified and click **Modify** in the **Operation** column.

         The **Modify Route** dialog box is displayed.

      #. Modify the route and click **OK**.

#. Log in to the management console using the account of the peer VPC and modify the route of the peer VPC by referring to :ref:`1 <vpc_peering_0007__li4105938135810>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865662901.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001818823166.png
