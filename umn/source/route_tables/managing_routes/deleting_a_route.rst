:original_name: vpc_route01_0012.html

.. _vpc_route01_0012:

Deleting a Route
================

Scenarios
---------

This section describes how to delete a custom route from a route table.

Notes and Constraints
---------------------

-  System routes cannot be deleted.

-  The routes automatically delivered by VPN or Direct Connect to the default route table cannot be deleted. The next hop types of such routes are:

   -  VPN connection
   -  Direct Connect gateway

   The following figure shows a route with **VPN gateway** as **Next Hop Type**. If you want to delete such a route, click the next hop hyperlink to delete the corresponding resource.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. Locate the target route table and click its name.

   The route table details page is displayed.

6. In the route list, locate the row that contains the route to be deleted and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

7. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823286.png
