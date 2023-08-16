:original_name: vpc_route_0001.html

.. _vpc_route_0001:

Querying VPC Routes
===================

Function
--------

This API is used to query all routes of the tenant submitting the request. The routes are filtered based on the filtering condition. For details about the response format of pagination query, see section :ref:`Pagination <vpc_version_0003>`.

URI
---

GET /v2.0/vpc/routes

Example:

.. code-block::

   Example:
   GET https://{Endpoint}/v2.0/vpc/routes?id={id}&vpc_id={vpc_id}&tenant_id={tenant_id}&destination={destination}&type={type}&limit={limit}&marker={marker}

:ref:`Table 1 <vpc_route_0001__table1256815152114>` describes the parameters.

.. _vpc_route_0001__table1256815152114:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | id              | No              | String          | Specifies that the route ID is used as the filtering condition.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies that the tenant ID is used as the filtering condition.                                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | Specifies that the VPC ID is used as the filtering condition.                                                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | destination     | No              | String          | Specifies that the route destination address (CIDR) is used as the filtering condition.                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Specifies that the type is used as the filtering condition. Currently, the value can only be **peering**.                                                                                                              |
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

   GET https://{Endpoint}/v2.0/vpc/routes?vpc_id=ab78be2d-782f-42a5-aa72-35879f6890ff

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                   | Description                                                                                                                                                                                                          |
   +=======================+========================================================================+======================================================================================================================================================================================================================+
   | routes                | Array of :ref:`route <vpc_route_0001__table05001250111>` objects       | Specifies the route object list. For details, see :ref:`Table 3 <vpc_route_0001__table05001250111>`.                                                                                                                 |
   +-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | routes_links          | Array of :ref:`routes_link <vpc_route_0001__table25150247450>` objects | Specifies the route object list. For details, see :ref:`Table 4 <vpc_route_0001__table25150247450>`.                                                                                                                 |
   |                       |                                                                        |                                                                                                                                                                                                                      |
   |                       |                                                                        | The value of **rel** will be **next** and that of **href** will be a link only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**). |
   +-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_route_0001__table05001250111:

.. table:: **Table 3** **route** objects

   +-------------+--------+------------------------------------------------------------------------------------------------+
   | Attribute   | Type   | Description                                                                                    |
   +=============+========+================================================================================================+
   | id          | String | Specifies the route ID.                                                                        |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | destination | String | Specifies the destination address in the CIDR notation format, for example, 192.168.200.0/24.  |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | nexthop     | String | Specifies the next hop. If the route type is **peering**, enter the VPC peering connection ID. |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | type        | String | Specifies the route type. Currently, the value can only be **peering**.                        |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | vpc_id      | String | Specifies the VPC of the route. Set this parameter to the existing VPC ID.                     |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | tenant_id   | String | Specifies the project ID.                                                                      |
   +-------------+--------+------------------------------------------------------------------------------------------------+

.. _vpc_route_0001__table25150247450:

.. table:: **Table 4** **routes_link** object

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
     "routes": [
       {
         "type": "peering",
         "nexthop": "60c809cb-6731-45d0-ace8-3bf5626421a9",
         "destination": "192.168.200.0/24",
         "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
         "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
         "id": "3d42a0d4-a980-4613-ae76-a2cddecff054"
       }
     ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
