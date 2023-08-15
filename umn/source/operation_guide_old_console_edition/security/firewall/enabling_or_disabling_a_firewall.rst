:original_name: vpc_acl02_0013.html

.. _vpc_acl02_0013:

Enabling or Disabling a Firewall
================================

Scenarios
---------

After a firewall is created, you may need to enable it based on network security requirements. You can also disable an enabled firewall if need. Before enabling a firewall, ensure that subnets have been associated with the firewall and that inbound and outbound rules have been added to the firewall.

When a firewall is disabled, custom rules will become invalid while default rules still take effect. Disabling a firewall may interrupt network traffic. For information about the default firewall rules, see :ref:`Default Firewall Rules <vpc_acl02_0001__en-us_topic_0144643910_section99541345213>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.
3. On the console homepage, under , click **Virtual Private Cloud**.
4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.
5. Locate the row that contains the firewall in the right pane, click **More** in the **Operation** column, and click **Enable** or **Disable**.
6. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
