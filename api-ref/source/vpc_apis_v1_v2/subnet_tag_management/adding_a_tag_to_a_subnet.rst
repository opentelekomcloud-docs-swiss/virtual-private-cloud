:original_name: subnet_tag_0001.html

.. _subnet_tag_0001:

Adding a Tag to a Subnet
========================

Function
--------

This API is used to add a tag to a subnet.

URI
---

POST /v2.0/{project_id}/subnets/{subnet_id}/tags

:ref:`Table 1 <subnet_tag_0001__table27380479>` describes the parameters.

.. _subnet_tag_0001__table27380479:

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

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +-----------+----------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                     | Mandatory | Description                                                                                            |
   +===========+==========================================================+===========+========================================================================================================+
   | tag       | :ref:`tag <subnet_tag_0001__table13242848193719>` object | Yes       | Specifies the **tag** objects. For details, see :ref:`Table 3 <subnet_tag_0001__table13242848193719>`. |
   +-----------+----------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------+

.. _subnet_tag_0001__table13242848193719:

.. table:: **Table 3** **tag** objects

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------+
   | Attribute       | Type            | Mandatory       | Description                                                                        |
   +=================+=================+=================+====================================================================================+
   | key             | String          | Yes             | -  Specifies the tag key.                                                          |
   |                 |                 |                 | -  Cannot be left blank.                                                           |
   |                 |                 |                 | -  Contain up to 128 characters (36 characters on the console).                    |
   |                 |                 |                 | -  Can contain only the following character types:                                 |
   |                 |                 |                 |                                                                                    |
   |                 |                 |                 |    -  Uppercase letters                                                            |
   |                 |                 |                 |    -  Lowercase letters                                                            |
   |                 |                 |                 |    -  Digits                                                                       |
   |                 |                 |                 |    -  Special characters, including hyphens (-), underscores (_), and at signs (@) |
   |                 |                 |                 |                                                                                    |
   |                 |                 |                 | -  The tag key of a VPC must be unique.                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------+
   | value           | String          | Yes             | -  Specifies the tag value.                                                        |
   |                 |                 |                 | -  Contain up to 255 characters (43 characters on the console).                    |
   |                 |                 |                 | -  Can contain only the following character types:                                 |
   |                 |                 |                 |                                                                                    |
   |                 |                 |                 |    -  Uppercase letters                                                            |
   |                 |                 |                 |    -  Lowercase letters                                                            |
   |                 |                 |                 |    -  Digits                                                                       |
   |                 |                 |                 |    -  Special characters, including hyphens (-), underscores (_), and at signs (@) |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------+

Example Request
---------------

-  Create a tag for a subnet. The key is **key1**, and the value is **value1**.

.. code-block:: text

   POST https://{Endpoint}/v2.0/{project_id}/subnets/{subnet_id}/tags

   {
       "tag": {
           "key": "key1",
           "value": "value1"
       }
   }

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
