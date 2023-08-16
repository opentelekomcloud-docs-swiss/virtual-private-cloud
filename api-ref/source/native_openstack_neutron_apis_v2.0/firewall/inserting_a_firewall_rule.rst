:original_name: vpc_firewall_0011.html

.. _vpc_firewall_0011:

Inserting a Firewall Rule
=========================

Function
--------

This API is used to insert a firewall rule to a firewall policy.

URI
---

PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}/insert_rule

:ref:`Table 1 <vpc_firewall_0011__table18880184689>` describes the parameters.

.. _vpc_firewall_0011__table18880184689:

.. table:: **Table 1** Parameter description

   +--------------------+-----------+--------+----------------------------------------------------------------------------------+
   | Name               | Mandatory | Type   | Description                                                                      |
   +====================+===========+========+==================================================================================+
   | firewall_policy_id | Yes       | String | Specifies the firewall policy ID, which uniquely identifies the firewall policy. |
   +--------------------+-----------+--------+----------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type            | Mandatory       | Description                                                                                                                                                                                                               |
   +==================+=================+=================+===========================================================================================================================================================================================================================+
   | firewall_rule_id | String          | Yes             | Specifies the firewall rule ID, which uniquely identifies the firewall rule.                                                                                                                                              |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | insert_after     | String          | No              | The **insert_after** parameter indicates the firewall rule that has already been associated with the firewall policy. A new firewall rule will be inserted after the firewall rule associated with the firewall policy.   |
   |                  |                 |                 |                                                                                                                                                                                                                           |
   |                  |                 |                 | If both the **insert_after** and **insert_before** parameters are specified, the **insert_after** parameter will be ignored.                                                                                              |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | insert_before    | String          | No              | The **insert_before** parameter indicates the firewall rule that has already been associated with the firewall policy. A new firewall rule will be inserted before the firewall rule associated with the firewall policy. |
   |                  |                 |                 |                                                                                                                                                                                                                           |
   |                  |                 |                 | If both the **insert_after** and **insert_before** parameters are specified, the **insert_after** parameter will be ignored.                                                                                              |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Insert rule 0f82b221-8cd6-44bd-9dfc-0e118fa7b6b1 below rule b8243448-cb3c-496e-851c-dadade4c161b in the ACL policy whose ID is afc52ce9-5305-4ec9-9feb-44feb8330341.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/fwaas/firewall_policies/afc52ce9-5305-4ec9-9feb-44feb8330341/insert_rule

   {
       "insert_after": "b8243448-cb3c-496e-851c-dadade4c161b",
       "firewall_rule_id": "0f82b221-8cd6-44bd-9dfc-0e118fa7b6b1",
       "insert_before": ""
   }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type             | Description                                                                                                                                                           |
   +================+==================+=======================================================================================================================================================================+
   | description    | String           | Provides supplementary information about the firewall policy.                                                                                                         |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | audited        | Boolean          | Each time the firewall policy or the associated firewall rules are changed, this attribute will be set to **False**.                                                  |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | firewall_rules | Array of strings | Specifies the ID list of the firewall rules associated with the current firewall policy.                                                                              |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id             | String           | Specifies the firewall policy ID.                                                                                                                                     |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name           | String           | Specifies the firewall policy name.                                                                                                                                   |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public         | Boolean          | If this attribute is set to **true**, the firewall policy is visible to tenants other than its owner. The firewall policy is not visible to other tenants by default. |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id      | String           | Specifies the project ID.                                                                                                                                             |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id     | String           | Specifies the project ID.                                                                                                                                             |
   +----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "description": "",
       "firewall_rules": [
           "b8243448-cb3c-496e-851c-dadade4c161b",
           "0f82b221-8cd6-44bd-9dfc-0e118fa7b6b1"
       ],
       "tenant_id": "23c8a121505047b6869edf39f3062712",
       "public": false,
       "id": "afc52ce9-5305-4ec9-9feb-44feb8330341",
       "audited": false,
       "name": "test-policy",
       "project_id": "23c8a121505047b6869edf39f3062712"
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
