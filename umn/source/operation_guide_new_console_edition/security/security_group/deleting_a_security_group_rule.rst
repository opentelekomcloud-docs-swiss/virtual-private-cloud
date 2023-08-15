:original_name: vpc_SecurityGroup_0006.html

.. _vpc_SecurityGroup_0006:

Deleting a Security Group Rule
==============================

Scenarios
---------

If the source of an inbound security group rule or destination of an outbound security group rule needs to be changed, you need to first delete the security group rule and add a new one.

Notes and Constraints
---------------------

Security group rules use whitelists. Deleting a security group rule may result in ECS access failures. Security group rules work as follows:

-  If an inbound request matches the source in an inbound security group rule with **Action** set to **Allow**, the request is allowed.
-  If the destination of an outbound security group rule with **Action** set to **Allow** is 0.0.0.0/0, all outbound requests are allowed.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.
3. On the console homepage, under , click **Virtual Private Cloud**.
4. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
5. On the **Security Groups** page, click the security group name.
6. If you do not need a security group rule, locate the row that contains the target rule, and click **Delete**.
7. Click **Yes** in the displayed dialog box.

**Deleting multiple security group rules at once**

You can also select multiple security group rules and click **Delete** above the security group rule list to delete multiple rules at a time.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
