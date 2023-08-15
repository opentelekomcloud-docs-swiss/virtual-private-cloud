:original_name: vpc_floatingiP_0005.html

.. _vpc_floatingiP_0005:

Deleting a Floating IP Address
==============================

Function
--------

This API is used to delete a floating IP address.

URI
---

DELETE /v2.0/floatingips/{floatingip_id}

:ref:`Table 1 <vpc_floatingip_0005__table49321613135118>` describes the parameters.

.. _vpc_floatingip_0005__table49321613135118:

.. table:: **Table 1** Parameter description

   ============= ========= ====== =====================================
   Parameter     Mandatory Type   Description
   ============= ========= ====== =====================================
   floatingip_id Yes       String Specifies the floating IP address ID.
   ============= ========= ====== =====================================

Request Message
---------------

None

Response Message
----------------

None

Example:
--------

Example request

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/floatingips/a95ec431-8473-463b-aede-34fb048ee3a7

Example response

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
