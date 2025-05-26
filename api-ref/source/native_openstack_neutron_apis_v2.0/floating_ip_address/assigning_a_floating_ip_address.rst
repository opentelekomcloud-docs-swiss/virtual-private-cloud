:original_name: vpc_floatingiP_0003.html

.. _vpc_floatingiP_0003:

Assigning a Floating IP Address
===============================

Function
--------

When assigning a floating IP address, you need to obtain the external network ID **floating_network_id** of the floating IP address.

You can use **GET /v2.0/networks?router:external=True** or run the **neutron net-external-list** command to obtain the UUID of the external network required for assigning a floating IP address.

URI
---

POST /v2.0/floatingips

Request Message
---------------

.. table:: **Table 1** Request parameter

   +------------+---------------------------------------------------------------------+-----------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                | Mandatory | Description                                                                                                         |
   +============+=====================================================================+===========+=====================================================================================================================+
   | floatingip | :ref:`floatingip <vpc_floatingip_0003__table15863423175513>` object | Yes       | Specifies the floating IP address list. For details, see :ref:`Table 2 <vpc_floatingip_0003__table15863423175513>`. |
   +------------+---------------------------------------------------------------------+-----------+---------------------------------------------------------------------------------------------------------------------+

.. _vpc_floatingip_0003__table15863423175513:

.. table:: **Table 2** **floatingip** objects

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                          |
   +=====================+=================+=================+======================================================================================================+
   | floating_ip_address | No              | String          | Specifies the floating IP address.                                                                   |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | floating_network_id | Yes             | String          | Specifies the external network ID.                                                                   |
   |                     |                 |                 |                                                                                                      |
   |                     |                 |                 | You can only use fixed external network.                                                             |
   |                     |                 |                 |                                                                                                      |
   |                     |                 |                 | You can use **GET /v2.0/networks?router:external=True** or                                           |
   |                     |                 |                 |                                                                                                      |
   |                     |                 |                 | **GET /v2.0/networks?name={floating_network}** or                                                    |
   |                     |                 |                 |                                                                                                      |
   |                     |                 |                 | run the **neutron net-external-list mode** command to obtain information about the external network. |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | port_id             | No              | String          | Specifies the port ID.                                                                               |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | fixed_ip_address    | No              | String          | Specifies the private IP address of the associated port.                                             |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 3** Response parameter

   +------------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                            | Description                                                                                                     |
   +============+=================================================================+=================================================================================================================+
   | floatingip | :ref:`floatingip <vpc_floatingip_0003__table8139247714>` object | Specifies the floating IP address list. For details, see :ref:`Table 4 <vpc_floatingip_0003__table8139247714>`. |
   +------------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

.. _vpc_floatingip_0003__table8139247714:

.. table:: **Table 4** **floatingip** objects

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                                                    |
   +=======================+=======================+================================================================================================+
   | status                | String                | Specifies the floating IP address status. The value can be **ACTIVE**, **DOWN**, or **ERROR**. |
   |                       |                       |                                                                                                |
   |                       |                       | -  **DOWN** indicates that the floating IP address has not been bound.                         |
   |                       |                       | -  **ACTIVE** indicates that the floating IP address has been bound.                           |
   |                       |                       | -  **ERROR** indicates that the floating IP address is abnormal.                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the floating IP address ID.                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | floating_ip_address   | String                | Specifies the floating IP address.                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | floating_network_id   | String                | Specifies the external network ID.                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | router_id             | String                | Specifies the ID of the belonged router.                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | port_id               | String                | Specifies the port ID.                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | fixed_ip_address      | String                | Specifies the private IP address of the associated port.                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Specifies the project ID.                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+

Example Request
---------------

Create a floating IP address whose network is **0a2228f2-7f8a-45f1-8e09-9039e1d09975**.

.. code-block:: text

   POST https://{Endpoint}/v2.0/floatingips

   {
       "floatingip": {
              "floating_network_id": "0a2228f2-7f8a-45f1-8e09-9039e1d09975"
       }
   }

Example Response
----------------

**Status code: 201**

Normal response to POST requests

.. code-block::

   {
       "floatingip": {
           "id": "b997e0d4-3359-4c74-8f88-bc0af81cd5a2",
           "status": "DOWN",
           "router_id": null,
           "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "floating_network_id": "0a2228f2-7f8a-45f1-8e09-9039e1d09975",
           "fixed_ip_address": null,
           "floating_ip_address": "88.88.215.205",
           "port_id": null,
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
