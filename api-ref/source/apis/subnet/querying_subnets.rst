:original_name: vpc_subnet01_0003.html

.. _vpc_subnet01_0003:

Querying Subnets
================

Function
--------

This API is used to query subnets using search criteria and to display the subnets in a list.

URI
---

GET /v1/{project_id}/subnets

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/subnets?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d&vpc_id=3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                         |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | Specifies that the VPC ID is used as the filtering condition.                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This field is mandatory in the fine-grained authorization scenario based on enterprise projects.                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/subnets

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +---------+-----------------------------------------------------------------------+------------------------+
   | Name    | Type                                                                  | Description            |
   +=========+=======================================================================+========================+
   | subnets | Array of :ref:`subnet <vpc_subnet01_0003__table946390317596>` objects | Specifies the subnets. |
   +---------+-----------------------------------------------------------------------+------------------------+

.. _vpc_subnet01_0003__table946390317596:

.. table:: **Table 3** **subnet** objects

   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                                                                          | Description                                                                                                                                            |
   +=======================+===============================================================================+========================================================================================================================================================+
   | id                    | String                                                                        | Specifies a resource ID in UUID format.                                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                        | -  Specifies the subnet name.                                                                                                                          |
   |                       |                                                                               | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                 |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                        | -  Provides supplementary information about the subnet.                                                                                                |
   |                       |                                                                               | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                       |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                                        | Specifies the subnet CIDR block.                                                                                                                       |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gateway_ip            | String                                                                        | Specifies the subnet gateway address.                                                                                                                  |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ipv6_enable           | Boolean                                                                       | Specifies whether an IPv6 subnet can be created.                                                                                                       |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr_v6               | String                                                                        | Specifies the IPv6 subnet CIDR block. If the subnet is an IPv4 subnet, this parameter is not returned.                                                 |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gateway_ip_v6         | String                                                                        | Specifies the IPv6 subnet gateway. If the subnet is an IPv4 subnet, this parameter is not returned.                                                    |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dhcp_enable           | Boolean                                                                       | Specifies whether the DHCP function is enabled for the subnet.                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | primary_dns           | String                                                                        | Specifies the IP address of DNS server 1 on the subnet.                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secondary_dns         | String                                                                        | Specifies the IP address of DNS server 2 on the subnet.                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dnsList               | Array of strings                                                              | Specifies the IP address list of DNS servers on the subnet.                                                                                            |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone     | String                                                                        | Identifies the AZ to which the subnet belongs.                                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                                                                        | Specifies the ID of the VPC to which the subnet belongs.                                                                                               |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                        | -  Specifies the status of the subnet.                                                                                                                 |
   |                       |                                                                               | -  The value can be **ACTIVE**, **UNKNOWN**, or **ERROR**.                                                                                             |
   |                       |                                                                               |                                                                                                                                                        |
   |                       |                                                                               |    -  **ACTIVE**: indicates that the subnet has been associated with a VPC.                                                                            |
   |                       |                                                                               |    -  **UNKNOWN**: indicates that the subnet has not been associated with a VPC.                                                                       |
   |                       |                                                                               |    -  **ERROR**: indicates that the subnet is abnormal.                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | neutron_network_id    | String                                                                        | Specifies the ID of the corresponding network (OpenStack Neutron API).                                                                                 |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | neutron_subnet_id     | String                                                                        | Specifies the ID of the corresponding subnet (OpenStack Neutron API).                                                                                  |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | neutron_subnet_id_v6  | String                                                                        | Specifies the ID of the IPv6 subnet (OpenStack Neutron API). If the subnet is an IPv4 subnet, this parameter is not returned.                          |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extra_dhcp_opts       | Array of :ref:`extra_dhcp_opt <vpc_subnet01_0003__table019517383270>` objects | Specifies the NTP server address or DHCP lease time configured for the subnet. For details, see :ref:`Table 4 <vpc_subnet01_0003__table019517383270>`. |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scope                 | String                                                                        | Specifies where the subnet is used.                                                                                                                    |
   |                       |                                                                               |                                                                                                                                                        |
   |                       |                                                                               | Values:                                                                                                                                                |
   |                       |                                                                               |                                                                                                                                                        |
   |                       |                                                                               | -  **center**: The subnet is used in a central AZ.                                                                                                     |
   |                       |                                                                               | -  *{azId}*: The subnet is used in an edge AZ.                                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_subnet01_0003__table019517383270:

.. table:: **Table 4** **extra_dhcp_opt** object

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | opt_value       | No              | String          | -  Specifies the NTP server address or DHCP lease expiration time configured for the subnet.                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Constraints:                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |    The option **ntp** for **opt_name** indicates the NTP server configured for the subnet. Currently, only IPv4 addresses are supported. A maximum of four IP addresses can be configured, and each address must be unique. Multiple IP addresses must be separated using commas (,). The option **null** for **opt_name** indicates that no NTP server is configured for the subnet. The parameter value cannot be an empty string. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |    The option **addresstime** for **opt_name** indicates the DHCP lease expiration time. The value can be **-1**, which indicates unlimited lease time, or *Number*\ **+h**. The number ranges from 1 to 30,000. For example, the value can be **5h**. The default value is **24h**.                                                                                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | opt_name        | Yes             | String          | -  Specifies the NTP server address name or DHCP lease expiration time configured for the subnet.                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | -  Currently, the value can only be set to **ntp** or **addresstime**.                                                                                                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "subnets": [
           {
               "id": "4779ab1c-7c1a-44b1-a02e-93dfc361b32d",
               "name": "subnet",
               "description": "",
               "cidr": "192.168.20.0/24",
               "dnsList": [
                   "114.xx.xx.114",
                   "114.xx.xx.115"
               ],
               "status": "ACTIVE",
               "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
               "gateway_ip": "192.168.20.1",
               "ipv6_enable": true,
               "cidr_v6": "2001:db8:a583::/64",
               "gateway_ip_v6": "2001:db8:a583::1",
               "dhcp_enable": true,
               "primary_dns": "114.xx.xx.114",
               "secondary_dns": "114.xx.xx.115",
               "availability_zone": "aa-bb-cc",
               "neutron_network_id": "4779ab1c-7c1a-44b1-a02e-93dfc361b32d",
               "neutron_subnet_id": "213cb9d-3122-2ac1-1a29-91ffc1231a12",
               "neutron_subnet_id_v6": "e0fa7de1-a6e2-44c9-b052-b9d8cebe93c4",
               "extra_dhcp_opts": [
                 {
                   "opt_value": "10.100.0.33,10.100.0.34",
                   "opt_name": "ntp"
                 }
              ]
           },
           {
               "id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "name": "Subnet1",
               "description": "",
               "cidr": "192.168.1.0/24",
               "dnsList": [
                   "114.xx.xx.114",
                   "114.xx.xx.115"
               ],
               "status": "ACTIVE",
               "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
               "gateway_ip": "192.168.1.1",
               "ipv6_enable": false,
               "dhcp_enable": true,
               "primary_dns": "114.xx.xx.114",
               "secondary_dns": "114.xx.xx.115",
               "availability_zone": "aa-bb-cc",
               "neutron_network_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "neutron_subnet_id": "1aac193-a2ad-f153-d122-12d64c2c1d78",
               "extra_dhcp_opts": [
                 {
                   "opt_value": "10.100.0.33,10.100.0.34",
                   "opt_name": "ntp"
                 }
              ],
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
