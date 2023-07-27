:original_name: vpc_apiv3_0029.html

.. _vpc_apiv3_0029:

Creating a Supplementary Network Interface
==========================================

Function
--------

This API is used to create a supplementary network interface.

URI
---

POST /v3/{project_id}/vpc/sub-network-interfaces

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

   +-----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                                                                           | Description                                                                                                                                                                                                                                                                              |
   +=======================+=================+================================================================================================================================+==========================================================================================================================================================================================================================================================================================+
   | dry_run               | No              | Boolean                                                                                                                        | Whether to only check the request.                                                                                                                                                                                                                                                       |
   |                       |                 |                                                                                                                                |                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                                                                | The value can be:                                                                                                                                                                                                                                                                        |
   |                       |                 |                                                                                                                                |                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                                                                | -  **true**: A check request will be sent and no supplementary network interface will be created. Check items include mandatory parameters, request format, and constraints. If the check fails, the system returns an error. If the check succeeds, response code 202 will be returned. |
   |                       |                 |                                                                                                                                | -  **false** (default value): A request will be sent and a supplementary network interface will be created.                                                                                                                                                                              |
   +-----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sub_network_interface | Yes             | :ref:`CreateSubNetworkInterfaceOption <vpc_apiv3_0029__en-us_topic_0267488915_request_createsubnetworkinterfaceoption>` object | Request body for creating a supplementary network interface                                                                                                                                                                                                                              |
   +-----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0029__en-us_topic_0267488915_request_createsubnetworkinterfaceoption:

.. table:: **Table 4** CreateSubNetworkInterfaceOption

   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type             | Description                                                                                                            |
   +====================+=================+==================+========================================================================================================================+
   | virsubnet_id       | Yes             | String           | Virtual subnet ID                                                                                                      |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value must be in standard UUID format.                                                                             |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | vlan_id            | No              | String           | VLAN ID of the supplementary network interface                                                                         |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value can be from 1 to 4094.                                                                                       |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | Each supplementary network interface of an elastic network interface has a unique VLAN ID.                             |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | parent_id          | Yes             | String           | ID of the elastic network interface                                                                                    |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value must be in standard UUID format.                                                                             |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value must be an existing port ID.                                                                                 |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | description        | No              | String           | Description of the supplementary network interface                                                                     |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                          |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | ipv6_enable        | No              | Boolean          | Whether to enable IPv6 for the supplementary network interface.                                                        |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value can be:                                                                                                      |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | -  **true**: Enable                                                                                                    |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | -  **false**: Disable                                                                                                  |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  |    The default value is **false**.                                                                                     |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | private_ip_address | No              | String           | Private IPv4 address of the supplementary network interface                                                            |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value must be within the virtual subnet. If this parameter is left blank, an IP address will be randomly assigned. |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | ipv6_ip_address    | No              | String           | IPv6 address of the supplementary network interface                                                                    |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | If this parameter is left blank, an IP address will be randomly assigned.                                              |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | security_groups    | No              | Array of strings | Security group IDs                                                                                                     |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | Example: "security_groups": ["a0608cbf-d047-4f54-8b28-cd7b59853fff"]                                                   |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The default value is the default security group.                                                                       |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+
   | project_id         | No              | String           | Project ID of the supplementary network interface                                                                      |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | The value must be in standard UUID format.                                                                             |
   |                    |                 |                  |                                                                                                                        |
   |                    |                 |                  | Only administrators have permissions to specify project IDs.                                                           |
   +--------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

When the status code is **201**, the response parameters are as follows:

.. table:: **Table 5** Response body parameters

   +-----------------------+---------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter             | Type                                                                                                    | Description                                        |
   +=======================+=========================================================================================================+====================================================+
   | request_id            | String                                                                                                  | Request ID                                         |
   +-----------------------+---------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | sub_network_interface | :ref:`SubNetworkInterface <vpc_apiv3_0029__en-us_topic_0267488915_response_subnetworkinterface>` object | Response body of a supplementary network interface |
   +-----------------------+---------------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _vpc_apiv3_0029__en-us_topic_0267488915_response_subnetworkinterface:

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

When the status code is **409**, the response parameters are as follows:

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

Create a supplementary network interface. Set its virtual subnet ID to 08278e6c-61ca-46c1-9fc3-0d4f6c12f193, elastic network interface ID to 637748df-2986-4350-8303-95d259580fb3, and associated security group to 6727c950-9f01-47a2-a7aa-7d3686c4c95b.

.. code-block:: text

   POST https://{Endpoint}/v3/8c6fb137a48a428aaf9a0229dca4edb3/vpc/sub-network-interfaces

   {
     "sub_network_interface" : {
       "virsubnet_id" : "08278e6c-61ca-46c1-9fc3-0d4f6c12f193",
       "parent_id" : "637748df-2986-4350-8303-95d259580fb3",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ]
     }
   }

Example Response
----------------

When the status code is **201**, the response parameters are as follows:

Created

.. code-block::

   {
     "sub_network_interface" : {
       "id" : "2be868f2-f7c9-48db-abc0-eea0b9105b0d",
       "project_id" : "8c6fb137a48a428aaf9a0229dca4edb3",
       "virsubnet_id" : "08278e6c-61ca-46c1-9fc3-0d4f6c12f193",
       "private_ip_address" : "10.0.0.225",
       "ipv6_ip_address" : null,
       "mac_address" : "fa:16:3e:48:f8:6f",
       "parent_device_id" : "1ab01f1d-4ef7-4d83-82be-802b3aca0223",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ],
       "vpc_id" : "63b97e6b-3598-430f-9eb8-1caf06937be8",
       "description" : null,
       "parent_id" : "637748df-2986-4350-8303-95d259580fb3",
       "vlan_id" : 2787,
       "tags" : [ ],
       "created_at" : "2020-05-19T01:16:25"
     },
     "request_id" : "ceb6273e-1ec9-4168-ac11-3dfeaacfc889"
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

When the status code is **409**, the response parameters are as follows:

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
409         Conflict
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
