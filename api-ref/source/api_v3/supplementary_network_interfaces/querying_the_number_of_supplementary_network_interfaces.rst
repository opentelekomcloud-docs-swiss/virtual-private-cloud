:original_name: vpc_apiv3_0033.html

.. _vpc_apiv3_0033:

Querying the Number of Supplementary Network Interfaces
=======================================================

Function
--------

This API is used to query the number of supplementary network interfaces.

URI
---

GET /v3/{project_id}/vpc/sub-network-interfaces/count

.. table:: **Table 1** Parameter description

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ========= ========= ==== ===========
   Parameter Mandatory Type Description
   ========= ========= ==== ===========
   ========= ========= ==== ===========

Response Parameters
-------------------

When the status code is **200**, the response parameters are as follows:

.. table:: **Table 3** Response body parameters

   +------------------------+---------+--------------------------------------------+
   | Parameter              | Type    | Description                                |
   +========================+=========+============================================+
   | request_id             | String  | Request ID                                 |
   +------------------------+---------+--------------------------------------------+
   | sub_network_interfaces | Integer | Number of supplementary network interfaces |
   +------------------------+---------+--------------------------------------------+

When the status code is **400**, the response parameters are as follows:

.. table:: **Table 4** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **401**, the response parameters are as follows:

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **403**, the response parameters are as follows:

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

When the status code is **500**, the response parameters are as follows:

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   request_id String Request ID
   error_msg  String Error message
   error_code String Error code
   ========== ====== =============

Example Request
---------------

Query the number of supplementary network interfaces.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/sub-network-interfaces/count

Example Response
----------------

When the status code is **200**, the response parameters are as follows:

OK

.. code-block::

   {
     "sub_network_interfaces" : 2,
     "request_id" : "4a79f1f7-67eb-43be-a8be-eb57ba894f90"
   }

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
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
