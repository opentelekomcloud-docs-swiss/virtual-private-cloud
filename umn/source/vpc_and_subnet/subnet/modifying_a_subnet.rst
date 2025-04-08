:original_name: vpc_vpc_0001.html

.. _vpc_vpc_0001:

Modifying a Subnet
==================

Scenarios
---------

Modify the subnet name, NTP server address, and DNS server address.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, click **Subnets**.

   The **Subnets** page is displayed.

5. In the subnet list, locate the target subnet and click its name.

   The subnet details page is displayed.

6. On the **Summary** tab, click |image3| on the right of the parameter to be modified and modify the parameter as prompted.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Example Value         |
      +=======================+============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Name                  | The subnet name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Subnet                |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | The name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                                                                                                                                                                                                                                                                                                      |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | DNS Server Address    | By default, two DNS server addresses are configured. You can change them as required. A maximum of two DNS server addresses are supported. Use commas (,) to separate every two addresses.                                                                                                                                                                                                                                                                                                 | 100.125.x.x           |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | For more information about private DNS servers, see `What Are the Private DNS Servers Provided by the DNS Service? <https://docs.sc.otc.t-systems.com/en-us/usermanual/dns/dns_faq_002.html>`__                                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | NTP Server Address    | The IP address of the NTP server. This parameter is optional.                                                                                                                                                                                                                                                                                                                                                                                                                              | 192.168.2.1           |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | You can configure the NTP server IP addresses to be added to the subnet as required. The IP addresses are added in addition to the default NTP server addresses. If you do not specify this parameter, no additional NTP server IP addresses will be added.                                                                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | A maximum of four unique NTP server IP addresses can be configured. Multiple IP addresses must be separated by a comma (,). If you add or change the NTP server addresses of a subnet, you need to renew the DHCP lease for or restart all the ECSs in the subnet to make the change take effect immediately. If the NTP server addresses have been cleared out, restarting the ECSs will not help. You must renew the DHCP lease for all ECSs to make the change take effect immediately. |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823766.png
.. |image3| image:: /_static/images/en-us_image_0000001865583301.png
