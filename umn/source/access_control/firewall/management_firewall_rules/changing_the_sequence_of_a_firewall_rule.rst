:original_name: vpc_acl_0004.html

.. _vpc_acl_0004:

Changing the Sequence of a Firewall Rule
========================================

Scenarios
---------

If you need a rule to take effect before or after a specific rule, you can insert that rule before or after the specific rule.

If multiple firewall rules conflict, only the rule with the highest priority takes effect.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. On the **Inbound Rules** or **Outbound Rules** tab, locate the target rule, click **More** in the **Operation** column, and select **Insert Rule Above** or **Insert Rule Below**.

7. In the displayed dialog box, configure required parameters and click **OK**.

   The rule is inserted. The procedure for inserting an outbound rule is the same as that for inserting an inbound rule.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582933.png
