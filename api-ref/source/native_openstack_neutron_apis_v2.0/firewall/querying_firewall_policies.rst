:original_name: vpc_firewall_0006.html

.. _vpc_firewall_0006:

Querying Firewall Policies
==========================

Function
--------

This API is used to query all firewall policies accessible to the tenant submitting the request.

URI
---

GET /v2.0/fwaas/firewall_policies

Example of querying policies by page

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_policies?limit=2&marker=6b70e321-0c21-4b83-bb8a-a886d1414a5f&page_reverse=False

:ref:`Table 1 <vpc_firewall_0006__table2168229184411>` describes the parameters.

.. _vpc_firewall_0006__table2168229184411:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================+
   | id              | No              | String          | Specifies that the firewall policy ID is used as the filtering condition.                                                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Specifies that the firewall policy name is used as the filtering condition.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Specifies that the firewall policy description is used as the filtering condition.                                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies that the project ID of the firewall policy is used as the filtering condition.                                                                                                                                           |
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

   GET https://{Endpoint}/v2.0/fwaas/firewall_policies

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-------------------------+-------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                                                                                | Description                                                                                                                                                                                                     |
   +=========================+=====================================================================================+=================================================================================================================================================================================================================+
   | firewall_policies       | Array of :ref:`firewall Policy <vpc_firewall_0006__table17002720121127>` object     | Specifies the firewall policies. For details, see :ref:`Table 3 <vpc_firewall_0006__table17002720121127>`.                                                                                                      |
   +-------------------------+-------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | firewall_policies_links | Array of :ref:`firewall_policies_link <vpc_firewall_0006__table25150247450>` object | **firewall_policies_link** object. For details, see :ref:`Table 4 <vpc_firewall_0006__table25150247450>`.                                                                                                       |
   |                         |                                                                                     |                                                                                                                                                                                                                 |
   |                         |                                                                                     | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**. |
   +-------------------------+-------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0006__table17002720121127:

.. table:: **Table 3** **firewall_Policy** object

   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Attribute      | Type             | Description                                                                                                               |
   +================+==================+===========================================================================================================================+
   | id             | String           | Specifies the UUID of the firewall policy.                                                                                |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | name           | String           | Specifies the name of the firewall policy.                                                                                |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | description    | String           | Provides supplementary information about the firewall policy.                                                             |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | tenant_id      | String           | Specifies the project ID.                                                                                                 |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | firewall_rules | Array of strings | Specifies the rules referenced by the firewall policy.                                                                    |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | audited        | Boolean          | Specifies the audit flag.                                                                                                 |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | public         | Boolean          | Specifies whether the policy can be shared by different tenants.                                                          |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id     | String           | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0006__table25150247450:

.. table:: **Table 4** **firewall_policies_link** object

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
       "firewall_policies": [
           {
               "description": "",
               "firewall_rules": [
                   "6c6803e0-ca8c-4aa9-afb3-4f89275b6c32"
               ],
               "tenant_id": "23c8a121505047b6869edf39f3062712",
               "public": false,
               "id": "6b70e321-0c21-4b83-bb8a-a886d1414a5f",
               "audited": false,
               "name": "fwp1",
               "project_id": "23c8a121505047b6869edf39f3062712"
           },
           {
               "description": "",
               "firewall_rules": [
                   "6c6803e0-ca8c-4aa9-afb3-4f89275b6c32"
               ],
               "tenant_id": "23c8a121505047b6869edf39f3062712",
               "public": false,
               "id": "fce92002-5a15-465d-aaca-9b44453bb738",
               "audited": false,
               "name": "fwp2",
               "project_id": "23c8a121505047b6869edf39f3062712"
           }
       ],
       "firewall_policies_links": [
          {    "rel": "previous",
               "href": "https://{Endpoint}/v2.0/fwaas/firewall_policies?marker=6b70e321-0c21-4b83-bb8a-a886d1414a5f&page_reverse=True"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
