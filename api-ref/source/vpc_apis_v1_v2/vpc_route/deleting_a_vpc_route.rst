:original_name: vpc_route_0004.html

.. _vpc_route_0004:

Deleting a VPC Route
====================

Function
--------

This API is used to delete a route.

URI
---

DELETE /v2.0/vpc/routes/{route_id}

:ref:`Table 1 <vpc_route_0004__table18880184689>` describes the parameters.

.. _vpc_route_0004__table18880184689:

.. table:: **Table 1** Parameter description

   +-----------+-----------+--------+--------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                  |
   +===========+===========+========+==============================================================+
   | route_id  | Yes       | String | Specifies the route ID, which uniquely identifies the route. |
   +-----------+-----------+--------+--------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/vpc/routes/60c809cb-6731-45d0-ace8-3bf5626421a9

Response Parameters
-------------------

None

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
