:original_name: vpc_firewall_0017.html

.. _vpc_firewall_0017:

Deleting a Firewall Group
=========================

Function
--------

This API is used to delete a firewall group.

URI
---

DELETE /v2.0/fwaas/firewall_groups/{firewall_group_id}

:ref:`Table 1 <vpc_firewall_0017__table18880184689>` describes the parameters.

.. _vpc_firewall_0017__table18880184689:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+--------+--------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                    |
   +===================+===========+========+================================================================================+
   | firewall_group_id | Yes       | String | Specifies the firewall group ID, which uniquely identifies the firewall group. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/fwaas/firewall_groups/0415f554-26ed-44e7-a881-bdf4e6216e38

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
