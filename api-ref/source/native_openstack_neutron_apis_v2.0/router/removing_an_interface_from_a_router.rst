:original_name: vpc_router_0007.html

.. _vpc_router_0007:

Removing an Interface from a Router
===================================

Function
--------

Removing an interface from a router will also remove the port.

Restrictions

You are not allowed to remove an interface from a router if there are load balancers in the subnet.

URI
---

PUT /v2.0/routers/{router_id}/remove_router_interface

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                               |
   +=================+=================+=================+===========================================================================================================================+
   | subnet_id       | String          | No              | Specifies the subnet ID. Either **subnet_id** or **port_id** must be specified.                                           |
   |                 |                 |                 |                                                                                                                           |
   |                 |                 |                 | Use the gateway IP address of the subnet to create a router interface.                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | port_id         | String          | No              | Specifies the port ID. Either **subnet_id** or **port_id** is used. Use the port IP address to create a router interface. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Remove an interface from a router. The router ID is b625c58c-0cfe-49e0-acc8-f2374f8187ff, and the subnet ID is 4b910a10-0860-428b-b463-d84dbc5e288e.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/routers/b625c58c-0cfe-49e0-acc8-f2374f8187ff/remove_router_interface

   {"subnet_id": "4b910a10-0860-428b-b463-d84dbc5e288e"}

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
     "subnet_id": "4b910a10-0860-428b-b463-d84dbc5e288e",
     "tenant_id": "3d72597871904daeb6887f75f848b531",
     "project_id": "3d72597871904daeb6887f75f848b531",
     "port_id": "34d7d063-8f40-4958-b420-096db40d4067",
     "id": "b625c58c-0cfe-49e0-acc8-f2374f8187ff"
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
