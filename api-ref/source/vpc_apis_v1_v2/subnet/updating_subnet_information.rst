:original_name: vpc_subnet01_0004.html

.. _vpc_subnet01_0004:

Updating Subnet Information
===========================

Function
--------

This API is used to update information about a subnet.

URI
---

PUT /v1/{project_id}/vpcs/{vpc_id}/subnets/{subnet_id}

:ref:`Table 1 <vpc_subnet01_0004__table27806533>` describes the parameters.

.. _vpc_subnet01_0004__table27806533:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | Yes                   | Specifies the VPC ID of the subnet.                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | subnet_id             | Yes                   | Specifies the subnet ID that uniquely identifies the subnet.                                                              |
   |                       |                       |                                                                                                                           |
   |                       |                       | If you use the management console, the value of this parameter is the **Network ID** value.                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +-----------+-----------+---------------------------------------------------------+-------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                    | Description                                                             |
   +===========+===========+=========================================================+=========================================================================+
   | subnet    | Yes       | :ref:`subnet <vpc_subnet01_0004__table45027976>` object | Specifies the :ref:`subnet objects <vpc_subnet01_0004__table45027976>`. |
   +-----------+-----------+---------------------------------------------------------+-------------------------------------------------------------------------+

.. _vpc_subnet01_0004__table45027976:

.. table:: **Table 3** **subnet** objects

   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                          | Description                                                                                                                                                                                                                                         |
   +=================+=================+===============================================================================+=====================================================================================================================================================================================================================================================+
   | name            | Yes             | String                                                                        | -  Specifies the subnet name.                                                                                                                                                                                                                       |
   |                 |                 |                                                                               | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                                              |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String                                                                        | -  Provides supplementary information about the subnet.                                                                                                                                                                                             |
   |                 |                 |                                                                               | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                    |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ipv6_enable     | No              | Boolean                                                                       | -  Specifies whether IPv6 is enabled.                                                                                                                                                                                                               |
   |                 |                 |                                                                               | -  The value can be **true** (enabled) or **false** (disabled).                                                                                                                                                                                     |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dhcp_enable     | No              | Boolean                                                                       | -  Specifies whether DHCP is enabled for the subnet.                                                                                                                                                                                                |
   |                 |                 |                                                                               | -  The value can be **true** (enabled) or **false** (disabled).                                                                                                                                                                                     |
   |                 |                 |                                                                               | -  If this parameter is left blank, the system automatically sets it to **true** by default. If this parameter is set to **false**, newly created ECSs cannot obtain IP addresses, and usernames and passwords cannot be injected using Cloud-init. |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | primary_dns     | No              | String                                                                        | -  Specifies the primary IP address of DNS server on the subnet.                                                                                                                                                                                    |
   |                 |                 |                                                                               | -  The value must be a valid IP address.                                                                                                                                                                                                            |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secondary_dns   | No              | String                                                                        | -  Specifies the standby IP address of DNS server on the subnet.                                                                                                                                                                                    |
   |                 |                 |                                                                               |                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                               | -  The value must be a valid IP address.                                                                                                                                                                                                            |
   |                 |                 |                                                                               |                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                               |    The value of **secondary_dns** must be different from that of **primary_dns**.                                                                                                                                                                   |
   |                 |                 |                                                                               |                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                               |    If there is only one DNS server address, only **primary_dns** is displayed.                                                                                                                                                                      |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dnsList         | No              | Array of strings                                                              | -  Specifies the DNS server address list of a subnet. This field is required if you need to use more than two DNS servers.                                                                                                                          |
   |                 |                 |                                                                               | -  This parameter value is the superset of both DNS server address 1 and DNS server address 2.                                                                                                                                                      |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extra_dhcp_opts | No              | Array of :ref:`extra_dhcp_opt <vpc_subnet01_0004__table019517383270>` objects | Specifies the NTP server address or DHCP lease time configured for the subnet. For details, see :ref:`Table 4 <vpc_subnet01_0004__table019517383270>`.                                                                                              |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_subnet01_0004__table019517383270:

.. table:: **Table 4** **extra_dhcp_opt** object

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | opt_value       | No              | String          | -  Specifies the NTP server address domain name, or DHCP lease expiration time configured for the subnet.                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 | -  Constraints:                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |    If **opt_name** is set to **ntp**, the value indicates the NTP server configured for the subnet. Currently, only IPv4 addresses are supported. A maximum of four IP addresses can be configured, and each address must be unique. Multiple IP addresses must be separated using commas (,). If **opt_name** is set to **null**, the value indicates that no NTP server is configured for the subnet. The parameter value cannot be an empty string. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |    If **opt_name** is set to **domainname**, the value is the domain name configured for DNS and is used to obtain the IP address from the DNS server. A domain name can contain only letters, digits, and hyphens (-) and cannot start or end with a hyphen (-). Each domain name contains at least two labels separated by periods (.). Max total: 254 characters. Max label: 63 characters.                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |    The option **addresstime** for **opt_name** indicates the DHCP lease expiration time of the IPv4 subnet. The value can be **-1**, which indicates unlimited lease time, or *Number*\ **h**. The number ranges from **1** to **175200**. For example, the value can be **5h**. The default value is **87600h**.                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |    The option **ipv6_addresstime** for **opt_name** indicates the DHCP lease expiration time of the IPv6 subnet. The value can be **-1**, which indicates unlimited lease time, or *Number*\ **h**. The number ranges from **1** to **175200**. For example, the value can be **5h**. The default value is **2h**.                                                                                                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | opt_name        | Yes             | String          | -  Specifies the NTP server address or DHCP lease expiration time configured for the subnet.                                                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  Currently, the value can be **ntp**, **domainname**, **addresstime**, or **ipv6_addresstime**.                                                                                                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Change the name of the subnet whose ID is 4779ab1c-7c1a-44b1-a02e-93dfc361b32d to **subnet02**, and also change its DNS and DHCP configurations.

   .. code-block:: text

      PUT https://{Endpoint}/v1/{project_id}/vpcs/{vpc_id}/subnets/4779ab1c-7c1a-44b1-a02e-93dfc361b32d

      {
          "subnet": {
              "name": "subnet02",
              "ipv6_enable": true,
              "dhcp_enable": false,
              "primary_dns": "114.xx.xx.115",
              "secondary_dns": "114.xx.xx.116",
              "extra_dhcp_opts": [
                  {
                      "opt_value": "10.100.0.33,10.100.0.34",
                      "opt_name": "ntp"
                  }
          }
      }

Response Parameters
-------------------

.. table:: **Table 5** Response parameter

   +-----------+--------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                   | Description                       |
   +===========+========================================================+===================================+
   | subnet    | :ref:`subnet <vpc_subnet01_0004__table1210700>` object | Specifies the **subnet** objects. |
   +-----------+--------------------------------------------------------+-----------------------------------+

.. _vpc_subnet01_0004__table1210700:

.. table:: **Table 6** **subnet** objects

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | id                    | String                | Specifies a resource ID in UUID format.                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | status                | String                | -  Specifies the status of the subnet.                                           |
   |                       |                       | -  The value can be **ACTIVE**, **UNKNOWN**, or **ERROR**.                       |
   |                       |                       |                                                                                  |
   |                       |                       |    -  **ACTIVE**: indicates that the subnet has been associated with a VPC.      |
   |                       |                       |    -  **UNKNOWN**: indicates that the subnet has not been associated with a VPC. |
   |                       |                       |    -  **ERROR**: indicates that the subnet is abnormal.                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "subnet": {
           "id": "4779ab1c-7c1a-44b1-a02e-93dfc361b32d",
           "status": "ACTIVE"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
