:original_name: vpc_SecurityGroup02_0004.html

.. _vpc_SecurityGroup02_0004:

Creating a Security Group
=========================

Scenarios
---------

A security group is a collection of access control rules to control the traffic that is allowed to reach and leave the cloud resources that it is associated with. The cloud resources can be cloud servers, containers, databases, and more. A security group consists of inbound and outbound rules.

Notes and Constraints
---------------------

Each ECS must be associated with at least one security group. If you have no security group when creating an ECS, the system automatically creates a default security group (default) for the ECS. For details about the rules in the default security group, see :ref:`Default Security Groups and Security Group Rules <vpc_securitygroup02_0002>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the upper right corner, click **Create Security Group**.

   The **Create Security Group** page is displayed.

#. Configure the parameters as prompted.

   .. table:: **Table 1** Parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                          | Example Value         |
      +=======================+======================================================================================================================================================================================+=======================+
      | Name                  | Mandatory                                                                                                                                                                            | sg-AB                 |
      |                       |                                                                                                                                                                                      |                       |
      |                       | Enter the security group name.                                                                                                                                                       |                       |
      |                       |                                                                                                                                                                                      |                       |
      |                       | The security group name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces. |                       |
      |                       |                                                                                                                                                                                      |                       |
      |                       | .. note::                                                                                                                                                                            |                       |
      |                       |                                                                                                                                                                                      |                       |
      |                       |    You can change the security group name after a security group is created. It is recommended that you give each security group a different name.                                   |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Optional                                                                                                                                                                             | N/A                   |
      |                       |                                                                                                                                                                                      |                       |
      |                       | Supplementary information about the security group. This parameter is optional.                                                                                                      |                       |
      |                       |                                                                                                                                                                                      |                       |
      |                       | The security group description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                   |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Confirm the inbound and outbound rules of the template and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
