:original_name: vpc_route01_0005.html

.. _vpc_route01_0005:

Creating a Custom Route Table
=============================

Scenarios
---------

A VPC automatically comes with a default route table. If your default route table cannot meet your service requirements, you can create a custom route table.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Route Tables**.

5. In the upper right corner, click **Create Route Table**. On the displayed page, configure parameters as prompted.


   .. figure:: /_static/images/en-us_image_0000001818983038.png
      :alt: **Figure 1** Create Route Table

      **Figure 1** Create Route Table

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================================+=======================+
      | Name                  | The name of the route table. This parameter is mandatory.                                                                                                             | rtb-001               |
      |                       |                                                                                                                                                                       |                       |
      |                       | The name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces. |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | VPC                   | The VPC that the route table belongs to. This parameter is mandatory.                                                                                                 | vpc-001               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the route table. This parameter is optional.                                                                                          | ``-``                 |
      |                       |                                                                                                                                                                       |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                   |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Route Settings        | The route information. This parameter is optional.                                                                                                                    | ``-``                 |
      |                       |                                                                                                                                                                       |                       |
      |                       | You can add a route when creating the route table or after the route table is created. For details, see :ref:`Adding a Custom Route <vpc_route01_0006>`.              |                       |
      |                       |                                                                                                                                                                       |                       |
      |                       | You can click **+** to add more routes.                                                                                                                               |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

6. Click **OK**.

   A message is displayed. You can determine whether to associate the route table with subnets immediately as prompted. If you want to associate immediately, perform the following operations:

   a. Click **Associate Subnet**. The route table details page is displayed.
   b. Click **Associate Subnet** and select the target subnets to be associated.
   c. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823254.png
