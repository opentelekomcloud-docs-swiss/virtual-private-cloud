:original_name: vpc_vpc_0004.html

.. _vpc_vpc_0004:

Managing VPC Tags
=================

Scenarios
---------

You can add tags to VPCs to help you identify and organize them.

You can add a tag to a VPC when creating the VPC, or you can add a tag to a created VPC on the VPC details page. A maximum of 20 tags can be added to each VPC.

A tag consists of a key and value pair. :ref:`Table 1 <vpc_vpc_0004__ted9687ca14074ef785241145365a6175>` lists the tag key and value requirements.

.. _vpc_vpc_0004__ted9687ca14074ef785241145365a6175:

.. table:: **Table 1** VPC tag key and value requirements

   +-----------------------+------------------------------------------------------------------------+-----------------------+
   | Parameter             | Requirements                                                           | Example Value         |
   +=======================+========================================================================+=======================+
   | Key                   | -  Cannot be left blank.                                               | vpc_key1              |
   |                       | -  Must be unique for each VPC and can be the same for different VPCs. |                       |
   |                       | -  Can contain a maximum of 36 characters.                             |                       |
   |                       | -  Can contain only the following character types:                     |                       |
   |                       |                                                                        |                       |
   |                       |    -  Uppercase letters                                                |                       |
   |                       |    -  Lowercase letters                                                |                       |
   |                       |    -  Digits                                                           |                       |
   |                       |    -  Only hyphens (-), underscores (_), and at signs (@) are allowed. |                       |
   +-----------------------+------------------------------------------------------------------------+-----------------------+
   | Value                 | -  Can contain a maximum of 43 characters.                             | vpc-01                |
   |                       | -  Can contain only the following character types:                     |                       |
   |                       |                                                                        |                       |
   |                       |    -  Uppercase letters                                                |                       |
   |                       |    -  Lowercase letters                                                |                       |
   |                       |    -  Digits                                                           |                       |
   |                       |    -  Only underscores (_), hyphens (-), and at signs (@) are allowed. |                       |
   +-----------------------+------------------------------------------------------------------------+-----------------------+

Procedure
---------

**Search for VPCs by tag key and value on the page showing the VPC list.**

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the search box above the VPC list, click anywhere in the search box.

   Click the tag key and then the value as required. The system filters resources based on the tag you select.

   Click anywhere in the search box to add the next tag key and value.

   You can add multiple tag keys and values to refine your search results. If you add more than one tag to search for VPCs, the VPCs containing all specified tags will be displayed.

**Add, delete, edit, and view tags on the Tags tab of a VPC.**

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. On the **Virtual Private Cloud** page, locate the VPC whose tags are to be managed and click the VPC name.

   The page showing details about the particular VPC is displayed.

#. Click the **Tags** tab and perform desired operations on tags.

   -  View tags.

      On the **Tags** tab, you can view details about tags added to the current VPC, including the number of tags and the key and value of each tag.

   -  Add a tag.

      Click **Add Tag** in the upper left corner. In the displayed **Add Tag** dialog box, enter the tag key and value, and click **OK**.

   -  Edit a tag.

      Locate the row that contains the tag you want to edit and click **Edit** in the **Operation** column. In the **Edit Tag** dialog box, change the tag value and click **OK**.

   -  Delete a tag.

      Locate the row that contains the tag you want to delete, and click **Delete** in the **Operation** column. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865583185.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001818983426.png
