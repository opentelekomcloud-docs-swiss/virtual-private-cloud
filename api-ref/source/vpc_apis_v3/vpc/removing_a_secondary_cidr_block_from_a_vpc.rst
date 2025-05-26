:original_name: vpc_apiv3_0008.html

.. _vpc_apiv3_0008:

Removing a Secondary CIDR Block from a VPC
==========================================

Function
--------

This API is used to remove a secondary CIDR block from a VPC.

URI
---

PUT /v3/{project_id}/vpc/vpcs/{vpc_id}/remove-extend-cidr

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   vpc_id     Yes       String VPC ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                  | Description                                                                                                                                                                                                                                                                                  |
   +=================+=================+=======================================================================================+==============================================================================================================================================================================================================================================================================================+
   | dry_run         | No              | Boolean                                                                               | -  Whether to only send the check request.                                                                                                                                                                                                                                                   |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                              |
   |                 |                 |                                                                                       | -  The value can be:                                                                                                                                                                                                                                                                         |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                              |
   |                 |                 |                                                                                       |    -  **true**: Only the check request will be sent and the secondary CIDR block will not be removed. Check items include mandatory parameters, request format, and constraints. If the check fails, the system returns an error. If the check succeeds, response code 202 will be returned. |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                              |
   |                 |                 |                                                                                       |    -  **false** (default value): A request will be sent and a secondary CIDR block will be removed.                                                                                                                                                                                          |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc             | Yes             | :ref:`RemoveExtendCidrOption <vpc_apiv3_0008__request_removeextendcidroption>` object | Request body for removing a secondary CIDR block.                                                                                                                                                                                                                                            |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0008__request_removeextendcidroption:

.. table:: **Table 3** RemoveExtendCidrOption

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                            |
   +=================+=================+==================+========================================================================================+
   | extend_cidrs    | Yes             | Array of strings | -  Secondary CIDR blocks to be removed.                                                |
   |                 |                 |                  |                                                                                        |
   |                 |                 |                  | -  The secondary CIDR block should be an existing one in the VPC.                      |
   |                 |                 |                  |                                                                                        |
   |                 |                 |                  | -  Before removing a secondary CIDR block, delete the subnets in the CIDR block first. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------+--------------------------------------------------+---------------------------------------------------+
   | Parameter  | Type                                             | Description                                       |
   +============+==================================================+===================================================+
   | request_id | String                                           | Request ID.                                       |
   +------------+--------------------------------------------------+---------------------------------------------------+
   | vpc        | :ref:`Vpc <vpc_apiv3_0008__response_vpc>` object | Response body of removing a secondary CIDR block. |
   +------------+--------------------------------------------------+---------------------------------------------------+

.. _vpc_apiv3_0008__response_vpc:

.. table:: **Table 5** Vpc

   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                           | Description                                                                                                                                                           |
   +=======================+================================================================================+=======================================================================================================================================================================+
   | id                    | String                                                                         | -  VPC ID, which uniquely identifies the VPC.                                                                                                                         |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value is in UUID format with hyphens (-).                                                                                                                      |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                         | -  VPC name.                                                                                                                                                          |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The name can contain up to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                         | -  Supplementary information about the VPC.                                                                                                                           |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                                                             |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                                         | -  Available VPC CIDR blocks.                                                                                                                                         |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value can be:                                                                                                                                                  |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                |    -  10.0.0.0/8-10.255.255.240/28                                                                                                                                    |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                |    -  172.16.0.0/12-172.31.255.240/28                                                                                                                                 |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                |    -  192.168.0.0/16-192.168.255.240/28                                                                                                                               |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                |    -  If **cidr** is not specified, the default value is **""**.                                                                                                      |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value must be in IPv4 CIDR format, for example, **192.168.0.0/16**.                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extend_cidrs          | Array of strings                                                               | -  Secondary CIDR blocks of a VPC.                                                                                                                                    |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  Currently, only IPv4 CIDR blocks are supported.                                                                                                                    |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                         | -  VPC status.                                                                                                                                                        |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value can be:                                                                                                                                                  |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                |    -  **PENDING**: The VPC is being created.                                                                                                                          |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                |    -  **ACTIVE**: The VPC is created successfully.                                                                                                                    |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                         | -  ID of the project to which the VPC belongs.                                                                                                                        |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                         | -  ID of the enterprise project to which the VPC belongs.                                                                                                             |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value can be **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                         | Time when the VPC was created.                                                                                                                                        |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                                      |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                         | -  Time when the VPC was updated.                                                                                                                                     |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloud_resources       | Array of :ref:`CloudResource <vpc_apiv3_0008__response_cloudresource>` objects | -  Type and number of resources associated with the VPC.                                                                                                              |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  Currently, only route tables and subnets of the VPC are returned. The number of **virsubnets** is the total number of IPv4 and IPv6 subnets.                       |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`Tag <vpc_apiv3_0008__response_tag>` objects                     | -  VPC tags. For details, see the tag objects.                                                                                                                        |
   |                       |                                                                                |                                                                                                                                                                       |
   |                       |                                                                                | -  Value range: 0 to 20 tag key-value pairs.                                                                                                                          |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0008__response_cloudresource:

