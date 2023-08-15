:original_name: vpc_route_0003.html

.. _vpc_route_0003:

Creating a VPC Route
====================

Function
--------

This API is used to create a route.

URI
---

POST /v2.0/vpc/routes

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------+--------------------------------------+-----------+------------------------------------------------------------------------------------------+
   | Parameter | Type                                 | Mandatory | Description                                                                              |
   +===========+======================================+===========+==========================================================================================+
   | route     | :ref:`route <vpc_route_0003>` object | Yes       | Specifies the route. For details, see :ref:`Table 2 <vpc_route_0003__table05001250111>`. |
   +-----------+--------------------------------------+-----------+------------------------------------------------------------------------------------------+

.. _vpc_route_0003__table05001250111:

.. table:: **Table 2** **route** objects

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | Attribute       | Type            | Mandatory       | Description                                                                                           |
   +=================+=================+=================+=======================================================================================================+
   | destination     | String          | Yes             | Specifies the destination address in the CIDR notation format, for example, 192.168.200.0/24.         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | nexthop         | String          | Yes             | Specifies the next hop. If the route type is **peering**, enter the VPC peering connection ID.        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | type            | String          | Yes             | Specifies the route type.                                                                             |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Currently, only the **peering** type is supported, that is, the next hop is a VPC peering connection. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | vpc_id          | String          | Yes             | Specifies the ID of the VPC ID requesting for creating a route.                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Create a route in the route table of the VPC whose ID is ab78be2d-782f-42a5-aa72-35879f6890ff for the VPC peering connection. The next hop is the peering connection whose ID is 60c809cb-6731-45d0-ace8-3bf5626421a9, and the destination is 192.168.200.0/24.

   .. code-block:: text

      POST https://{Endpoint}/v2.0/vpc/routes

      {
          "route": {
              "type": "peering",
              "nexthop": "60c809cb-6731-45d0-ace8-3bf5626421a9",
              "destination": "192.168.200.0/24",
              "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff"
          }
      }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +-----------+--------------------------------------+--------------------------------------------------------------------------------------------+
   | Parameter | Type                                 | Description                                                                                |
   +===========+======================================+============================================================================================+
   | route     | :ref:`route <vpc_route_0003>` object | Specifies the route. For details, see :ref:`Table 4 <vpc_route_0003__table1163544010410>`. |
   +-----------+--------------------------------------+--------------------------------------------------------------------------------------------+

.. _vpc_route_0003__table1163544010410:

.. table:: **Table 4** **route** objects

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
