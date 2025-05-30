:original_name: vpc010005.html

.. _vpc010005:

Assigning a Shared Bandwidth
============================

Scenarios
---------

Assign a shared bandwidth for use with EIPs.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. Click |image2| in the upper left corner, and choose > **Elastic IP**.
#. In the navigation pane on the left, choose **Elastic IP and Bandwidth** > **Shared Bandwidths**.
#. In the upper right corner, click **Assign Shared Bandwidth**. On the displayed page, configure parameters as prompted.

   .. table:: **Table 1** Parameter descriptions

      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Parameter      | Description                                                                                                                                                                                                                                                                                             | Example Value |
      +================+=========================================================================================================================================================================================================================================================================================================+===============+
      | Region         | Regions are geographic areas that are physically isolated from each other. The networks inside different regions are not connected to each other, so resources cannot be shared across different regions. For lower network latency and faster access to your resources, select the region nearest you. | eu-ch2        |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Bandwidth      | The bandwidth size in Mbit/s. The minimum value is 5 Mbit/s. The maximum bandwidth can be 1000 Mbit/s.                                                                                                                                                                                                  | 10            |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Bandwidth Name | The name of the shared bandwidth.                                                                                                                                                                                                                                                                       | Bandwidth-001 |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+

#. Click **Create Now**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982822.png
