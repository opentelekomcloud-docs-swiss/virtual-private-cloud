:original_name: vpc010017.html

.. _vpc010017:

Viewing Traces
==============

Scenarios
---------

After CTS is enabled, it starts recording operations on cloud resources. You can view the operation records of the last seven days on the CTS console.

This section describes how to query or export the operation records of the last seven days on the CTS console.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. In the upper left corner of the page, click |image2| to go to the service list. Under **Management & Deployment**, click **Cloud Trace Service**.

#. In the navigation pane on the left, choose **Trace List**.

#. Specify filters as needed. The following filters are available:


   .. figure:: /_static/images/en-us_image_0000002239303682.png
      :alt: **Figure 1** Filters

      **Figure 1** Filters

   -  **Trace Type**: Set it to **Management** or **Data**.

   -  **Trace Source**, **Resource Type**, and **Search By**

      Select filters from the drop-down list.

      If you select **Trace name** for **Search By**, select a trace name.

      If you select **Resource ID** for **Search By**, select or enter a resource ID.

      If you select **Resource name** for **Search By**, select or enter a resource name.

   -  **Operator**: Select a specific operator (a user other than an account).

   -  **Trace Status**: Select **All trace statuses**, **Normal**, **Warning**, or **Incident**.

   -  Search time range: In the upper right corner, choose **Last 1 hour**, **Last 1 day**, or **Last 1 week**, or specify a custom time range.

#. Click arrow on the left of the required trace to expand its details.

#. Locate the required trace and click **View Trace** in the **Operation** column.

   A dialog box is displayed, showing the trace content.

.. |image1| image:: /_static/images/en-us_image_0000001865663149.png
.. |image2| image:: /_static/images/en-us_image_0000001865582949.png
