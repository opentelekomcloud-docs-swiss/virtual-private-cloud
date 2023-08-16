:original_name: vpc_vpc02_0008.html

.. _vpc_vpc02_0008:

Managing VPC Tags
=================

Scenarios
---------

A VPC tag identifies a VPC. Tags can be added to VPCs to facilitate VPC identification and management. You can add a tag to a VPC when creating the VPC, or you can add a tag to a created VPC on the VPC details page. A maximum of 20 tags can be added to each VPC.

A tag consists of a key and value pair. :ref:`Table 1 <vpc_vpc02_0008__en-us_topic_0118498924_ted9687ca14074ef785241145365a6175>` lists the tag key and value requirements.

.. _vpc_vpc02_0008__en-us_topic_0118498924_ted9687ca14074ef785241145365a6175:

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
   |                       |    -  Special characters, including hyphens (-) and underscores (_)    |                       |
   +-----------------------+------------------------------------------------------------------------+-----------------------+
   | Value                 | -  Can contain a maximum of 43 characters.                             | vpc-01                |
   |                       | -  Can contain only the following character types:                     |                       |
   |                       |                                                                        |                       |
   |                       |    -  Uppercase letters                                                |                       |
   |                       |    -  Lowercase letters                                                |                       |
   |                       |    -  Digits                                                           |                       |
   |                       |    -  Special characters, including hyphens (-) and underscores (_)    |                       |
   +-----------------------+------------------------------------------------------------------------+-----------------------+

Procedure
---------

**Search for VPCs by tag key and value on the page showing the VPC list.**

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **Virtual Private Cloud**.

#. In the upper right corner of the VPC list, click **Search by Tag**.

#. In the displayed area, enter the tag key and value of the VPC you are looking for.

   Both the tag key and value must be specified. The system automatically displays the VPCs you are looking for if both the tag key and value are matched.

#. Click + to add more tag keys and values.

   You can add multiple tag keys and values to refine your search results. If you add more than one tag to search for VPCs, the VPCs containing all specified tags will be displayed.

#. Click **Search**.

   The system displays the VPCs you are looking for based on the entered tag keys and values.

**Add, delete, edit, and view tags on the Tags tab of a VPC.**

#. Log in to the management console.

#. Click |image2| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **Virtual Private Cloud**.

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

      Locate the row that contains the tag you want to delete, and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0141273034.png
