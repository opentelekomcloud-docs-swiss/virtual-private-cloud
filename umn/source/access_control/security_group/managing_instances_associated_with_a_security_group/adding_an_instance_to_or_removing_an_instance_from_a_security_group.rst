:original_name: SecurityGroup_0017.html

.. _SecurityGroup_0017:

Adding an Instance to or Removing an Instance from a Security Group
===================================================================

Scenarios
---------

When you create an instance, the system automatically adds the instance to a security group for protection.

-  If one security group cannot meet your requirements, you can add an instance to multiple security groups.
-  An instance must be added to at least one security group. If you want to change the security group for an instance, you can add the instance to a new security group and then remove the instance from the original security group.

Adding an Instance to a Security Group
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the security group list, locate the row that contains the security group and click **Manage Instances** in the **Operation** column.

   The **Associated Instances** tab is displayed.

#. Click an instance type.

   The following operations use **Servers** as an example.

#. Click the **Servers** tab and click **Add**.

   The **Add Server** dialog box is displayed.

#. In the server list, select one or more servers and click **OK** to add them to the current security group.

Removing an Instance from a Security Group
------------------------------------------

An instance must be added to at least one security group. If you want to remove an instance from a security group, the instance must be associated with at least two security groups now.

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the security group list, locate the row that contains the security group and click **Manage Instances** in the **Operation** column.

   The **Associated Instances** tab is displayed.

#. Click an instance type.

   The following operations use **Servers** as an example.

#. Click the **Servers** tab, select one or more servers, and click **Remove** in the upper left corner of the server list.

   A confirmation dialog box is displayed.

#. Confirm the information and click **OK**.

Follow-Up Operations
--------------------

You can delete the security groups that you no longer need. Deleting a security group will also delete all security group rules in the security group. For details, see :ref:`Deleting a Security Group <vpc_securitygroup_0008>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982974.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001865582721.png
