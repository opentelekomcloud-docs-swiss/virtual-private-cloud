:original_name: eip_tag_0003.html

.. _eip_tag_0003:

Deleting an EIP Tag
===================

Function
--------

This API is used to delete an EIP tag.

URI
---

DELETE /v2.0/{project_id}/publicips/{publicip_id}/tags/{key}

:ref:`Table 1 <eip_tag_0003__table5716115334>` describes the parameters.

.. _eip_tag_0003__table5716115334:

.. table:: **Table 1** Parameter description

   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name        | Mandatory | Description                                                                                                               |
   +=============+===========+===========================================================================================================================+
   | project_id  | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | publicip_id | Yes       | Specifies the unique identifier of an EIP.                                                                                |
   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | key         | Yes       | Specifies the tag key.                                                                                                    |
   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2.0/{project_id}/publicips/{publicip_id}/tags/{key}

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
