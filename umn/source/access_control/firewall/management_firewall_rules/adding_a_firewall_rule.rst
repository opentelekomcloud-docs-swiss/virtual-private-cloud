:original_name: en-us_topic_0051746702.html

.. _en-us_topic_0051746702:

Adding a Firewall Rule
======================

Scenarios
---------

Add an inbound or outbound rule based on your network security requirements.

Notes and Constraints
---------------------

A firewall can contain no more than 20 rules in one direction, or performance will deteriorate.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. On the **Inbound Rules** or **Outbound Rules** tab, click **Add Rule** to add an inbound or outbound rule.

   -  Click **+** to add more rules.
   -  Locate the row that contains the firewall rule and click **Replicate** in the **Operation** column to replicate an existing rule.


   .. figure:: /_static/images/en-us_image_0000002449675548.png
      :alt: **Figure 1** Add Inbound Rule

      **Figure 1** Add Inbound Rule

   .. table:: **Table 1** Parameter descriptions

      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter              | Description                                                                                                                                                                            | Example Value         |
      +========================+========================================================================================================================================================================================+=======================+
      | Type                   | The firewall type. This parameter is mandatory. You can select a value from the drop-down list. Currently, only **IPv4** and **IPv6** are supported.                                   | IPv4                  |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Action                 | The action in the firewall. This parameter is mandatory. You can select a value from the drop-down list. Currently, the value can be **Allow** or **Deny**.                            | Allow                 |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol               | The protocol supported by the firewall. This parameter is mandatory. You can select a protocol from the drop-down list.                                                                | TCP                   |
      |                        |                                                                                                                                                                                        |                       |
      |                        | You can select **TCP**, **UDP**, **ICMP**, or **All**.                                                                                                                                 |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                 | The source from which the traffic is allowed. The source can be an IP address or IP address range.                                                                                     | 0.0.0.0/0             |
      |                        |                                                                                                                                                                                        |                       |
      |                        | -  IP address:                                                                                                                                                                         |                       |
      |                        |                                                                                                                                                                                        |                       |
      |                        |    -  Single IP address: 192.168.10.10/32                                                                                                                                              |                       |
      |                        |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                      |                       |
      |                        |    -  IP address range: 192.168.1.0/24                                                                                                                                                 |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source Port Range      | The source port number or port number range. The value ranges from 1 to 65535. For a port number range, enter two port numbers connected by a hyphen (-). For example, **1-100**.      | 22, or 22-30          |
      |                        |                                                                                                                                                                                        |                       |
      |                        | You must specify this parameter if **TCP** or **UDP** is selected for **Protocol**.                                                                                                    |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination            | The destination to which the traffic is allowed. The destination can be an IP address or IP address range.                                                                             | 0.0.0.0/0             |
      |                        |                                                                                                                                                                                        |                       |
      |                        | -  IP address:                                                                                                                                                                         |                       |
      |                        |                                                                                                                                                                                        |                       |
      |                        |    -  Single IP address: 192.168.10.10/32                                                                                                                                              |                       |
      |                        |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                      |                       |
      |                        |    -  IP address range: 192.168.1.0/24                                                                                                                                                 |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination Port Range | The destination port number or port number range. The value ranges from 1 to 65535. For a port number range, enter two port numbers connected by a hyphen (-). For example, **1-100**. | 22, or 22-30          |
      |                        |                                                                                                                                                                                        |                       |
      |                        | You must specify this parameter if **TCP** or **UDP** is selected for **Protocol**.                                                                                                    |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description            | Supplementary information about the firewall rule. This parameter is optional.                                                                                                         | N/A                   |
      |                        |                                                                                                                                                                                        |                       |
      |                        | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                    |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.


   .. figure:: /_static/images/en-us_image_0000002492668909.png
      :alt: **Figure 2** Firewall rules

      **Figure 2** Firewall rules

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983162.png
