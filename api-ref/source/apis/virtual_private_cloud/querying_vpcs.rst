:original_name: vpc_api01_0003.html

.. _vpc_api01_0003:

Querying VPCs
=============

Function
--------

This API is used to query VPCs using search criteria and to display the VPCs in a list.

URI
---

GET /v1/{project_id}/vpcs

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/vpcs?limit=10&marker=13551d6b-755d-4757-b956-536f674975c0

:ref:`Table 1 <vpc_api01_0003__table39337169>` describes the parameters.

.. _vpc_api01_0003__table39337169:

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

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/vpcs

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +------+--------------------------------------------------------------+---------------------+
   | Name | Type                                                         | Description         |
   +======+==============================================================+=====================+
   | vpcs | Array of :ref:`vpcs <vpc_api01_0003__table65129753>` objects | Specifies the VPCs. |
   +------+--------------------------------------------------------------+---------------------+

.. _vpc_api01_0003__table65129753:

.. table:: **Table 3** Description of the **vpcs** field

   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                                                               | Description                                                                                                                                                                           |
   +=======================+====================================================================+=======================================================================================================================================================================================+
   | id                    | String                                                             | Specifies a resource ID in UUID format.                                                                                                                                               |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                             | -  Specifies the VPC name.                                                                                                                                                            |
   |                       |                                                                    | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                        |
   |                       |                                                                    | -  Each VPC name of a tenant must be unique if the VPC name is not left blank.                                                                                                        |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                             | -  Provides supplementary information about the VPC.                                                                                                                                  |
   |                       |                                                                    | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                                      |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                             | -  Specifies the available IP address ranges for subnets in the VPC.                                                                                                                  |
   |                       |                                                                    | -  Possible values are as follows:                                                                                                                                                    |
   |                       |                                                                    |                                                                                                                                                                                       |
   |                       |                                                                    |    -  10.0.0.0/8-24                                                                                                                                                                   |
   |                       |                                                                    |    -  172.16.0.0/12-24                                                                                                                                                                |
   |                       |                                                                    |    -  192.168.0.0/16-24                                                                                                                                                               |
   |                       |                                                                    |                                                                                                                                                                                       |
   |                       |                                                                    | -  If **cidr** is not specified, the default value is left blank.                                                                                                                     |
   |                       |                                                                    | -  The value must be in CIDR format, for example, **192.168.0.0/16**.                                                                                                                 |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                             | -  Specifies the VPC status.                                                                                                                                                          |
   |                       |                                                                    | -  Possible values are as follows:                                                                                                                                                    |
   |                       |                                                                    |                                                                                                                                                                                       |
   |                       |                                                                    |    -  **CREATING**: The VPC is being created.                                                                                                                                         |
   |                       |                                                                    |    -  **OK**: The VPC is created successfully.                                                                                                                                        |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | routes                | Array of :ref:`route <vpc_api01_0003__table3576833291556>` objects | -  Specifies the route information.                                                                                                                                                   |
   |                       |                                                                    | -  For details, see :ref:`Table 4 <vpc_api01_0003__table3576833291556>`.                                                                                                              |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_shared_snat    | Boolean                                                            | Specifies whether the shared SNAT function is enabled. The value **true** indicates that the function is enabled, and the value **false** indicates that the function is not enabled. |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_api01_0003__table3576833291556:

.. table:: **Table 4** **route** objects

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                  | Description                                                                                                              |
   +=======================+=======================+==========================================================================================================================+
   | destination           | String                | -  Specifies the destination network segment of a route.                                                                 |
   |                       |                       | -  The value must be in the CIDR format. Currently, only the value **0.0.0.0/0** is supported.                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | nexthop               | String                | -  Specifies the next hop of a route.                                                                                    |
   |                       |                       | -  The value must be an IP address and must belong to the subnet in the VPC. Otherwise, this value does not take effect. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "vpcs": [
           {
               "id": "13551d6b-755d-4757-b956-536f674975c0",
               "name": "default",
               "description": "test",
               "cidr": "172.16.0.0/16",
               "status": "OK",
               "routes": [],
               "enable_shared_snat": false
           },
           {
               "id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
               "name": "222",
               "description": "test",
               "cidr": "192.168.0.0/16",
               "status": "OK",
               "routes": [],
               "enable_shared_snat": false
           },
           {
               "id": "99d9d709-8478-4b46-9f3f-2206b1023fd3",
               "name": "vpc",
               "description": "test",
               "cidr": "192.168.0.0/16",
               "status": "OK",
               "routes": [],
               "enable_shared_snat": false
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
