:original_name: vpc_sharebandwidth_0003.html

.. _vpc_sharebandwidth_0003:

Deleting a Shared Bandwidth
===========================

Function
--------

This API is used to delete a shared bandwidth.

URI
---

DELETE /v2.0/{project_id}/bandwidths/{bandwidth_id}

:ref:`Table 1 <vpc_sharebandwidth_0003__table45251091>` describes the parameters.

.. _vpc_sharebandwidth_0003__table45251091:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | bandwidth_id          | Yes                   | Specifies the bandwidth ID, which uniquely identifies the bandwidth.                                                      |
   |                       |                       |                                                                                                                           |
   |                       |                       | Currently, only the shared bandwidth can be deleted.                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2.0/{project_id}/bandwidths/{bandwidth_id}

Response Message
----------------

-  Response parameter

   None

-  Example response

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
