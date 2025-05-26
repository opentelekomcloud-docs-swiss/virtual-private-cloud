:original_name: vpc_tag_0002.html

.. _vpc_tag_0002:

Querying VPC Tags
=================

Function
--------

This API is used to query tags of a specified VPC.

URI
---

GET /v2.0/{project_id}/vpcs/{vpc_id}/tags

:ref:`Table 1 <vpc_tag_0002__table27380479>` describes the parameters.

.. _vpc_tag_0002__table27380479:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | vpc_id     | Yes       | Specifies the VPC ID that uniquely identifies the VPC.                                                                    |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/{project_id}/vpcs/{vpc_id}/tags

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+-----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                            | Description                                                                                             |
   +===========+=================================================================+=========================================================================================================+
   | tags      | Array of :ref:`tag <vpc_tag_0002__table13242848193719>` objects | Specifies the **tag** object list. For details, see :ref:`Table 3 <vpc_tag_0002__table13242848193719>`. |
   +-----------+-----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _vpc_tag_0002__table13242848193719:

.. table:: **Table 3** **tag** objects

   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                                        |
   +=======================+=======================+====================================================================================+
   | key                   | String                | -  Specifies the tag key.                                                          |
   |                       |                       | -  Cannot be left blank.                                                           |
   |                       |                       | -  Contain up to 128 characters (36 characters on the console).                    |
   |                       |                       | -  Can contain only the following character types:                                 |
   |                       |                       |                                                                                    |
   |                       |                       |    -  Uppercase letters                                                            |
   |                       |                       |    -  Lowercase letters                                                            |
   |                       |                       |    -  Digits                                                                       |
   |                       |                       |    -  Special characters, including hyphens (-), underscores (_), and at signs (@) |
   |                       |                       |                                                                                    |
   |                       |                       | -  The tag key of a VPC must be unique.                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | value                 | String                | -  Specifies the tag value.                                                        |
   |                       |                       | -  Contain up to 255 characters (43 characters on the console).                    |
   |                       |                       | -  Can contain only the following character types:                                 |
   |                       |                       |                                                                                    |
   |                       |                       |    -  Uppercase letters                                                            |
   |                       |                       |    -  Lowercase letters                                                            |
   |                       |                       |    -  Digits                                                                       |
   |                       |                       |    -  Special characters, including hyphens (-), underscores (_), and at signs (@) |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "tags": [
           {
               "key": "key1",
               "value": "value1"
           },
           {
               "key": "key2",
               "value": "value3"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
