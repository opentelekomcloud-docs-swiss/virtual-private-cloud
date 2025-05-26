:original_name: eip_tag_0002.html

.. _eip_tag_0002:

Querying EIP Tags
=================

Function
--------

This API is used to query tags of a specified EIP.

URI
---

GET /v2.0/{project_id}/publicips/{publicip_id}/tags

:ref:`Table 1 <eip_tag_0002__table450964213214>` describes the parameters.

.. _eip_tag_0002__table450964213214:

.. table:: **Table 1** Parameter description

   +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Description                                                                                                               |
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

      GET https://{Endpoint}/v2.0/{project_id}/publicips/{publicip_id}/tags

Response Message
----------------

-  Response parameter

   .. table:: **Table 2** Response parameter

      +-----------+-----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
      | Parameter | Type                                                            | Description                                                                                             |
      +===========+=================================================================+=========================================================================================================+
      | tags      | Array of :ref:`tag <eip_tag_0002__table13242848193719>` objects | Specifies the **tag** object list. For details, see :ref:`Table 3 <eip_tag_0002__table13242848193719>`. |
      +-----------+-----------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

   .. _eip_tag_0002__table13242848193719:

   .. table:: **Table 3** **tag** objects

      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | Attribute             | Type                  | Description                                                                        |
      +=======================+=======================+====================================================================================+
      | key                   | String                | -  Specifies the tag key.                                                          |
      |                       |                       | -  Cannot be left blank.                                                           |
      |                       |                       | -  Can contain a maximum of 36 characters.                                         |
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
      |                       |                       | -  Can contain a maximum of 43 characters.                                         |
      |                       |                       | -  Can contain only the following character types:                                 |
      |                       |                       |                                                                                    |
      |                       |                       |    -  Uppercase letters                                                            |
      |                       |                       |    -  Lowercase letters                                                            |
      |                       |                       |    -  Digits                                                                       |
      |                       |                       |    -  Special characters, including hyphens (-), underscores (_), and at signs (@) |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+

-  Example response

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
