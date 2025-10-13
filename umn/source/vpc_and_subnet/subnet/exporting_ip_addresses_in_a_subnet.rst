:original_name: vpc_vpc_0014.html

.. _vpc_vpc_0014:

Exporting IP Addresses in a Subnet
==================================

Scenarios
---------

You can export virtual and private IP addresses in a subnet as an Excel file to a local directory.

-  The exported virtual IP address file records the virtual IP addresses, EIPs, and server's network interfaces.
-  The exported private IP address file records the IPv4 addresses, IPv6 addresses, resource IDs, and usage information.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The **Subnets** page is displayed.

#. Locate the target subnet and click its name.

   The subnet details page is displayed.

#. Click the **IP Addresses** tab to export the IP addresses in the subnet.

   a. In the upper left corner of above the virtual IP address list, click **Export**.

      -  **Export selected data to an XLSX file**: Select one or more virtual IP addresses and export information about the selected virtual IP addresses.
      -  **Export all data to an XLSX file**: Export information about all the virtual IP addresses in the current subnet.

      The system will automatically export information about the virtual IP addresses as an Excel file to a local directory.

   b. In the upper left corner of above the private IP address list, click **Export**.

      -  **Export selected data to an XLSX file**: Select one or more private IP addresses and export information about the selected private IP addresses.
      -  **Export all data to an XLSX file**: Export information about all the private IP addresses in the current subnet.

      The system will automatically export information about the private IP addresses as an Excel file to a local directory.


   .. figure:: /_static/images/en-us_image_0000002063982285.png
      :alt: **Figure 1** Exporting virtual and private IP addresses

      **Figure 1** Exporting virtual and private IP addresses

.. |image1| image:: /_static/images/en-us_image_0000002027767176.png
.. |image2| image:: /_static/images/en-us_image_0000002027925628.png
