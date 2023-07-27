:original_name: vpc_eip_0005.html

.. _vpc_eip_0005:

Releasing an EIP
================

Function
--------

This API is used to release an EIP.

URI
---

DELETE /v1/{project_id}/publicips/{publicip_id}

:ref:`Table 1 <vpc_eip_0005__table45251091>` describes the parameters.

.. _vpc_eip_0005__table45251091:

.. table:: **Table 1** Parameter description

   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name        | Mandatory | Description                                                                                                               |
   +=============+===========+===========================================================================================================================+
   | project_id  | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | publicip_id | Yes       | Specifies the unique identifier of an EIP.                                                                                |
   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v1/{project_id}/publicips/{publicip_id}

Response Message
----------------

-  Response parameter

   None

-  Example response

   None

   Or

   .. code-block::

      {
             "code":"xxx",
             "message":"xxxxx"
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
