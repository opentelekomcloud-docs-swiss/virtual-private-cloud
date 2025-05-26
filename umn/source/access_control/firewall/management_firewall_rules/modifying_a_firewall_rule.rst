:original_name: vpc_acl_0005.html

.. _vpc_acl_0005:

Modifying a Firewall Rule
=========================

Scenarios
---------

Modify an inbound or outbound firewall rule based on your network security requirements.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. On the **Inbound Rules** or **Outbound Rules** tab, locate the row that contains the target rule and click **Modify** in the **Operation** column. In the displayed dialog box, configure parameters as prompted. :ref:`Table 1 <vpc_acl_0005__table59686157164549>` lists the parameters to be configured.

   .. _vpc_acl_0005__table59686157164549:

   .. table:: **Table 1** Parameter descriptions

      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Item                       | Description                                                                                                                                                                                                             | Example Value         |
      +============================+=========================================================================================================================================================================================================================+=======================+
      | Priority                   | Specifies the priority of a firewall rule. A smaller priority value represents a higher priority. Each firewall has a default rule whose priority value is an asterisk (``*``). Default rules have the lowest priority. | 3                     |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Status                     | Specifies the status of the firewall. By default, the status is enabled.                                                                                                                                                | Enabled               |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                       | Specifies the firewall type. This parameter is mandatory. You can select a value from the drop-down list. Currently, only **IPv4** and **IPv6** are supported.                                                          | IPv4                  |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Action                     | Specifies the firewall policy. This parameter is mandatory. You can select a value from the drop-down list. Currently, the value can be **Allow** or **Deny**.                                                          | Allow                 |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol                   | Specifies the protocol supported by the firewall. This parameter is mandatory. You can select a value from the drop-down list.                                                                                          | TCP                   |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            | You can select **TCP**, **UDP**, **ICMP**, or **All**.                                                                                                                                                                  |                       |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                     | The source from which the traffic is allowed. The source can be an IP address or IP address range.                                                                                                                      | 0.0.0.0/0             |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            | -  IP address:                                                                                                                                                                                                          |                       |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            |    -  Single IP address: 192.168.10.10/32                                                                                                                                                                               |                       |
      |                            |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                                                       |                       |
      |                            |    -  IP address range: 192.168.1.0/24                                                                                                                                                                                  |                       |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source Port Range          | The source port number or port number range. The value ranges from 1 to 65535. For a port number range, enter two port numbers connected by a hyphen (-). For example, **1-100**.                                       | 22, or 22-30          |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination                | The destination to which the traffic is allowed. The destination can be an IP address or IP address range.                                                                                                              | 0.0.0.0/0             |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            | -  IP address:                                                                                                                                                                                                          |                       |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            |    -  Single IP address: 192.168.10.10/32                                                                                                                                                                               |                       |
      |                            |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                                                       |                       |
      |                            |    -  IP address range: 192.168.1.0/24                                                                                                                                                                                  |                       |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | **Destination Port Range** | The destination port number or port number range. The value ranges from 1 to 65535. For a port number range, enter two port numbers connected by a hyphen (-). For example, **1-100**.                                  | 22, or 22-30          |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            | You must specify this parameter if **TCP** or **UDP** is selected for **Protocol**.                                                                                                                                     |                       |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description                | Provides supplementary information about the firewall network ACL rule. This parameter is optional.                                                                                                                     | ``-``                 |
      |                            |                                                                                                                                                                                                                         |                       |
      |                            | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                     |                       |
      +----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823406.png
