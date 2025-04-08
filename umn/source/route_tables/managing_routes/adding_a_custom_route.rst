:original_name: vpc_route01_0006.html

.. _vpc_route01_0006:

Adding a Custom Route
=====================

Scenarios
---------

Each route table contains a default system route, which indicates that ECSs in a VPC can communicate with each other. You can also add custom routes as required to forward the traffic destined for the destination to the specified next hop.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Route Tables**.

5. In the route table list, click the name of the route table to which you want to add a route.

6. Click **Add Route** and set parameters as prompted.

   You can click **+** to add more routes.


   .. figure:: /_static/images/en-us_image_0000001818823258.png
      :alt: **Figure 1** Add Route

      **Figure 1** Add Route

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Parameter             | Description                                                                                                                                                          | Example Value          |
      +=======================+======================================================================================================================================================================+========================+
      | Destination           | Mandatory                                                                                                                                                            | IPv4: 192.168.0.0/16   |
      |                       |                                                                                                                                                                      |                        |
      |                       | Enter the destination of the route. You can enter a single IP address or an IP address range in CIDR notation.                                                       |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | The destination of each route in a route table must be unique. The destination cannot overlap with any subnet in the VPC.                                            |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop Type         | Mandatory                                                                                                                                                            | VPC peering connection |
      |                       |                                                                                                                                                                      |                        |
      |                       | Set the type of the next hop.                                                                                                                                        |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | .. note::                                                                                                                                                            |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       |    When you add or modify a custom route in a default route table, the next hop type of the route cannot be set to **VPN connection** or **Direct Connect gateway**. |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop              | Mandatory                                                                                                                                                            | peer-AB                |
      |                       |                                                                                                                                                                      |                        |
      |                       | Set the next hop. The resources in the drop-down list box are displayed based on the selected next hop type.                                                         |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Description           | Optional                                                                                                                                                             | ``-``                  |
      |                       |                                                                                                                                                                      |                        |
      |                       | Enter the description of the route in the text box as required.                                                                                                      |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865662989.png
