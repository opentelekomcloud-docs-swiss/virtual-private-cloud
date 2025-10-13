:original_name: vpc_qs_0012.html

.. _vpc_qs_0012:

Step 4: Create a Security Group
===============================

Scenarios
---------

A security group is a collection of access control rules to control the traffic that is allowed to reach and leave the cloud resources that it is associated with. The cloud resources can be cloud servers, containers, databases, and more. Cloud resources associated with the same security group have the same security requirements and are mutually trusted within a VPC. A security group consists of inbound and outbound rules.

If your instances have different Internet access requirements, you can allocate them to different security groups when creating them.

Each ECS must be associated with at least one security group. If you do not have a security group when creating an ECS, the system provides a default security group.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the upper right corner, click **Create Security Group**.

   The **Create Security Group** page is displayed.

#. Configure the parameters as prompted.

   .. table:: **Table 1** Parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Parameter             | Description                                                                                                                                                                                                                    | Example Value              |
      +=======================+================================================================================================================================================================================================================================+============================+
      | Name                  | Mandatory                                                                                                                                                                                                                      | sg-AB                      |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | Enter the security group name.                                                                                                                                                                                                 |                            |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | The security group name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                           |                            |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | .. note::                                                                                                                                                                                                                      |                            |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       |    You can change the security group name after a security group is created. It is recommended that you give each security group a different name.                                                                             |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Enterprise Project    | Mandatory                                                                                                                                                                                                                      | default                    |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | When creating a security group, you can add the security group to an enabled enterprise project.                                                                                                                               |                            |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | An enterprise project facilitates project-level management and grouping of cloud resources and users. The name of the default project is **default**.                                                                          |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Template              | Mandatory                                                                                                                                                                                                                      | General-purpose web server |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | The system provides several security group templates for you to create a security group. A security group template has preconfigured inbound and outbound rules. You can select a template based on your service requirements. |                            |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | :ref:`Table 1 <en-us_topic_0013748715__table117828131111>` describes the security group templates.                                                                                                                             |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Description           | Optional                                                                                                                                                                                                                       | N/A                        |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | Supplementary information about the security group. This parameter is optional.                                                                                                                                                |                            |
      |                       |                                                                                                                                                                                                                                |                            |
      |                       | The security group description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                             |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+

#. Confirm the inbound and outbound rules of the template and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582681.png
