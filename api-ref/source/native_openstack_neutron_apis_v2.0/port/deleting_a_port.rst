:original_name: vpc_port02_0005.html

.. _vpc_port02_0005:

Deleting a Port
===============

Function
--------

This API is used to delete a port.

Restrictions

-  A port with **device_owner** set to a value other than **neutron:VIP_PORT** cannot be deleted.
-  A port with **device_id** specified cannot be deleted.

URI
---

DELETE /v2.0/ports/{port_id}

:ref:`Table 1 <vpc_port02_0005__table1855162528>` describes the parameters.

.. _vpc_port02_0005__table1855162528:

.. table:: **Table 1** Parameter description

   +-----------+-----------+----------------------------------------------------------+
   | Parameter | Mandatory | Description                                              |
   +===========+===========+==========================================================+
   | port_id   | Yes       | Specifies the port ID that uniquely identifies the port. |
   +-----------+-----------+----------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/ports/2b098395-046a-4071-b009-312bcee665cb

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
