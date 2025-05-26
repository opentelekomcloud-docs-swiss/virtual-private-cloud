:original_name: vpc_firewall_0010.html

.. _vpc_firewall_0010:

Deleting a Firewall Policy
==========================

Function
--------

This API is used to delete a firewall policy.

URI
---

DELETE /v2.0/fwaas/firewall_policies/{firewall_policy_id}

:ref:`Table 1 <vpc_firewall_0010__table18880184689>` describes the parameters.

.. _vpc_firewall_0010__table18880184689:

.. table:: **Table 1** Parameter description

   +--------------------+-----------+--------+----------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type   | Description                                                                      |
   +====================+===========+========+==================================================================================+
   | firewall_policy_id | Yes       | String | Specifies the firewall policy ID, which uniquely identifies the firewall policy. |
   +--------------------+-----------+--------+----------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/fwaas/firewall_policies/2fb0e81f-9f63-44b2-9894-c13a3284594a

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
