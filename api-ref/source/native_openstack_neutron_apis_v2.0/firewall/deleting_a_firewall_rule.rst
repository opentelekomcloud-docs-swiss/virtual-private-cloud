:original_name: vpc_firewall_0005.html

.. _vpc_firewall_0005:

Deleting a Firewall Rule
========================

Function
--------

This API is used to delete a firewall rule.

.. note::

   Before deleting a rule, you need to remove the rule from the corresponding policy first. For details, see :ref:`Removing a Firewall Rule <vpc_firewall_0012>`.

URI
---

DELETE /v2.0/fwaas/firewall_rules/{firewall_rule_id}

:ref:`Table 1 <vpc_firewall_0005__table18880184689>` describes the parameters.

.. _vpc_firewall_0005__table18880184689:

.. table:: **Table 1** Parameter description

   +------------------+-----------+--------+------------------------------------------------------------------------------+
   | Name             | Mandatory | Type   | Description                                                                  |
   +==================+===========+========+==============================================================================+
   | firewall_rule_id | Yes       | String | Specifies the firewall rule ID, which uniquely identifies the firewall rule. |
   +------------------+-----------+--------+------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/fwaas/firewall_rules/b94acf06-efc2-485d-ba67-a61acf2a7e28

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
