:original_name: vpc_floatingiP_0004.html

.. _vpc_floatingiP_0004:

Updating a Floating IP Address
==============================

Function
--------

This API is used to update a floating IP address.

During the update, the ID of the floating IP address must be provided in the URL.

If **port_id** is left blank, the floating IP address has been unbound from the port.

.. note::

   This API has the following constraints:

   -  If a floating IP address that you are binding is in the **error** state, unbind the IP address first.
   -  Do not associate a port that has a floating IP address associated to another floating IP address. You must first disassociate the port from the IP address and then associate it with another IP address.

URI
---

PUT /v2.0/floatingips/{floatingip_id}

:ref:`Table 1 <vpc_floatingip_0004__table5388109319164>` describes the parameters.

.. _vpc_floatingip_0004__table5388109319164:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================+
   | floatingip_id   | Yes             | String          | Specifies the floating IP address ID.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | This parameter is not required when you assign a floating IP address. This parameter is mandatory when you query, update, or delete a floating IP address. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

.. table:: **Table 2** Request parameter

   +------------+-------------------------------------------------------------------+-----------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                              | Mandatory | Description                                                                                                       |
   +============+===================================================================+===========+===================================================================================================================+
   | floatingip | :ref:`floatingip <vpc_floatingip_0004__table547993685510>` object | Yes       | Specifies the floating IP address list. For details, see :ref:`Table 3 <vpc_floatingip_0004__table547993685510>`. |
   +------------+-------------------------------------------------------------------+-----------+-------------------------------------------------------------------------------------------------------------------+

.. _vpc_floatingip_0004__table547993685510:

.. table:: **Table 3** **floatingip** objects

   ========= ========= ====== ======================
   Parameter Mandatory Type   Description
   ========= ========= ====== ======================
   port_id   No        String Specifies the port ID.
   ========= ========= ====== ======================

Response Message
----------------

.. table:: **Table 4** Response parameter

   +------------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                            | Description                                                                                                     |
   +============+=================================================================+=================================================================================================================+
   | floatingip | :ref:`floatingip <vpc_floatingip_0004__table8139247714>` object | Specifies the floating IP address list. For details, see :ref:`Table 5 <vpc_floatingip_0004__table8139247714>`. |
   +------------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

.. _vpc_floatingip_0004__table8139247714:

.. table:: **Table 5** **floatingip** objects

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

-  Unbind a floating IP address from a port.

   .. code-block:: text

      PUT https://{Endpoint}/v2.0/floatingips/b997e0d4-3359-4c74-8f88-bc0af81cd5a2

      {
          "floatingip": {
              "port_id": null
          }
      }

-  Bind a floating IP address to a port. The port ID is f91f5763-c5a2-4458-979d-61e48b3c3fac.

   .. code-block:: text

      PUT https://{Endpoint}/v2.0/floatingips/b997e0d4-3359-4c74-8f88-bc0af81cd5a2

      {
          "floatingip": {
                 "port_id": "f91f5763-c5a2-4458-979d-61e48b3c3fac"
          }
      }

Example Response
----------------

**Status code: 200**

(The floating IP address is unbound from the port.)

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

(The floating IP address is bound to the port.)

.. code-block::

   {
       "floatingip": {
           "id": "b997e0d4-3359-4c74-8f88-bc0af81cd5a2",
           "status": "DOWN",
           "router_id": null,
           "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "floating_network_id": "0a2228f2-7f8a-45f1-8e09-9039e1d09975",
           "fixed_ip_address": "192.168.10.3",
           "floating_ip_address": "88.88.215.205",
           "port_id": "f91f5763-c5a2-4458-979d-61e48b3c3fac",
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
