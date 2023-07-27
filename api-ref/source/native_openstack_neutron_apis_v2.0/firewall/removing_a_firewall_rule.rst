:original_name: vpc_firewall_0012.html

.. _vpc_firewall_0012:

Removing a Firewall Rule
========================

Function
--------

This API is used to remove a firewall rule from a firewall policy.

URI
---

PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}/remove_rule

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +------------------+--------+-----------+------------------------------------------------------------------------------+
   | Parameter        | Type   | Mandatory | Description                                                                  |
   +==================+========+===========+==============================================================================+
   | firewall_rule_id | String | Yes       | Specifies the firewall rule ID, which uniquely identifies the firewall rule. |
   +------------------+--------+-----------+------------------------------------------------------------------------------+

Example Request
---------------

Remove ACL rule 0f82b221-8cd6-44bd-9dfc-0e118fa7b6b1 from the ACL policy whose ID is afc52ce9-5305-4ec9-9feb-44feb8330341.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/fwaas/firewall_policies/afc52ce9-5305-4ec9-9feb-44feb8330341/remove_rule

   {
       "firewall_rule_id": "0f82b221-8cd6-44bd-9dfc-0e118fa7b6b1"
   }

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

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
           "b8243448-cb3c-496e-851c-dadade4c161b"
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
