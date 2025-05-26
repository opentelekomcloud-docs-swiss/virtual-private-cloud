:original_name: vpc_firewall_0014.html

.. _vpc_firewall_0014:

Querying a Firewall Group
=========================

Function
--------

This API is used to query details about a specific firewall group.

URI
---

GET /v2.0/fwaas/firewall_groups/{firewall_group_id}

:ref:`Table 1 <vpc_firewall_0014__table18880184689>` describes the parameters.

.. _vpc_firewall_0014__table18880184689:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                                       |
   +===================+===========+========+===================================================================================================================================+
   | firewall_group_id | Yes       | String | Specifies the firewall group ID, which uniquely identifies the firewall group. The **fire_group_id** value is used as the filter. |
   +-------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_groups/a504a4cf-9300-40e0-b2d4-649bd157c55a

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +----------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                                  | Description                                                                                             |
   +================+=======================================================================+=========================================================================================================+
   | firewall_group | :ref:`firewall_group <vpc_firewall_0014__table31629250121127>` object | Specifies the firewall group. For details, see :ref:`Table 3 <vpc_firewall_0014__table31629250121127>`. |
   +----------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0014__table31629250121127:

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
   | status                     | String                | Specifies the status of the firewall policy.                                                                              |
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

Example Response
----------------

.. code-block::

   {
       "firewall_group": {
           "status": "ACTIVE",
           "public": false,
           "egress_firewall_policy_id": null,
           "name": "bobby_fwg1",
           "admin_state_up": true,
           "ports": [
               "16e6d779-15e9-48fb-abc5-b86457792a15"
           ],
           "tenant_id": "23c8a121505047b6869edf39f3062712",
           "id": "a504a4cf-9300-40e0-b2d4-649bd157c55a",
           "ingress_firewall_policy_id": "fed2d88f-d0e7-4cc5-bd7e-c495f67037b6",
           "description": "test",
           "project_id": "23c8a121505047b6869edf39f3062712",
           "created_at": "2018-09-12T08:24:14",
           "updated_at": "2018-09-12T08:24:14"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
