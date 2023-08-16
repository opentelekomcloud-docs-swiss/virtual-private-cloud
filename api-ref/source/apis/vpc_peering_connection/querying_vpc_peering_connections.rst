:original_name: vpc_peering_0001.html

.. _vpc_peering_0001:

Querying VPC Peering Connections
================================

Function
--------

This API is used to query all VPC peering connections accessible to the tenant submitting the request. The connections are filtered based on the filtering condition. For details about pagination query, see section :ref:`Pagination <vpc_version_0003>`.

URI
---

GET /v2.0/vpc/peerings

Example:

.. code-block:: text

   GET https://{Endpoint}/v2.0/vpc/peerings?id={id}&name={name}&status={status}&tenant_id={tenant_id}&vpc_id={vpc_id}&limit={limit}&marker={marker}

:ref:`Table 1 <vpc_peering_0001__table18880184689>` describes the parameters.

.. _vpc_peering_0001__table18880184689:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | id              | No              | String          | Specifies that the VPC peering connection ID is used as the filtering condition.                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | -  Specifies that the peering connection name is used as the filter.                                                                                                                                                   |
   |                 |                 |                 | -  The value can contain no more than 64 characters.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies that the VPC peering connection status is used as the filtering condition.                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies that the tenant ID is used as the filtering condition.                                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | Specifies that the VPC ID is used as the filtering condition.                                                                                                                                                          |
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
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The default value is **2000**.                                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/vpc/peerings

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+----------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                                                                                                                                                     |
   +=======================+============================================================================+=================================================================================================================================================================================================================+
   | peerings              | Array of :ref:`peering <vpc_peering_0001__table1026243410414>` objects     | Specifies the VPC peering connection object list. For details, see :ref:`Table 3 <vpc_peering_0001__table1026243410414>`.                                                                                       |
   +-----------------------+----------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | peerings_links        | Array of :ref:`peerings_link <vpc_peering_0001__table25150247450>` objects | Specifies the VPC peering connection object list. For details, see :ref:`Table 5 <vpc_peering_0001__table25150247450>`.                                                                                         |
   |                       |                                                                            |                                                                                                                                                                                                                 |
   |                       |                                                                            | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**. |
   +-----------------------+----------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0001__table1026243410414:

.. table:: **Table 3** **peering** objects

   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                                                          | Description                                                                                                        |
   +=======================+===============================================================+====================================================================================================================+
   | id                    | String                                                        | Specifies the VPC peering connection ID.                                                                           |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                        | Specifies the VPC peering connection name.                                                                         |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                        | Specifies the VPC peering connection status. Possible values are as follows:                                       |
   |                       |                                                               |                                                                                                                    |
   |                       |                                                               | -  **PENDING_ACCEPTANCE**                                                                                          |
   |                       |                                                               | -  **REJECTED**                                                                                                    |
   |                       |                                                               | -  **EXPIRED**                                                                                                     |
   |                       |                                                               | -  **DELETED**                                                                                                     |
   |                       |                                                               | -  **ACTIVE**                                                                                                      |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | request_vpc_info      | :ref:`vpc_info <vpc_peering_0001__table1132310347417>` object | Specifies information about the local VPC. For details, see :ref:`Table 4 <vpc_peering_0001__table1132310347417>`. |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | accept_vpc_info       | :ref:`vpc_info <vpc_peering_0001__table1132310347417>` object | Specifies information about the peer VPC. For details, see :ref:`Table 4 <vpc_peering_0001__table1132310347417>`.  |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                        | Provides supplementary information about the VPC peering connection.                                               |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                        | Specifies the time (UTC) when the VPC peering connection is created.                                               |
   |                       |                                                               |                                                                                                                    |
   |                       |                                                               | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                      |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                        | Specifies the time (UTC) when the VPC peering connection is updated.                                               |
   |                       |                                                               |                                                                                                                    |
   |                       |                                                               | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                      |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0001__table1132310347417:

.. table:: **Table 4** **vpc_info** objects

   +-----------+--------+------------------------------------------------------------------------------------------------+
   | Attribute | Type   | Description                                                                                    |
   +===========+========+================================================================================================+
   | vpc_id    | String | Specifies the ID of a VPC involved in a VPC peering connection.                                |
   +-----------+--------+------------------------------------------------------------------------------------------------+
   | tenant_id | String | Specifies the ID of the project to which a VPC involved in the VPC peering connection belongs. |
   +-----------+--------+------------------------------------------------------------------------------------------------+

.. _vpc_peering_0001__table25150247450:

.. table:: **Table 5** **peerings_link** object

   +------+--------+----------------------------------------------------------------------+
   | Name | Type   | Description                                                          |
   +======+========+======================================================================+
   | href | String | Specifies the API link.                                              |
   +------+--------+----------------------------------------------------------------------+
   | rel  | String | Specifies the relationship between the API link and the API version. |
   +------+--------+----------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "peerings": [
           {
               "request_vpc_info": {
                   "vpc_id": "9daeac7c-a98f-430f-8e38-67f9c044e299",
                   "tenant_id": "f65e9ebc-ed5d-418b-a931-9a723718ba4e"
               },
               "accept_vpc_info": {
                   "vpc_id": "f583c072-0bb8-4e19-afb2-afb7c1693be5",
                   "tenant_id": "f65e9ebc-ed5d-418b-a931-9a723718ba4e"
               },
               "name": "test",
               "id": "b147a74b-39bb-4c7a-aed5-19cac4c2df13",
               "status": "ACTIVE"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
