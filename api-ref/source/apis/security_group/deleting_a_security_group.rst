:original_name: vpc_sg01_0004.html

.. _vpc_sg01_0004:

Deleting a Security Group
=========================

Function
--------

This API is used to delete a security group.

URI
---

DELETE /v1/{project_id}/security-groups/{security_group_id}

:ref:`Table 1 <vpc_sg01_0004__table1939240195259>` describes the parameters.

.. _vpc_sg01_0004__table1939240195259:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name              | Mandatory | Description                                                                                                               |
   +===================+===========+===========================================================================================================================+
   | security_group_id | Yes       | Specifies the security group ID, which uniquely identifies the security group.                                            |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id        | No        | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/security-groups/0c4a2336-b036-4fa2-bc3c-1a291ed4c431

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
