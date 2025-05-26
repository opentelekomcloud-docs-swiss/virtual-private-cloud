:original_name: vpc_firewall_0013.html

.. _vpc_firewall_0013:

Querying Firewall Groups
========================

Function
--------

This API is used to query all firewall groups accessible to the tenant submitting the request.

URI
---

GET /v2.0/fwaas/firewall_groups

Example of querying groups by page

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_groups?limit=2&marker=cd600d47-0045-483f-87a1-5041ae2f513b&page_reverse=False

:ref:`Table 1 <vpc_firewall_0013__table2285151162120>` describes the parameters.

.. _vpc_firewall_0013__table2285151162120:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================+
   | id              | No              | String          | Specifies that the ID of the firewall group is used as the filtering condition.                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Specifies that the name of the firewall group is used as the filtering condition.                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Specifies that the description of the firewall group is used as the filtering condition.                                                                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up  | No              | Boolean         | Specifies that the admin state of the firewall group is used as the filtering condition.                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | The value can be **true** or **false**.                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies that the project ID of the firewall group is used as the filtering condition.                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                                     |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                                |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                                |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, 11th to 2,000th resource records will be returned. The default value of **limit** is **2000**. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_groups

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                               | Description                                                                                                                                                                                                     |
   +=======================+====================================================================================+=================================================================================================================================================================================================================+
   | firewall_groups       | Array of :ref:`Firewall Group <vpc_firewall_0013__table31629250121127>` objects    | Specifies the firewall group list. For details, see :ref:`Table 3 <vpc_firewall_0013__table31629250121127>`.                                                                                                    |
   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | firewall_groups_links | Array of :ref:`firewall_groups_link <vpc_firewall_0013__table25150247450>` objects | Specifies the **firewall_groups_link** object list. For details, see :ref:`Table 4 <vpc_firewall_0013__table25150247450>`.                                                                                      |
   |                       |                                                                                    |                                                                                                                                                                                                                 |
   |                       |                                                                                    | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**. |
   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0013__table31629250121127:

.. table:: **Table 3** **Firewall Group** objects

   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Attribute                  | Type                  | Description                                                                                                               |
   +============================+=======================+===========================================================================================================================+
   | id                         | String                | Specifies the UUID of the firewall group.                                                                                 |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | name                       | String                | Specifies the name of the firewall group.                                                                                 |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | description                | String                | Provides supplementary information about the firewall group.                                                              |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | tenant_id                  | String                | Specifies the project ID.                                                                                                 |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | ingress_firewall_policy_id | String                | Specifies the firewall policy for inbound traffic.                                                                        |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | egress_firewall_policy_id  | String                | Specifies the firewall policy for outbound traffic.                                                                       |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | ports                      | Array of strings      | Specifies the list of ports bound with the firewall group.                                                                |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | public                     | Boolean               | Specifies whether the firewall group can be shared by different tenants.                                                  |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | status                     | String                | Specifies the status of a firewall group.                                                                                 |
   |                            |                       |                                                                                                                           |
   |                            |                       | The value can be:                                                                                                         |
   |                            |                       |                                                                                                                           |
   |                            |                       | -  **ACTIVE** (Normal)                                                                                                    |
   |                            |                       | -  **INACTIVE** (Inactive)                                                                                                |
   |                            |                       | -  **ERROR** (Error occurred)                                                                                             |
   |                            |                       | -  **PENDING_CREATE** (Creating)                                                                                          |
   |                            |                       | -  **PENDING_UPDATE** (Updating)                                                                                          |
   |                            |                       | -  **PENDING_DELETE** (Deleting)                                                                                          |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up             | Boolean               | Specifies the administrative status of the firewall.                                                                      |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id                 | String                | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | created_at                 | String                | Specifies the time (UTC) when the resource is created.                                                                    |
   |                            |                       |                                                                                                                           |
   |                            |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                             |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | updated_at                 | String                | Specifies the time (UTC) when the resource is updated.                                                                    |
   |                            |                       |                                                                                                                           |
   |                            |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                             |
   +----------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0013__table25150247450:

.. table:: **Table 4** **firewall_groups_link** object

   +-----------+--------+----------------------------------------------------------------------+
   | Parameter | Type   | Description                                                          |
   +===========+========+======================================================================+
   | href      | String | Specifies the API link.                                              |
   +-----------+--------+----------------------------------------------------------------------+
   | rel       | String | Specifies the relationship between the API link and the API version. |
   +-----------+--------+----------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "firewall_groups": [
           {
               "status": "INACTIVE",
               "public": false,
               "egress_firewall_policy_id": null,
               "name": "",
               "admin_state_up": true,
               "ports": [ ],
               "tenant_id": "23c8a121505047b6869edf39f3062712",
               "id": "cd600d47-0045-483f-87a1-5041ae2f513b",
               "ingress_firewall_policy_id": null,
               "description": "",
               "project_id": "23c8a121505047b6869edf39f3062712",
               "created_at": "2018-09-12T08:24:14",
               "updated_at": "2018-09-12T08:24:14"
           },
           {
               "status": "INACTIVE",
               "public": false,
               "egress_firewall_policy_id": "d939df29-fe76-4089-90c3-3778e4d53141",
               "name": "fwg-1475475043",
               "admin_state_up": true,
               "ports": [ ],
               "tenant_id": "0af57070695044ea9a70f04779e6aa1f",
               "id": "ca971b45-70ce-4879-9734-b6cac1d00845",
               "ingress_firewall_policy_id": "d939df29-fe76-4089-90c3-3778e4d53141",
               "description": "",
               "project_id": "0af57070695044ea9a70f04779e6aa1f",
               "created_at": "2018-09-12T08:24:14",
               "updated_at": "2018-09-12T08:24:14"
           }
       ],
       "firewall_groups_links": [
          {    "rel": "previous",
               "href": "https://{Endpoint}/v2.0/fwaas/firewall_groups?marker=cd600d47-0045-483f-87a1-5041ae2f513b&page_reverse=True"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
