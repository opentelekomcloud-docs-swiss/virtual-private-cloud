:original_name: FlowLog_0006.html

.. _FlowLog_0006:

Enabling or Disabling VPC Flow Log
==================================

Scenarios
---------

After a VPC flow log is created, the VPC flow log is automatically enabled. If you do not need to record flow log data, you can disable the corresponding VPC flow log. A disabled VPC flow log can be enabled again.

Notes and Constraints
---------------------

-  After a VPC flow log is enabled, the system starts to collect flow logs in the next log collection period.
-  After a VPC flow log is disabled, the system stops collecting flow logs in the next log collection period. Generated flow logs will still be reported.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **VPC Flow Logs**.
5. Locate the VPC flow log to be enabled or disabled, and choose **More** > **Enable** or **More** > **Disable** in the **Operation** column.
6. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983174.png
