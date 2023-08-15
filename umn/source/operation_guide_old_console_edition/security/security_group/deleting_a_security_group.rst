:original_name: vpc_SecurityGroup02_0011.html

.. _vpc_SecurityGroup02_0011:

Deleting a Security Group
=========================

Scenarios
---------

This section describes how to delete security groups.

Notes and Constraints
---------------------

-  The default security group is named **default** and cannot be deleted.

-  A security group cannot be deleted if it is being used by instances, such as cloud servers, containers, and databases.

   If you need to delete such a security group, delete the instances or change the security group used by the instance first.

-  A security group cannot be deleted if it is used as the source or destination of a rule in another security group.

   :ref:`Delete <vpc_securitygroup02_0009>` or :ref:`modify <vpc_securitygroup02_0008>` the rule and delete the security group again.

   For example, if the source of a rule in security group **sg-B** is set to **sg-A**, you need to delete or modify the rule in **sg-B** before deleting **sg-A**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. Locate the row that contains the target security group, click **More** in the **Operation** column, and click **Delete**.

   A confirmation dialog box is displayed.

#. Confirm the information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
