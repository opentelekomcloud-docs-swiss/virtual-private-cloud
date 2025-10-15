:original_name: FlowLog_0005.html

.. _FlowLog_0005:

Deleting a VPC Flow Log
=======================

Scenarios
---------

Delete a VPC flow log that is not required. Deleting a VPC flow log will not delete the existing flow log records in LTS.

.. note::

   If a network interface that uses a VPC flow log is deleted, the flow log will be automatically deleted. However, the flow log records are not deleted.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **VPC Flow Logs**.
5. Locate the row that contains the VPC flow log to be deleted and click **Delete** in the **Operation** column.
6. Click **OK** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582989.png
