:original_name: vpc_route_0002.html

.. _vpc_route_0002:

Querying a VPC Route
====================

Function
--------

This API is used to query details about a route.

URI
---

GET /v2.0/vpc/routes/{route_id}

:ref:`Table 1 <vpc_route_0002__table18880184689>` describes the parameters.

.. _vpc_route_0002__table18880184689:

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

   GET https://{Endpoint}/v2.0/vpc/routes/60c809cb-6731-45d0-ace8-3bf5626421a9

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+--------------------------------------+------------------------------------------------------------------------------------------+
   | Parameter | Type                                 | Description                                                                              |
   +===========+======================================+==========================================================================================+
   | route     | :ref:`route <vpc_route_0002>` object | Specifies the route. For details, see :ref:`Table 3 <vpc_route_0002__table05001250111>`. |
   +-----------+--------------------------------------+------------------------------------------------------------------------------------------+

.. _vpc_route_0002__table05001250111:

.. table:: **Table 3** **route** objects

   +-------------+--------+------------------------------------------------------------------------------------------------+
   | Attribute   | Type   | Description                                                                                    |
   +=============+========+================================================================================================+
   | id          | String | Specifies the route ID.                                                                        |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | destination | String | Specifies the destination address in the CIDR notation format, for example, 192.168.200.0/24.  |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | nexthop     | String | Specifies the next hop. If the route type is **peering**, enter the VPC peering connection ID. |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | type        | String | Specifies the route type. Currently, the value can only be **peering**.                        |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | vpc_id      | String | Specifies the VPC of the route. Set this parameter to the existing VPC ID.                     |
   +-------------+--------+------------------------------------------------------------------------------------------------+
   | tenant_id   | String | Specifies the project ID.                                                                      |
   +-------------+--------+------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "route": {
           "type": "peering",
           "nexthop": "60c809cb-6731-45d0-ace8-3bf5626421a9",
           "destination": "192.168.200.0/24",
           "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
           "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
           "id": "3d42a0d4-a980-4613-ae76-a2cddecff054"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
