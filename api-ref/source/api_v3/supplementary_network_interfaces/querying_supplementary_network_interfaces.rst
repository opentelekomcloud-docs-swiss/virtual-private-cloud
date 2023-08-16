:original_name: vpc_apiv3_0031.html

.. _vpc_apiv3_0031:

Querying Supplementary Network Interfaces
=========================================

Function
--------

This API is used to query supplementary network interfaces. A maximum of 2000 records can be returned for each query.

URI
---

GET /v3/{project_id}/vpc/sub-network-interfaces

.. table:: **Table 1** Parameter description

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                              |
   +====================+=================+=================+==========================================================================================================================================+
   | description        | No              | ARRAY           | -  Description of the supplementary network interface. Multiple descriptions can be specified for filtering.                             |
   |                    |                 |                 | -  This parameter can be used to filter supplementary network interfaces.                                                                |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | id                 | No              | ARRAY           | -  ID of the supplementary network interface. Multiple IDs can be specified for filtering.                                               |
   |                    |                 |                 | -  This parameter can be used to filter supplementary network interfaces.                                                                |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | limit              | No              | Integer         | Number of records returned on each page                                                                                                  |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | mac_address        | No              | ARRAY           | -  MAC address of the supplementary network interface. Multiple MAC addresses can be specified for filtering.                            |
   |                    |                 |                 | -  This parameter can be used to precisely filter supplementary network interfaces.                                                      |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | marker             | No              | String          | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried.                     |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | parent_id          | No              | ARRAY           | -  ID of elastic network interface that the supplementary network interface is attached to. Multiple IDs can be specified for filtering. |
   |                    |                 |                 | -  This parameter can be used to filter supplementary network interfaces of one or more elastic network interfaces.                      |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | private_ip_address | No              | ARRAY           | -  Private IPv4 address of the supplementary network interface. Multiple private IPv4 addresses can be specified for filtering.          |
   |                    |                 |                 | -  This parameter can be used to filter supplementary network interfaces.                                                                |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | virsubnet_id       | No              | ARRAY           | -  Virtual subnet ID of the supplementary network interface. Multiple IDs can be specified for filtering.                                |
   |                    |                 |                 | -  This parameter can be used to filter supplementary network interfaces in one or more virtual subnets.                                 |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id             | No              | ARRAY           | -  VPC ID of the supplementary network interface. Multiple IDs can be specified for filtering.                                           |
   |                    |                 |                 | -  This field can be used to filter supplementary network interfaces in one or more VPCs.                                                |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ========= ========= ==== ===========
   Parameter Mandatory Type Description
   ========= ========= ==== ===========
   ========= ========= ==== ===========

Response Parameters
-------------------

When the status code is **200**, the response parameters are as follows:

.. table:: **Table 4** Response body parameters

   +------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter              | Type                                                                                                              | Description                                   |
   +========================+===================================================================================================================+===============================================+
   | request_id             | String                                                                                                            | -  Request ID                                 |
   |                        |                                                                                                                   | -  The value must be in standard UUID format. |
   |                        |                                                                                                                   | -  Constraints: N/A                           |
   |                        |                                                                                                                   | -  Default value: N/A                         |
   |                        |                                                                                                                   | -  Permissions: N/A                           |
   +------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | sub_network_interfaces | Array of :ref:`SubNetworkInterface <vpc_apiv3_0031__en-us_topic_0267488923_response_subnetworkinterface>` objects | -  Supplementary network interfaces           |
   |                        |                                                                                                                   | -  Value range: N/A                           |
   |                        |                                                                                                                   | -  Constraints: N/A                           |
   |                        |                                                                                                                   | -  Default value: N/A                         |
   |                        |                                                                                                                   | -  Permissions: N/A                           |
   +------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | page_info              | :ref:`PageInfo <vpc_apiv3_0031__en-us_topic_0267488923_response_pageinfo>` object                                 | Pagination information                        |
   +------------------------+-------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _vpc_apiv3_0031__en-us_topic_0267488923_response_subnetworkinterface:

