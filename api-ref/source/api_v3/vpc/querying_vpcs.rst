:original_name: vpc_apiv3_0003.html

.. _vpc_apiv3_0003:

Querying VPCs
=============

Function
--------

This API is used to query VPCs.

Constraints
-----------

This API is used to query all VPCs accessible to the tenant submitting the request. A maximum of 2000 records can be returned for each query. If the number of records exceeds 2000, the pagination marker will be returned.

URI
---

GET /v3/{project_id}/vpc/vpcs

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                       |
   +=================+=================+=================+===================================================================================================+
   | project_id      | Yes             | String          | Project ID.                                                                                       |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                          |
   +=================+=================+==================+======================================================================================================================+
   | limit           | No              | Integer          | Number of records displayed on each page.                                                                            |
   |                 |                 |                  |                                                                                                                      |
   |                 |                 |                  | Value range: 0 to 2000                                                                                               |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String           | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | id              | No              | Array of strings | VPC ID, which can be used to filter VPCs.                                                                            |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | name            | No              | Array of strings | VPC name, which can be used to filter VPCs.                                                                          |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | description     | No              | Array of strings | Supplementary information about the VPC, which can be used to filter VPCs.                                           |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | cidr            | No              | Array of strings | VPC CIDR block, which can be used to filter VPCs.                                                                    |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------+

Request Parameter
-----------------

None

Example Request
---------------

-  Querying VPCs

   .. code-block::

      "GET https://{Endpoint}/v3/{project_id}/vpc/vpcs"

-  Querying VPCs by VPC ID

   .. code-block::

      "GET https://{Endpoint}/v3/{project_id}/vpc/vpcs?id=01ab4be1-4447-45fb-94be-3ee787ed4ebe&id=02cd5ef2-4447-36fb-75be-3ee787ed6adf"

-  Querying VPCs by VPC name

   .. code-block::

      "GET https://{Endpoint}/v3/{project_id}/vpc/vpcs?name=vpc-test"

-  Querying VPCs by page

   .. code-block::

      "GET https://{Endpoint}/v3/{project_id}/vpc/vpcs?limit=2&marker=01ab4be1-4447-45fb-94be-3ee787ed4ebe"

Response Parameter
------------------

.. table:: **Table 3** Response body parameters

   +------------+-----------------------------------------------------------------------------------+------------------------+
   | Parameter  | Type                                                                              | Description            |
   +============+===================================================================================+========================+
   | request_id | String                                                                            | Request ID             |
   +------------+-----------------------------------------------------------------------------------+------------------------+
   | vpcs       | Array of :ref:`Vpc <vpc_apiv3_0003__en-us_topic_0267488966_response_vpc>` objects | Response body of VPCs  |
   +------------+-----------------------------------------------------------------------------------+------------------------+
   | page_info  | :ref:`PageInfo <vpc_apiv3_0003__en-us_topic_0267488966_response_pageinfo>` object | Pagination information |
   +------------+-----------------------------------------------------------------------------------+------------------------+

.. _vpc_apiv3_0003__en-us_topic_0267488966_response_vpc:

.. table:: **Table 4** Vpc

   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                  | Description                                                                                                                                                    |
   +=======================+=======================================================================================================+================================================================================================================================================================+
   | id                    | String                                                                                                | VPC ID, which uniquely identifies the VPC                                                                                                                      |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | The value is in UUID format with hyphens (-).                                                                                                                  |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                                | VPC name                                                                                                                                                       |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                    |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                                | Provides supplementary information about the VPC.                                                                                                              |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                  |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                                                                | Available VPC CIDR blocks                                                                                                                                      |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | Value range:                                                                                                                                                   |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | -  10.0.0.0/8-10.255.255.240/28                                                                                                                                |
   |                       |                                                                                                       | -  172.16.0.0/12-172.31.255.240/28                                                                                                                             |
   |                       |                                                                                                       | -  192.168.0.0/16-192.168.255.240/28                                                                                                                           |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | If **cidr** is not specified, the default value is **""**.                                                                                                     |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | -  The value must be in IPv4 CIDR format, for example, **192.168.0.0/16**.                                                                                     |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extend_cidrs          | Array of strings                                                                                      | Secondary CIDR blocks of VPCs                                                                                                                                  |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | Value range:                                                                                                                                                   |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | Currently, only IPv4 CIDR blocks are supported.                                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                                | VPC status                                                                                                                                                     |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | Value range:                                                                                                                                                   |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | -  **PENDING**: The VPC is being created.                                                                                                                      |
   |                       |                                                                                                       | -  **ACTIVE**: The VPC is created successfully.                                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                                                | ID of the project to which the VPC belongs                                                                                                                     |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                                                | ID of the enterprise project that the VPC belongs to                                                                                                           |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                                                | Time when the VPC is created                                                                                                                                   |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | UTC time in the format of yyyy-MM-ddTHH:mmss                                                                                                                   |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                                                | Time when the VPC is updated                                                                                                                                   |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | UTC time in the format of yyyy-MM-ddTHH:mm:ss                                                                                                                  |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloud_resources       | Array of :ref:`CloudResource <vpc_apiv3_0003__en-us_topic_0267488966_response_cloudresource>` objects | Type and number of resources associated with the VPC                                                                                                           |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | Currently, only route tables and subnets of the VPC are returned. The number of **virsubnets** is the total number of IPv4 and IPv6 subnets.                   |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`Tag <vpc_apiv3_0003__en-us_topic_0267488966_response_tag>` objects                     | VPC tags. For details, see the tag objects.                                                                                                                    |
   |                       |                                                                                                       |                                                                                                                                                                |
   |                       |                                                                                                       | Value range: 0 to 10 tag key-value pairs                                                                                                                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0003__en-us_topic_0267488966_response_cloudresource:

