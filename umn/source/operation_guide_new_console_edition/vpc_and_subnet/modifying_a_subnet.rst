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

3. On the console homepage, under , click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **Virtual Private Cloud**.

5. Locate the row that contains the target VPC and click the number in the **Subnets** column.

   The **Subnets** page is displayed.

6. In the subnet list, locate the target subnet and click its name.

   The subnet details page is displayed.

7. On the **Summary** tab, click |image2| on the right of the parameter to be modified and modify the parameter as prompted.

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
      |                       | You can configure the NTP server IP addresses to be added to the subnet as required. The IP addresses are added in addition to the default NTP server addresses. If this parameter is left empty, you do not add an NTP server IP address.                                                                                                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | A maximum of four unique NTP server IP addresses can be configured. Multiple IP addresses must be separated by a comma (,). If you add or change the NTP server addresses of a subnet, you need to renew the DHCP lease for or restart all the ECSs in the subnet to make the change take effect immediately. If the NTP server addresses have been cleared out, restarting the ECSs will not help. You must renew the DHCP lease for all ECSs to make the change take effect immediately. |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

8. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001337710801.png