.. table:: **Table 5** SubNetworkInterface

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | id                    | String                | -  Unique identifier of the supplementary network interface                                                               |
   |                       |                       | -  The value is in UUID format with hyphens (-).                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | virsubnet_id          | String                | -  Virtual subnet ID                                                                                                      |
   |                       |                       | -  The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | private_ip_address    | String                | -  Private IPv4 address of the supplementary network interface                                                            |
   |                       |                       | -  The value must be within the virtual subnet. If this parameter is left blank, an IP address will be randomly assigned. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | ipv6_ip_address       | String                | IPv6 address of the supplementary network interface                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | mac_address           | String                | -  MAC address of the supplementary network interface                                                                     |
   |                       |                       | -  The value is a valid MAC address assigned by the system randomly.                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | parent_device_id      | String                | -  Device ID                                                                                                              |
   |                       |                       | -  The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | parent_id             | String                | -  ID of the elastic network interface                                                                                    |
   |                       |                       | -  The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | -  Description of the supplementary network interface                                                                     |
   |                       |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                | -  VPC ID of the supplementary network interface                                                                          |
   |                       |                       | -  The value must be in standard UUID format.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | vlan_id               | Integer               | -  VLAN ID of the supplementary network interface                                                                         |
   |                       |                       | -  The value can be from 1 to 4094.                                                                                       |
   |                       |                       | -  Each supplementary network interface of an elastic network interface has a unique VLAN ID.                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | security_groups       | Array of strings      | -  Security group IDs, for example, "security_groups": ["a0608cbf-d047-4f54-8b28-cd7b59853fff"]                           |
   |                       |                       | -  The default value is the default security group.                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of strings      | Tags of the supplementary network interface                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Project ID of the supplementary network interface                                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | -  Creation time of the supplementary network interface                                                                   |
   |                       |                       | -  The value is a UTC time in the format of yyyy-MM-ddTHH:mmss.                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0031__en-us_topic_0267488923_response_pageinfo:

.. table:: **Table 6** PageInfo

   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                 |
   +=================+=========+=============================================================================================+
   | previous_marker | String  | First record on the current page                                                            |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | current_count   | Integer | Total number of records on the current page                                                 |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | next_marker     | String  | Last record on the current page. This parameter does not exist if the page is the last one. |
   +-----------------+---------+---------------------------------------------------------------------------------------------+

Example Request
---------------

List all supplementary network interfaces.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/sub-network-interfaces?vpc_id=63b97e6b-3598-430f-9eb8-1caf06937be8

Example Response
----------------

When the status code is **200**, the response parameters are as follows:

OK

.. code-block::

   {
     "request_id" : "e4cb9e3a-7b99-41c9-afd8-1630fe313299",
     "sub_network_interfaces" : [ {
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
     }, {
       "id" : "55761e2d-8f72-42c0-9874-98e9885bf0fe",
       "project_id" : "8c6fb137a48a428aaf9a0229dca4edb3",
       "virsubnet_id" : "08278e6c-61ca-46c1-9fc3-0d4f6c12f193",
       "private_ip_address" : "10.0.3.55",
       "ipv6_ip_address" : null,
       "mac_address" : "fa:16:3e:c2:2c:ba",
       "parent_device_id" : "1ab01f1d-4ef7-4d83-82be-802b3aca0223",
       "security_groups" : [ "6727c950-9f01-47a2-a7aa-7d3686c4c95b" ],
       "vpc_id" : "63b97e6b-3598-430f-9eb8-1caf06937be8",
       "description" : null,
       "parent_id" : "637748df-2986-4350-8303-95d259580fb3",
       "vlan_id" : 799,
       "tags" : [ ],
       "created_at" : "2020-05-19T01:16:31"
     } ],
     "page_info" : {
       "next_marker" : "55761e2d-8f72-42c0-9874-98e9885bf0fe",
       "previous_marker" : "2be868f2-f7c9-48db-abc0-eea0b9105b0d",
       "current_count" : 2
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