.. table:: **Table 5** CloudResource

   ============== ======= ===================
   Parameter      Type    Description
   ============== ======= ===================
   resource_type  String  Resource type
   resource_count Integer Number of resources
   ============== ======= ===================

.. _vpc_apiv3_0003__en-us_topic_0267488966_response_tag:

.. table:: **Table 6** Tag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================+
   | key                   | String                | Tag key                                                                                                                                      |
   |                       |                       |                                                                                                                                              |
   |                       |                       | Value range:                                                                                                                                 |
   |                       |                       |                                                                                                                                              |
   |                       |                       | -  A tag key contains a maximum of 36 Unicode characters.                                                                                    |
   |                       |                       | -  A tag key cannot be left blank. It cannot contain non-printable ASCII characters (0-31) or the following special characters: ``*,<,>,,=`` |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Tag value                                                                                                                                    |
   |                       |                       |                                                                                                                                              |
   |                       |                       | Value range:                                                                                                                                 |
   |                       |                       |                                                                                                                                              |
   |                       |                       | -  A tag value contains a maximum of 43 Unicode characters and can be left blank.                                                            |
   |                       |                       | -  A tag value cannot contain non-printable ASCII characters (0-31) or the following special characters: ``*,<,>,,=``                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0003__en-us_topic_0267488966_response_pageinfo:

.. table:: **Table 7** PageInfo

   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                 |
   +=================+=========+=============================================================================================+
   | previous_marker | String  | First record on the current page                                                            |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | current_count   | Integer | Total number of records on the current page                                                 |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | next_marker     | String  | Last record on the current page. This parameter does not exist if the page is the last one. |
   +-----------------+---------+---------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "request_id": "9c1838ba498249547be43dd618b58d27",
       "vpcs": [
           {
               "id": "01da5a65-0bb9-4638-8ab7-74c64e24a9a7",
               "name": "API-PERF-TEST-14bd44c121",
               "description": "",
               "cidr": "192.168.0.0/16",
               "extend_cidrs": [ ],
               "status": "ACTIVE",
               "project_id": "087679f0aa80d32a2f4ec0172f5e902b",
               "enterprise_project_id": "0",
               "tags": [ ],
               "created_at": "2020-06-16T02:32:18Z",
               "updated_at": "2020-06-16T02:32:18Z",
               "cloud_resources": [
                   {
                       "resource_type": "routetable",
                       "resource_count": 1
                   },
                   {
                       "resource_type": "virsubnet",
                       "resource_count": 0
                   }
               ]
           },
           {
               "id": "43fd79b0-f7d7-4e9b-828b-2d4d7bfae428",
               "name": "API-PERF-TEST_m2n33",
               "description": "",
               "cidr": "192.168.0.0/16",
               "extend_cidrs": [ ],
               "status": "ACTIVE",
               "project_id": "087679f0aa80d32a2f4ec0172f5e902b",
               "enterprise_project_id": "0",
               "tags": [ ],
               "created_at": "2020-06-15T06:29:40Z",
               "updated_at": "2020-06-15T06:29:41Z",
               "cloud_resources": [
                   {
                       "resource_type": "routetable",
                       "resource_count": 1
                   },
                   {
                       "resource_type": "virsubnet",
                       "resource_count": 1
                   }
               ]
           },
           {
               "id": "5ed053ba-b46c-4dce-a1ae-e9d8a7015f21",
               "name": "API-PERF-TEST-c34b1c4b12",
               "description": "",
               "cidr": "192.168.0.0/16",
               "extend_cidrs": [ ],
               "status": "ACTIVE",
               "project_id": "087679f0aa80d32a2f4ec0172f5e902b",
               "enterprise_project_id": "0",
               "tags": [ ],
               "created_at": "2020-06-16T02:32:33Z",
               "updated_at": "2020-06-16T02:32:33Z",
               "cloud_resources": [
                   {
                       "resource_type": "routetable",
                       "resource_count": 1
                   },
                   {
                       "resource_type": "virsubnet",
                       "resource_count": 0
                   }
               ]
           }
       ],
       "page_info": {
           "previous_marker": "01da5a65-0bb9-4638-8ab7-74c64e24a9a7",
           "current_count": 3
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
