:original_name: en-us_topic_0051746700.html

.. _en-us_topic_0051746700:

Associating Subnets with a Firewall
===================================

Scenarios
---------

You can associate a firewall with a subnet to protect resources in the subnet.

Notes and Constraints
---------------------

-  You can associate a firewall with multiple subnets. However, a subnet can only be associated with one firewall at a time.
-  After a firewall is associated with a subnet, the default firewall rules deny all traffic to and from the subnet until you add custom rules to allow traffic. For details, see :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. On the displayed page, click the **Associated Subnets** tab.

7. On the **Associated Subnets** tab, click **Associate**.

8. On the displayed page, select the subnets to be associated with the firewall, and click **OK**.

.. note::

   A subnet with a firewall associated will not be displayed on the page for you to select. If you want to associate such a subnet with another firewall, you must first disassociate the subnet from the original firewall. One-click subnet association and disassociation are not supported currently. A subnet can only be associated with one firewall.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823450.png
