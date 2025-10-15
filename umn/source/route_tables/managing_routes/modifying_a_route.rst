:original_name: vpc_route01_0011.html

.. _vpc_route01_0011:

Modifying a Route
=================

Scenarios
---------

This section describes how to modify a custom route in a route table.

Notes and Constraints
---------------------

-  System routes cannot be modified.
-  When you create a VPC endpoint, VPN or Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. In the route table list, click the name of the target route table.

6. Locate the row that contains the route to be modified and click **Modify** in the **Operation** column.

7. Modify the route information in the displayed dialog box.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Item                  | Description                                                                                                                                                          | Example Value         |
      +=======================+======================================================================================================================================================================+=======================+
      | Destination Type      | Mandatory                                                                                                                                                            | IP address            |
      |                       |                                                                                                                                                                      |                       |
      |                       | The destination can be:                                                                                                                                              |                       |
      |                       |                                                                                                                                                                      |                       |
      |                       | -  **IP address**: Select this option if you want to enter an IP address or IP address range.                                                                        |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | Mandatory                                                                                                                                                            | IPv4: 192.168.0.0/16  |
      |                       |                                                                                                                                                                      |                       |
      |                       | Enter the destination of the route. You can enter a single IP address or an IP address range in CIDR notation.                                                       |                       |
      |                       |                                                                                                                                                                      |                       |
      |                       | The destination of each route must be unique. The destination cannot overlap with any subnet CIDR block in the VPC.                                                  |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Next Hop Type         | Mandatory                                                                                                                                                            | VPC peering           |
      |                       |                                                                                                                                                                      |                       |
      |                       | Set the type of the next hop.                                                                                                                                        |                       |
      |                       |                                                                                                                                                                      |                       |
      |                       | .. note::                                                                                                                                                            |                       |
      |                       |                                                                                                                                                                      |                       |
      |                       |    When you add or modify a custom route in a default route table, the next hop type of the route cannot be set to **VPN connection** or **Direct Connect gateway**. |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Next Hop              | Mandatory                                                                                                                                                            | peer-AB               |
      |                       |                                                                                                                                                                      |                       |
      |                       | Set the next hop. The resources in the drop-down list box are displayed based on the selected next hop type.                                                         |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Optional                                                                                                                                                             | ``-``                 |
      |                       |                                                                                                                                                                      |                       |
      |                       | Enter the description of the route in the text box as required.                                                                                                      |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

8. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823338.png
