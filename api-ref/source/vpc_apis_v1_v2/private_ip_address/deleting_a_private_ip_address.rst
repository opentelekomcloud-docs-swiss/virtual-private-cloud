:original_name: vpc_privateip_0004.html

.. _vpc_privateip_0004:

Deleting a Private IP Address
=============================

Function
--------

This API is used to delete a private IP address.

URI
---

DELETE /v1/{project_id}/privateips/{privateip_id}

:ref:`Table 1 <vpc_privateip_0004__table24633528>` describes the parameters.

.. _vpc_privateip_0004__table24633528:

.. table:: **Table 1** Parameter description

   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Description                                                                                                               |
   +==============+===========+===========================================================================================================================+
   | project_id   | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | privateip_id | Yes       | Specifies the ID of the private IP address, which uniquely identifies the private IP address.                             |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/privateips/4779ab1c-7c1a-44b1-a02e-93dfc361b32d

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
