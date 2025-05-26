:original_name: subnet_tag_0003.html

.. _subnet_tag_0003:

Deleting a Tag from a Subnet
============================

Function
--------

This API is used to delete a tag from a subnet.

URI
---

DELETE /v2.0/{project_id}/subnets/{subnet_id}/tags/{key}

:ref:`Table 1 <subnet_tag_0003__table27380479>` describes the parameters.

.. _subnet_tag_0003__table27380479:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | subnet_id             | Yes                   | Specifies the subnet ID, which uniquely identifies the subnet.                                                            |
   |                       |                       |                                                                                                                           |
   |                       |                       | If you use the management console, the value of this parameter is the **Network ID** value.                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | key                   | Yes                   | Specifies the tag key.                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/{project_id}/subnets/{subnet_id}/tags/{key}

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
