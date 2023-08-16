:original_name: vpc_apiv3_0035.html

.. _vpc_apiv3_0035:

Deleting a Supplementary Network Interface
==========================================

Function
--------

This API is used to delete a supplementary network interface.

URI
---

DELETE /v3/{project_id}/vpc/sub-network-interfaces/{sub_network_interface_id}

.. table:: **Table 1** Parameter description

   +--------------------------+-----------+--------+----------------------------------------------------------+
   | Parameter                | Mandatory | Type   | Description                                              |
   +==========================+===========+========+==========================================================+
   | project_id               | Yes       | String | Project ID                                               |
   +--------------------------+-----------+--------+----------------------------------------------------------+
   | sub_network_interface_id | Yes       | String | Unique identifier of the supplementary network interface |
   +--------------------------+-----------+--------+----------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ========= ========= ==== ===========
   Parameter Mandatory Type Description
   ========= ========= ==== ===========
   ========= ========= ==== ===========

Response Parameters
-------------------

When the status code is **400**, the response parameters are as follows:

.. table:: **Table 3** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **401**, the response parameters are as follows:

.. table:: **Table 4** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **403**, the response parameters are as follows:

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **404**, the response parameters are as follows:

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **409**, the response parameters are as follows:

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **500**, the response parameters are as follows:

.. table:: **Table 8** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

Example Request
---------------

Delete a supplementary network interface.

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/vpc/sub-network-interfaces/2be868f2-f7c9-48db-abc0-eea0b9105b0d

Example Response
----------------

When the status code is **400**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **401**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **403**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **404**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **409**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

When the status code is **500**, the response parameters are as follows:

.. code-block::

   {
     "request_id" : "string",
     "error_msg" : "string",
     "error_code" : "string"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
204         No Content
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
409         Conflict
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
