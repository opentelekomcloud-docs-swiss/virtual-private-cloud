:original_name: vpc_router_0006.html

.. _vpc_router_0006:

Adding an Interface to a Router
===============================

Function
--------

This API is used to add an interface to a router.

Restrictions

-  When a port is used, the port can have only one IP address.
-  When a subnet is used, the gateway IP address must be configured for the subnet.
-  A router cannot be added to networks whose **provider:network_type** is **geneve**.
-  Only one router can be added to a subnet.

URI
---

PUT /v2.0/routers/{router_id}/add_router_interface

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                               |
   +=================+=================+=================+===========================================================================================================================+
   | subnet_id       | String          | No              | Specifies the subnet ID. Either **subnet_id** or **port_id** is used.                                                     |
   |                 |                 |                 |                                                                                                                           |
   |                 |                 |                 | Use the gateway IP address of the subnet to create a router interface.                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | port_id         | String          | No              | Specifies the port ID. Either **subnet_id** or **port_id** is used. Use the port IP address to create a router interface. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Add an interface to the router. The router ID is i5b8e885c-1347-4ac2-baf9-2249c8ed1270, and the subnet ID is ab78be2d-782f-42a5-aa72-35879f6890ff.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/routers/5b8e885c-1347-4ac2-baf9-2249c8ed1270/add_router_interface

   {"subnet_id": "ab78be2d-782f-42a5-aa72-35879f6890ff"}

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   ========== ====== =========================
   Parameter  Type   Description
   ========== ====== =========================
   subnet_id  String Specifies the subnet ID.
   tenant_id  String Specifies the project ID.
   project_id String Specifies the project ID.
   port_id    String Specifies the port ID.
   id         String Specifies the router ID.
   ========== ====== =========================

Example Response
----------------

.. code-block::

   {
     "subnet_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
     "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
     "project_id": "6fbe9263116a4b68818cf1edce16bc4f",
     "port_id": "40e86635-b2a3-45de-a7c8-3cced5b7e755",
     "id": "5b8e885c-1347-4ac2-baf9-2249c8ed1270"
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
