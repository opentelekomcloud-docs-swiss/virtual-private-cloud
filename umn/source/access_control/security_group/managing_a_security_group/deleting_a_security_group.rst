:original_name: vpc_SecurityGroup_0008.html

.. _vpc_SecurityGroup_0008:

Deleting a Security Group
=========================

Scenarios
---------

If your security group is no longer required, you can delete it.

Notes and Constraints
---------------------

-  The default security group is named **default** and cannot be deleted.

-  If you want to delete a security group that is associated with instances, such as cloud servers, containers, and databases, you need to remove the instances from the security group first. For details, see :ref:`Adding an Instance to or Removing an Instance from a Security Group <securitygroup_0017>`.

-  A security group cannot be deleted if it is used as the source or destination of a rule in another security group.

   :ref:`Delete <vpc_securitygroup_0006>` or :ref:`modify <vpc_securitygroup_0005>` the rule and delete the security group again.

   For example, if the source of a rule in security group **sg-B** is set to **sg-A**, you need to delete or modify the rule in **sg-B** before deleting **sg-A**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. Locate the row that contains the target security group, click **More** in the **Operation** column, and click **Delete**.

   A confirmation dialog box is displayed.

#. Enter **DELETE** as prompted and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982846.png
