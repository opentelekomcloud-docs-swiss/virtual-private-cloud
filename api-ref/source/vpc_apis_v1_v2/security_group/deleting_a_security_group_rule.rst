:original_name: vpc_sg01_0008.html

.. _vpc_sg01_0008:

Deleting a Security Group Rule
==============================

Function
--------

This API is used to delete a security group rule.

URI
---

DELETE /v1/{project_id}/security-group-rules/{security_group_rule_id}

:ref:`Table 1 <vpc_sg01_0008__table1939240195259>` describes the parameters.

.. _vpc_sg01_0008__table1939240195259:

.. table:: **Table 1** Parameter description

   +------------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory | Description                                                                                                               |
   +========================+===========+===========================================================================================================================+
   | security_group_rule_id | Yes       | Specifies the security group rule ID, which uniquely identifies the security group rule.                                  |
   +------------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id             | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/security-group-rules/2bc0accf-312e-429a-956e-e4407625eb62

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
