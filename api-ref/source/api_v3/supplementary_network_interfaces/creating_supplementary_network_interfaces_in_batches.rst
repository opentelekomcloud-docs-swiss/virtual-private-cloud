:original_name: vpc_apiv3_0030.html

.. _vpc_apiv3_0030:

Creating Supplementary Network Interfaces in Batches
====================================================

Function
--------

This API is used to create supplementary network interfaces in batches.

URI
---

POST /v3/{project_id}/vpc/sub-network-interfaces/batch-create

.. table:: **Table 1** Parameter description

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token. For details about how to obtain the token, see "**Obtaining the User Token**" in the *Identity and Access Management API Reference*. |
   |                 |                 |                 |                                                                                                                                                  |
   |                 |                 |                 | The token is the value **X-Subject-Token** in the response message header.                                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                                                                                     | Description                                                                                                                                                                                                                                                                              |
   +=======================+=================+==========================================================================================================================================+==========================================================================================================================================================================================================================================================================================+
   | dry_run               | No              | Boolean                                                                                                                                  | Whether to only check the request.                                                                                                                                                                                                                                                       |
   |                       |                 |                                                                                                                                          |                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                                                                          | The value can be:                                                                                                                                                                                                                                                                        |
   |                       |                 |                                                                                                                                          |                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                                                                          | -  **true**: A check request will be sent and no supplementary network interface will be created. Check items include mandatory parameters, request format, and constraints. If the check fails, the system returns an error. If the check succeeds, response code 202 will be returned. |
   |                       |                 |                                                                                                                                          | -  **false** (default value): A request will be sent and a supplementary network interface will be created.                                                                                                                                                                              |
   +-----------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sub_network_interface | Yes             | :ref:`BatchCreateSubNetworkInterfaceOption <vpc_apiv3_0030__en-us_topic_0267488947_request_batchcreatesubnetworkinterfaceoption>` object | Request body for creating a supplementary network interface                                                                                                                                                                                                                              |
   +-----------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | count                 | Yes             | Integer                                                                                                                                  | Number of supplementary network interfaces to be created in batches                                                                                                                                                                                                                      |
   |                       |                 |                                                                                                                                          |                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                                                                          | Minimum value: **1**                                                                                                                                                                                                                                                                     |
   |                       |                 |                                                                                                                                          |                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                                                                          | Maximum value: **20**                                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0030__en-us_topic_0267488947_request_batchcreatesubnetworkinterfaceoption:

.. table:: **Table 4** BatchCreateSubNetworkInterfaceOption

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                   |
   +=================+=================+==================+===============================================================================================+
   | virsubnet_id    | Yes             | String           | Virtual subnet ID                                                                             |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The value must be in standard UUID format.                                                    |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | parent_id       | Yes             | String           | ID of the elastic network interface                                                           |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The value must be in standard UUID format.                                                    |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The value must be an existing port ID.                                                        |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | security_groups | No              | Array of strings | Security group IDs Example: "security_groups": ["a0608cbf-d047-4f54-8b28-cd7b59853fff"]       |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The default value is the default security group.                                              |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | description     | No              | String           | Description of the supplementary network interface                                            |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The value can contain no more than 255 characters and cannot contain angle brackets (< or >). |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | ipv6_enable     | No              | Boolean          | Whether to enable IPv6 for the supplementary network interface                                |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The value can be:                                                                             |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | -  **true**: Enable                                                                           |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | -  **false**: Disable                                                                         |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  |    The default value is **false**.                                                            |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+
   | project_id      | No              | String           | Project ID of the supplementary network interface                                             |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | The value must be in standard UUID format.                                                    |
   |                 |                 |                  |                                                                                               |
   |                 |                 |                  | Only administrators have permissions to specify project IDs.                                  |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------+

Response Parameters
-------------------

When the status code is **201**, the response parameters are as follows:

.. table:: **Table 5** Response body parameters

   +------------------------+-------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter              | Type                                                                                                              | Description                                                            |
   +========================+===================================================================================================================+========================================================================+
   | request_id             | String                                                                                                            | Request ID                                                             |
   +------------------------+-------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | sub_network_interfaces | Array of :ref:`SubNetworkInterface <vpc_apiv3_0030__en-us_topic_0267488947_response_subnetworkinterface>` objects | Response body for creating supplementary network interfaces in batches |
   +------------------------+-------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _vpc_apiv3_0030__en-us_topic_0267488947_response_subnetworkinterface:

