:original_name: vpc_firewall_0008.html

.. _vpc_firewall_0008:

Creating a Firewall Policy
==========================

Function
--------

This API is used to create a firewall policy. A firewall policy must be associated with a firewall group. You can learn more about the :ref:`relationships among network ACL groups, policies, and rules <en-us_topic_0000001487936070>`.

URI
---

POST /v2.0/fwaas/firewall_policies

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------------+------------------------------------------------------------------------+-----------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                   | Mandatory | Description                                                                                              |
   +=================+========================================================================+===========+==========================================================================================================+
   | firewall_policy | :ref:`firewall_policy <vpc_firewall_0008__table17002720121127>` object | Yes       | Specifies the firewall policy. For details, see :ref:`Table 2 <vpc_firewall_0008__table17002720121127>`. |
   +-----------------+------------------------------------------------------------------------+-----------+----------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0008__table17002720121127:

.. table:: **Table 2** **Firewall Policy** objects

   +-----------------+-----------------+------------------+-----------------------------------------------------------------+
   | Attribute       | Mandatory       | Type             | Description                                                     |
   +=================+=================+==================+=================================================================+
   | name            | No              | String           | Specifies the name of the firewall policy.                      |
   |                 |                 |                  |                                                                 |
   |                 |                 |                  | The value can contain a maximum of 255 characters.              |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------+
   | description     | No              | String           | Provides supplementary information about the firewall policy.   |
   |                 |                 |                  |                                                                 |
   |                 |                 |                  | The value can contain a maximum of 255 characters.              |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------+
   | firewall_rules  | No              | Array of strings | Specifies the firewall rules referenced by the firewall policy. |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------+
   | audited         | No              | Boolean          | Specifies the audit flag.                                       |
   |                 |                 |                  |                                                                 |
   |                 |                 |                  | The value can be **true** or **false**.                         |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------+

Example Request
---------------

Create an ACL policy named **test-policy** and associate it with the ACL rule whose ID is b8243448-cb3c-496e-851c-dadade4c161b.

.. code-block:: text

   POST https://{Endpoint}/v2.0/fwaas/firewall_policies

   {
       "firewall_policy": {
           "name": "test-policy",
           "firewall_rules": [
               "b8243448-cb3c-496e-851c-dadade4c161b"
           ]
       }
   }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +-----------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                  | Description                                                                                             |
   +=================+=======================================================================+=========================================================================================================+
   | firewall_policy | :ref:`firewall_policy <vpc_firewall_0008__table6763048152111>` object | Specifies the firewall policy. For details, see :ref:`Table 4 <vpc_firewall_0008__table6763048152111>`. |
   +-----------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0008__table6763048152111:

.. table:: **Table 4** **Firewall Policy** objects

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
               "b8243448-cb3c-496e-851c-dadade4c161b"
           ],
           "tenant_id": "23c8a121505047b6869edf39f3062712",
           "public": false,
           "id": "2fb0e81f-9f63-44b2-9894-c13a3284594a",
           "audited": false,
           "name": "test-policy",
           "project_id": "23c8a121505047b6869edf39f3062712"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
