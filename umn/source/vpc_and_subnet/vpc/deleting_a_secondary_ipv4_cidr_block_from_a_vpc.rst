:original_name: vpc_vpc_0008.html

.. _vpc_vpc_0008:

Deleting a Secondary IPv4 CIDR Block from a VPC
===============================================

Scenarios
---------

If a secondary CIDR block of a VPC is no longer required, you can delete it.

-  A secondary IPv4 CIDR block of a VPC can be deleted, but the primary CIDR block cannot be deleted.
-  If you want to delete a secondary CIDR block that contains subnets, you need to delete the subnets first.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the VPC list, locate the target VPC and click **Edit CIDR Block** in the **Operation** column.

   The **Edit CIDR Block** dialog box is displayed.

#. Locate the row that contains the secondary CIDR block to be deleted and click **Delete** in the **Operation** column.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818823194.png
.. |image2| image:: /_static/images/en-us_image_0000001865582729.png