.. table:: **Table 6** SubNetworkInterface

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                            |
   +=======================+=======================+========================================================================================================================+
   | id                    | String                | Unique identifier of the supplementary network interface                                                               |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value is in UUID format with hyphens (-).                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | virsubnet_id          | String                | Virtual subnet ID                                                                                                      |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | private_ip_address    | String                | Private IPv4 address of the supplementary network interface                                                            |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value must be within the virtual subnet. If this parameter is left blank, an IP address will be randomly assigned. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | ipv6_ip_address       | String                | IPv6 address of the supplementary network interface                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | mac_address           | String                | MAC address of the supplementary network interface                                                                     |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value is a valid MAC address assigned by the system randomly.                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | parent_device_id      | String                | Device ID                                                                                                              |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | parent_id             | String                | ID of the elastic network interface                                                                                    |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Description of the supplementary network interface                                                                     |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                | VPC ID of the supplementary network interface                                                                          |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | vlan_id               | Integer               | VLAN ID of the supplementary network interface                                                                         |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value can be from 1 to 4094.                                                                                       |
   |                       |                       |                                                                                                                        |
   |                       |                       | Each supplementary network interface of an elastic network interface has a unique VLAN ID.                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | security_groups       | Array of strings      | Security group IDs Example: "security_groups": ["a0608cbf-d047-4f54-8b28-cd7b59853fff"]                                |
   |                       |                       |                                                                                                                        |
   |                       |                       | The default value is the default security group.                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of strings      | Tags of the supplementary network interface                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Project ID of the supplementary network interface                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | Creation time of the supplementary network interface                                                                   |
   |                       |                       |                                                                                                                        |
   |                       |                       | The value is a UTC time in the format of yyyy-MM-ddTHH:mmss.                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------+

When the status code is **400**, the response parameters are as follows:

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **401**, the response parameters are as follows:

.. table:: **Table 8** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **403**, the response parameters are as follows:

.. table:: **Table 9** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **404**, the response parameters are as follows:

.. table:: **Table 10** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **500**, the response parameters are as follows:

.. table:: **Table 11** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

Example Request
---------------

Create three supplementary network interfaces in batches. Set the virtual subnet ID to 115b5a84-31dc-4b1e-8de9-bf5a75d2c566, elastic network interface ID to 8b6c46f1-c68d-4bba-a922-2d97da185af5, and associated security group to 6727c950-9f01-47a2-a7aa-7d3686c4c95b.

.. code-block:: text

   POST https://{Endpoint}/v3/8c6fb137a48a428aaf9a0229dca4edb3/vpc/sub-network-interfaces/batch-create

   {
     "sub_network_interface" : {
       "virsubnet_id" : "115b5a84-31dc-4b1e-8de9-bf5a75d2c566",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ],
       "parent_id" : "8b6c46f1-c68d-4bba-a922-2d97da185af5"
     },
     "count" : 3
   }

Example Response
----------------

When the status code is **201**, the response parameters are as follows:

Created

.. code-block::

   {
     "sub_network_interfaces" : [ {
       "id" : "d1f8094c-bb3d-43c5-b625-52dd43eab451",
       "project_id" : "8c6fb137a48a428aaf9a0229dca4edb3",
       "virsubnet_id" : "115b5a84-31dc-4b1e-8de9-bf5a75d2c566",
       "private_ip_address" : "192.168.6.245",
       "ipv6_ip_address" : "2001:db8:a583:5d:11e8:b908:4fe6:9802",
       "mac_address" : "fa:16:3e:97:1f:f5",
       "parent_device_id" : "11185aa2-4e08-4d9e-87ed-84817280eaa7",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ],
       "vpc_id" : null,
       "description" : "",
       "parent_id" : "8b6c46f1-c68d-4bba-a922-2d97da185af5",
       "vlan_id" : 41,
       "tags" : [ ]
     }, {
       "id" : "0dce57ab-00de-443b-a7fe-e8ff68bd95bc",
       "project_id" : "8c6fb137a48a428aaf9a0229dca4edb3",
       "virsubnet_id" : "115b5a84-31dc-4b1e-8de9-bf5a75d2c566",
       "private_ip_address" : "192.168.6.75",
       "ipv6_ip_address" : "2001:db8:a583:5d:6c22:8ea2:c061:a802",
       "mac_address" : "fa:16:3e:5a:61:84",
       "parent_device_id" : "11185aa2-4e08-4d9e-87ed-84817280eaa7",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ],
       "vpc_id" : null,
       "description" : "",
       "parent_id" : "8b6c46f1-c68d-4bba-a922-2d97da185af5",
       "vlan_id" : 42,
       "tags" : [ ]
     }, {
       "id" : "1eca03ee-c0f1-4434-9c4c-87fe4426718c",
       "project_id" : "8c6fb137a48a428aaf9a0229dca4edb3",
       "virsubnet_id" : "115b5a84-31dc-4b1e-8de9-bf5a75d2c566",
       "private_ip_address" : "192.168.6.194",
       "ipv6_ip_address" : "2001:db8:a583:5d:2b45:a3ae:17db:ec02",
       "mac_address" : "fa:16:3e:b8:ec:6d",
       "parent_device_id" : "11185aa2-4e08-4d9e-87ed-84817280eaa7",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ],
       "vpc_id" : null,
       "description" : "",
       "parent_id" : "8b6c46f1-c68d-4bba-a922-2d97da185af5",
       "vlan_id" : 43,
       "tags" : [ ]
     } ],
     "request_id" : "344544c1-d053-4ad3-b673-900a0e01db7e"
   }

When the status code is **400**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **401**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **403**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **404**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **500**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
201         Created
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
