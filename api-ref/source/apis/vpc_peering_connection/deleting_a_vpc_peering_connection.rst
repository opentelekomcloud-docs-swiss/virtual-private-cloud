:original_name: vpc_peering_0007.html

.. _vpc_peering_0007:

Deleting a VPC Peering Connection
=================================

Function
--------

This API is used to delete a VPC peering connection.

A VPC peering connection can be deleted either by the local or peer tenant.

URI
---

DELETE /v2.0/vpc/peerings/{peering_id}

:ref:`Table 1 <vpc_peering_0007__table18880184689>` describes the parameters.

.. _vpc_peering_0007__table18880184689:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+------------------------------------------------------------------------------------------------+
   | Name       | Mandatory | Type   | Description                                                                                    |
   +============+===========+========+================================================================================================+
   | peering_id | Yes       | String | Specifies the VPC peering connection ID, which uniquely identifies the VPC peering connection. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/vpc/peerings/2b098395-046a-4071-b009-312bcee665cb

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
