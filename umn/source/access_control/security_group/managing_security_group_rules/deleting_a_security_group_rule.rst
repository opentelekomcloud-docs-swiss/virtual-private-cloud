:original_name: vpc_SecurityGroup_0006.html

.. _vpc_SecurityGroup_0006:

Deleting a Security Group Rule
==============================

Scenarios
---------

If your security group rule is no longer required, you can delete it.

Notes and Constraints
---------------------

Security group rules use whitelists. Deleting a security group rule may result in ECS access failures.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

5. In the security group list, click the name of the security group.

   The security group details page is displayed.

6. Click the **Inbound Rules** or **Outbound Rules** tab as required.

   The security group rule list is displayed.

7. In the security group rule list:

   -  To delete a single security group rule, locate the row that contains the rule and click **Delete** in the **Operation** column.
   -  To delete multiple security group rules, select multiple security group rules and click **Delete** in the upper left corner of the rule list.

8. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582633.png
