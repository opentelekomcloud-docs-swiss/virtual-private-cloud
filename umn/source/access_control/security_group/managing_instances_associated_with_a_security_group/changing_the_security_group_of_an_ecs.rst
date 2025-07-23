:original_name: SecurityGroup_0006.html

.. _SecurityGroup_0006:

Changing the Security Group of an ECS
=====================================

Scenarios
---------

Change the security group associated with the network interface of an ECS.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Click |image2| and choose **Computing** > **Elastic Cloud Server**.

#. In the ECS list, choose **More** > **Manage Network** > **Change Security Group** in the **Operation** column.

   The **Change Security Group** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001865662753.png
      :alt: **Figure 1** Changing a security group

      **Figure 1** Changing a security group

#. Select the network interfaces and security groups.

   You can select multiple security groups. In such a case, the access rules of all the selected security groups apply to the ECS.

   To create a security group, click **Create Security Group**.

   .. note::

      Using multiple security groups may deteriorate ECS network performance. We recommend that you associate no more than five security groups with each ECS.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818823030.png
.. |image2| image:: /_static/images/en-us_image_0000001865662757.jpg
