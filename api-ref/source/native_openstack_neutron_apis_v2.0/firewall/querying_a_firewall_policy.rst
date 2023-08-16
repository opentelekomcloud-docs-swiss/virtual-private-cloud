:original_name: vpc_firewall_0007.html

.. _vpc_firewall_0007:

Querying a Firewall Policy
==========================

Function
--------

This API is used to query details about a specific firewall policy.

URI
---

GET /v2.0/fwaas/firewall_policies/{firewall_policy_id}

:ref:`Table 1 <vpc_firewall_0007__table18880184689>` describes the parameters.

.. _vpc_firewall_0007__table18880184689:

.. table:: **Table 1** Parameter description

   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Name               | Mandatory | Type   | Description                                                                                                                              |
   +====================+===========+========+==========================================================================================================================================+
   | firewall_policy_id | Yes       | String | Specifies the firewall policy ID, which uniquely identifies the firewall policy. The **firewall_policy_id** value is used as the filter. |
   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_policies/fed2d88f-d0e7-4cc5-bd7e-c495f67037b6

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                   | Description                                                                                              |
   +=================+========================================================================+==========================================================================================================+
   | firewall_policy | :ref:`firewall_policy <vpc_firewall_0007__table17002720121127>` object | Specifies the firewall policy. For details, see :ref:`Table 3 <vpc_firewall_0007__table17002720121127>`. |
   +-----------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0007__table17002720121127:

.. table:: **Table 3** **Firewall Policy** objects

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
   | firewall_rules | Array of strings | Specifies the firewall rules referenced by the firewall policy.                                                           |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | audited        | Boolean          | Specifies the audit flag.                                                                                                 |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | public         | Boolean          | Specifies whether the firewall policy can be shared by different tenants.                                                 |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id     | String           | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "firewall_policy": {
           "description": "",
           "firewall_rules": [
               "3c0e6267-73df-4d9a-87a6-e226f2db2036"
           ],
           "tenant_id": "23c8a121505047b6869edf39f3062712",
           "public": false,
           "id": "fed2d88f-d0e7-4cc5-bd7e-c495f67037b6",
           "audited": false,
           "name": "bobby_fwp1",
           "project_id": "23c8a121505047b6869edf39f3062712"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
