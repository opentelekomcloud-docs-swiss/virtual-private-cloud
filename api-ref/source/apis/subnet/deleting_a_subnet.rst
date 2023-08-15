:original_name: vpc_subnet01_0005.html

.. _vpc_subnet01_0005:

Deleting a Subnet
=================

Function
--------

This API is used to delete a subnet.

URI
---

DELETE /v1/{project_id}/vpcs/{vpc_id}/subnets/{subnet_id}

:ref:`Table 1 <vpc_subnet01_0005__table23279683>` describes the parameters.

.. _vpc_subnet01_0005__table23279683:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Mandatory             | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | Yes                   | Specifies the ID of the subnet VPC.                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | subnet_id             | Yes                   | Specifies the subnet ID, which uniquely identifies the subnet.                                                            |
   |                       |                       |                                                                                                                           |
   |                       |                       | If you use the management console, the value of this parameter is the **Network ID** value.                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/vpcs/{vpc_id}/subnets/4779ab1c-7c1a-44b1-a02e-93dfc361b32d

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
