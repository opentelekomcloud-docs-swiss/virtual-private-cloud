:original_name: en-us_topic_0030969470.html

.. _en-us_topic_0030969470:

Adding a Security Group Rule
============================

Scenarios
---------

A security group is a collection of access control rules to control the traffic that is allowed to reach and leave the cloud resources that it is associated with. The cloud resources can be cloud servers, containers, databases, and more. A security group consists of inbound and outbound rules.

Like whitelists, security group rules work as follows:

-  Inbound rules control incoming traffic to instances in the security group. If an inbound request matches the source in an inbound security group rule with **Action** set to **Allow**, the request is allowed.

   Unless otherwise specified, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rules control outgoing traffic from instances in the security group. If the destination of an outbound security group rule with **Action** set to **Allow** is 0.0.0.0/0, all outbound requests are allowed.

   0.0.0.0/0 represents all IPv4 addresses.

If the rules of the security group associated with your instance cannot meet your requirements, for example, you need to allow inbound traffic on a specific TCP port, you can add an inbound rule to allow traffic on the TCP port.

Security Group Rule Configuration Examples
------------------------------------------

-  The system provides a default security group. For details about the default security group rules, see :ref:`Default Security Groups and Security Group Rules <securitygroup_0003>`. If the default security group rules cannot meet your requirements, you can modify them.
-  Before configuring security group rules, you need to plan rules for communications among instances in the security group. For more security group rule configuration examples, see :ref:`Security Group Configuration Examples <en-us_topic_0081124350>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. Locate the row that contains the target security group, click **Manage Rule** in the **Operation** column.

   The page for configuring security group rules is displayed.

#. On the **Inbound Rules** tab, click **Add Rule**.

   The **Add Inbound Rule** dialog box is displayed.

#. Configure required parameters.

   You can click **+** to add more inbound rules.


   .. figure:: /_static/images/en-us_image_0000001233786243.png
      :alt: **Figure 1** Add Inbound Rule

      **Figure 1** Add Inbound Rule

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                              | Example Value         |
      +=======================+==========================================================================================================================================================================+=======================+
      | Type                  | Source IP address version. You can select:                                                                                                                               | IPv4                  |
      |                       |                                                                                                                                                                          |                       |
      |                       | -  IPv4                                                                                                                                                                  |                       |
      |                       | -  IPv6                                                                                                                                                                  |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                 | TCP                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which the traffic can reach your ECS. The value ranges from 1 to 65535.                                                            | 22, or 22-30          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                          |                       |
      |                       | -  IP address:                                                                                                                                                           |                       |
      |                       |                                                                                                                                                                          |                       |
      |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                |                       |
      |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                        |                       |
      |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                   |                       |
      |                       |                                                                                                                                                                          |                       |
      |                       | -  Security group: sg-A                                                                                                                                                  |                       |
      |                       |                                                                                                                                                                          |                       |
      |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                    |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                     | N/A                   |
      |                       |                                                                                                                                                                          |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                  |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   The inbound rule list is displayed.

#. On the **Outbound Rules** tab, click **Add Rule**.

   The **Add Outbound Rule** dialog box is displayed.

#. Configure required parameters.

   You can click **+** to add more outbound rules.


   .. figure:: /_static/images/en-us_image_0000001233907913.png
      :alt: **Figure 2** Add Outbound Rule

      **Figure 2** Add Outbound Rule

   .. table:: **Table 2** Outbound rule parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                 | Example Value         |
      +=======================+=============================================================================================================================================================================+=======================+
      | Type                  | Destination IP address version. You can select:                                                                                                                             | IPv4                  |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  IPv4                                                                                                                                                                     |                       |
      |                       | -  IPv6                                                                                                                                                                     |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                    | TCP                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which the traffic can leave your ECS. The value ranges from 1 to 65535.                                                               | 22, or 22-30          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  IP address:                                                                                                                                                              |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                   |                       |
      |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                           |                       |
      |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                      |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  Security group: sg-A                                                                                                                                                     |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                        | N/A                   |
      |                       |                                                                                                                                                                             |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                     |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   The outbound rule list is displayed.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