.. table:: **Table 6** CloudResource

   +-----------------------+-----------------------+-------------------------+
   | Parameter             | Type                  | Description             |
   +=======================+=======================+=========================+
   | resource_type         | String                | -  Resource type.       |
   +-----------------------+-----------------------+-------------------------+
   | resource_count        | Integer               | -  Number of resources. |
   +-----------------------+-----------------------+-------------------------+

.. _vpc_apiv3_0008__response_tag:

.. table:: **Table 7** Tag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | key                   | String                | -  Tag key.                                                                      |
   |                       |                       |                                                                                  |
   |                       |                       | -  Value ranges:                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key can contain up to 36 Unicode characters and cannot be left blank. |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key value of a resource must be unique.                               |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscores (_) ,at signs (@), and hyphens (-)      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | value                 | String                | -  Tag value.                                                                    |
   |                       |                       |                                                                                  |
   |                       |                       | -  Value range:                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each value can contain up to 43 Unicode characters and can be left blank.  |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscore (_), at signs (@), and hyphen (-)        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+

**Status code: 202**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   request_id String Request ID.
   error_msg  String Error message.
   error_code String Error code.
   ========== ====== ==============

Example Requests
----------------

Remove the secondary CIDR block **23.8.0.0/16** from the VPC whose ID is **99d9d709-8478-4b46-9f3f-2206b1023fd3**.

.. code-block:: text

   PUT https://{Endpoint}/v3/{project_id}/vpc/vpcs/99d9d709-8478-4b46-9f3f-2206b1023fd3/remove-extend-cidr

   {
     "vpc" : {
       "extend_cidrs" : [ "23.8.0.0/16" ]
     }
   }

Example Responses
-----------------

**Status code: 200**

Normal response to the PUT operation. For more status codes, see :ref:`Status Code <vpc_api_0002>`.

.. code-block::

   {
     "request_id" : "84eb4f775d66dd916db121768ec55626",
     "vpc" : {
       "id" : "0552091e-b83a-49dd-88a7-4a5c86fd9ec3",
       "name" : "vpc1",
       "description" : "test1",
       "cidr" : "192.168.0.0/16",
       "extend_cidrs" : [ ],
       "enterprise_project_id" : "0",
       "tags" : [ {
         "key" : "key",
         "value" : "value"
       } ],
       "cloud_resources" : [ {
         "resource_type" : "routetable",
         "resource_count" : 1
       } ],
       "status" : "ACTIVE",
       "project_id" : "060576782980d5762f9ec014dd2f1148",
       "created_at" : "2018-03-23T09:26:08",
       "updated_at" : "2018-08-24T08:49:53"
     }
   }

**Status code: 202**

Normal response to the specified preflight request of API V3. For more status codes, see :ref:`Status Code <vpc_api_0002>`.

.. code-block::

   {
     "error_msg" : "Request validation has been passed with dry run...",
     "error_code" : "SYS.0202",
     "request_id" : "cfd81aea3f59eac7128dba4b36d516c8"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                 |
+=============+=============================================================================================================================+
| 200         | Normal response to the PUT operation. For more status codes, see :ref:`Status Code <vpc_api_0002>`.                         |
+-------------+-----------------------------------------------------------------------------------------------------------------------------+
| 202         | Normal response to the specified preflight request of API V3. For more status codes, see :ref:`Status Code <vpc_api_0002>`. |
+-------------+-----------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
