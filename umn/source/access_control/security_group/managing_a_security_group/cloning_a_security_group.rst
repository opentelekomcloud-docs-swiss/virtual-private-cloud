:original_name: vpc_SecurityGroup_0009.html

.. _vpc_SecurityGroup_0009:

Cloning a Security Group
========================

Scenarios
---------

You can clone a security group from one region to another to quickly apply the security group rules to ECSs in another region.

You can clone a security group in the following scenarios:

-  For example, you have security group **sg-A** in region A. If ECSs in region B require the same security group rules as those configured for security group **sg-A**, you can clone security group **sg-A** to region B, freeing you from creating a new security group in region B.
-  If you need new security group rules, you can clone the original security group as a backup.
-  Before you modify security group rules used by a service, you can clone the security group and modify the security group rules in the test environment to ensure that the modified rules work.

Notes and Constraints
---------------------

-  You can clone a security group from the same or a different region.

   -  If you want to clone a security group from the same region, you can clone all rules in the security group.
   -  If you want to clone a security group from a different region, the system will clone only rules whose source and destination are IP addresses and rules whose source and destination is the current security group.

-  Cloning a security group clones its security group rules, but not the instances associated with the security group.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. Locate the row that contains the security group, click **More** in the **Operation** column, and click **Clone**.

#. Select the region and name of the new security group as prompted.

#. Click **OK**.

   You can then switch to the required region to view the cloned security group in the security group list.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982762.png
