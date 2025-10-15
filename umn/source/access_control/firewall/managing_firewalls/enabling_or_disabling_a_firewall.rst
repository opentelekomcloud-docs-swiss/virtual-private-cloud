:original_name: vpc_acl_0011.html

.. _vpc_acl_0011:

Enabling or Disabling a Firewall
================================

Scenarios
---------

After a firewall is created, you may need to enable it based on network security requirements. You can also disable an enabled firewall if needed. Before enabling a firewall, ensure that subnets have been associated with the firewall and that inbound and outbound rules have been added to the firewall.

When a firewall is disabled, custom rules will become invalid while default rules still take effect. Disabling a firewall may interrupt network traffic. For information about the default firewall rules, see :ref:`Default Firewall Rules <acl_0001__section99541345213>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the row that contains the firewall, click **More** in the **Operation** column, and click **Enable** or **Disable**.

6. Click **OK** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823714.png
