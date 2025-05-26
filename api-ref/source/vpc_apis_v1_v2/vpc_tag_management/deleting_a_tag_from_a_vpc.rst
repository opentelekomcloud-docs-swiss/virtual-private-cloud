:original_name: vpc_tag_0003.html

.. _vpc_tag_0003:

Deleting a Tag from a VPC
=========================

Function
--------

This API is used to delete a tag from a VPC.

URI
---

DELETE /v2.0/{project_id}/vpcs/{vpc_id}/tags/{key}

:ref:`Table 1 <vpc_tag_0003__table27380479>` describes the parameters.

.. _vpc_tag_0003__table27380479:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | vpc_id     | Yes       | Specifies the VPC ID, which uniquely identifies the VPC.                                                                  |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | key        | Yes       | Specifies the tag key.                                                                                                    |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/{project_id}/vpcs/{vpc_id}/tags/{key}

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
