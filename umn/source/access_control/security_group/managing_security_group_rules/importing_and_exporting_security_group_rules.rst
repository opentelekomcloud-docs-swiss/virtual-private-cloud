:original_name: vpc_SecurityGroup_0007.html

.. _vpc_SecurityGroup_0007:

Importing and Exporting Security Group Rules
============================================

Scenarios
---------

You can configure security group rules in an Excel file and import the rules to the security group. You can also export security group rules to an Excel file. You are advised to use this function in the following scenarios:

-  If you want to quickly create or restore a security group rule, you can import your exported security group rule file to the security group.
-  If you want to back up security group rules locally, you can export the rules to an Excel file.
-  If you want to quickly apply the rules of one security group to another, or if you want to modify multiple rules of the current security group at once, you can import or export existing rules.

Notes and Constraints
---------------------

-  The security group rules to be imported must be configured based on the template. Do not add parameters or change existing parameters. Otherwise, the import will fail.
-  If a security group rule to be imported is the same as an existing one, the security group rule cannot be imported. You can delete the rule and try again.
-  If you want to import rules of the security group in one region to another under one account, only rules with both **Source** and **Destination** set to **IP address** can be applied.
-  If you want to import rules of the security group in one account to the security group in another account, only rules with both **Source** and **Destination** set to **IP address** can be applied.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. On the security group list, click the name of the target security group.

   The security group details page is displayed.

#. Export and import security group rules.

   -  Click **Export Rule** to export all rules of the current security group to an Excel file.

   -  Click **Import Rule** to import security group rules from an Excel file into the current security group.

      :ref:`Table 1 <vpc_securitygroup_0007__table111445216564>` describes the parameters in the template for importing rules.

      .. _vpc_securitygroup_0007__table111445216564:

      .. table:: **Table 1** Template parameters

         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Parameter             | Description                                                                                                                                                    | Example Value                      |
         +=======================+================================================================================================================================================================+====================================+
         | Direction             | The direction in which the security group rule takes effect.                                                                                                   | Inbound                            |
         |                       |                                                                                                                                                                |                                    |
         |                       | -  **Inbound**: Inbound rules control incoming traffic to instances in the security group.                                                                     |                                    |
         |                       | -  **Outbound**: Outbound rules control outgoing traffic from instances in the security group.                                                                 |                                    |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Protocol & Port       | The network protocol used to match traffic in a security group rule.                                                                                           | TCP                                |
         |                       |                                                                                                                                                                |                                    |
         |                       | Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, or more.                                                                                      |                                    |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Protocol & Port       | Destination port used to match traffic in a security group rule. The value can be from 1 to 65535.                                                             | 22, or 22-30                       |
         |                       |                                                                                                                                                                |                                    |
         |                       | Inbound rules control incoming traffic over specific ports to instances in the security group.                                                                 |                                    |
         |                       |                                                                                                                                                                |                                    |
         |                       | Outbound rules control outgoing traffic over specific ports from instances in the security group.                                                              |                                    |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group.    | sg-test[96a8a93f-XXX-d7872990c314] |
         |                       |                                                                                                                                                                |                                    |
         |                       | -  IP address:                                                                                                                                                 |                                    |
         |                       |                                                                                                                                                                |                                    |
         |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                      |                                    |
         |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                              |                                    |
         |                       |    -  IP address range: 192.168.1.0/24                                                                                                                         |                                    |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. | sg-test[96a8a93f-XXX-d7872990c314] |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Description           | (Optional) Supplementary information about the security group rule.                                                                                            | ``-``                              |
         |                       |                                                                                                                                                                |                                    |
         |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                            |                                    |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Last Modified         | The time when the security group was modified.                                                                                                                 | ``-``                              |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582585.png
