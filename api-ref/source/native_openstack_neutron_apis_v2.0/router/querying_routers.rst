:original_name: vpc_router_0001.html

.. _vpc_router_0001:

Querying Routers
================

Function
--------

This API is used to query all routers accessible to the tenant submitting the request.

URI
---

GET /v2.0/routers

Example:

.. code-block:: text

   GET https://{Endpoint}/v2.0/routers?id={id}&name={name}&admin_state_up={admin_state_up}&tenant_id={tenant_id}&status={status}

Example of querying routers by page

.. code-block:: text

   GET https://{Endpoint}/v2.0/routers?limit=2&marker=01ab4be1-4447-45fb-94be-3ee787ed4ebe&page_reverse=False

:ref:`Table 1 <vpc_router_0001__table966161441716>` describes the parameters.

.. _vpc_router_0001__table966161441716:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | id              | No              | String          | Specifies that the router ID is used as the filtering condition.                                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up  | No              | Boolean         | Specifies that the admin state is used as the filtering condition.                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The value can be **true** or **false**.                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies that the router status is used as the filtering condition.                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The value can be **ACTIVE**, **DOWN**, or **ERROE**.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies that the project ID is used as the filtering condition.                                                                                                                                                      |
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

   GET https://{Endpoint}/v2.0/routers?limit=1

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                     | Description                                                                                                                                                                                                     |
   +=======================+==========================================================================+=================================================================================================================================================================================================================+
   | routers               | Array of :ref:`router <vpc_router_0001__table24153696181443>` objects    | Specifies the router list. For details, see :ref:`Table 3 <vpc_router_0001__table24153696181443>`.                                                                                                              |
   +-----------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | routers_links         | Array of :ref:`routers_link <vpc_router_0001__table25150247450>` objects | Specifies the pagination information. For details, see :ref:`Table 5 <vpc_router_0001__table25150247450>`.                                                                                                      |
   |                       |                                                                          |                                                                                                                                                                                                                 |
   |                       |                                                                          | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**. |
   +-----------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0001__table24153696181443:

.. table:: **Table 3** **router** objects

   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                                                                       | Description                                                                                                               |
   +=======================+============================================================================+===========================================================================================================================+
   | id                    | String                                                                     | Specifies the router ID.                                                                                                  |
   |                       |                                                                            |                                                                                                                           |
   |                       |                                                                            | This parameter is not mandatory when you query routers.                                                                   |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                     | Specifies the router name.                                                                                                |
   |                       |                                                                            |                                                                                                                           |
   |                       |                                                                            | The name can contain only letters, digits, underscores (_), hyphens (-), and periods (.).                                 |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | Boolean                                                                    | Specifies the administrative status.                                                                                      |
   |                       |                                                                            |                                                                                                                           |
   |                       |                                                                            | The value can only be **true**.                                                                                           |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                     | Specifies the router status. The value can be **ACTIVE**, **DOWN**, or **ERROR**.                                         |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                     | Specifies the project ID.                                                                                                 |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | external_gateway_info | :ref:`external_gateway_info <vpc_router_0001__table11448068181443>` object | Specifies the external gateway. This is an extended attribute. For details, see the **external_gateway_info** objects.    |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                     | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                     | Specifies the time (UTC) when the router is created.                                                                      |
   |                       |                                                                            |                                                                                                                           |
   |                       |                                                                            | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                             |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                     | Specifies the time (UTC) when the router is updated.                                                                      |
   |                       |                                                                            |                                                                                                                           |
   |                       |                                                                            | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                             |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0001__table11448068181443:

.. table:: **Table 4** **external_gateway_info** objects

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================+
   | network_id            | String                | Specifies the UUID of the external network.                                                                                                               |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | You can use **GET /v2.0/networks?router:external=True** or run the **neutron net-external-list** command to query information about the external network. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_snat           | Boolean               | Specifies whether the SNAT function is enabled.                                                                                                           |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | The default value is **false**.                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0001__table25150247450:

.. table:: **Table 5** **routers_link** object

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
       "routers": [
           {
               "id": "01ab4be1-4447-45fb-94be-3ee787ed4ebe",
               "name": "xiaoleizi-tag",
               "status": "ACTIVE",
               "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
               "project_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
               "admin_state_up": true,
               "external_gateway_info": {
                   "network_id": "0a2228f2-7f8a-45f1-8e09-9039e1d09975",
                   "enable_snat": false
               },
               "routes": [
                   {
                       "destination": "0.0.0.0/0",
                       "nexthop": "172.16.0.124"
                   }
               ],
               "created_at": "2018-03-23T09:26:08",
               "updated_at": "2018-08-24T08:49:53"
           }
       ],
       "routers_links": [
          {
               "rel": "next",
               "href": "https://{Endpoint}/v2.0/routers?limit=1&marker=01ab4be1-4447-45fb-94be-3ee787ed4ebe"
           },
          {    "rel": "previous",
               "href": "https://{Endpoint}/v2.0/routers?limit=1&marker=01ab4be1-4447-45fb-94be-3ee787ed4ebe&page_reverse=True"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
