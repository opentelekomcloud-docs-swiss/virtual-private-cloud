:original_name: subnet_tag_0002.html

.. _subnet_tag_0002:

Querying Subnet Tags
====================

Function
--------

This API is used to query tags of a specified subnet.

URI
---

GET /v2.0/{project_id}/subnets/{subnet_id}/tags

:ref:`Table 1 <subnet_tag_0002__table27380479>` describes the parameters.

.. _subnet_tag_0002__table27380479:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Mandatory             | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | project_id            | Yes                   | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
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

   GET https://{Endpoint}/v2.0/{project_id}/subnets/{subnet_id}/tags

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+--------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                               | Description                                                                                                |
   +===========+====================================================================+============================================================================================================+
   | tags      | Array of :ref:`tag <subnet_tag_0002__table13242848193719>` objects | Specifies the **tag** object list. For details, see :ref:`Table 3 <subnet_tag_0002__table13242848193719>`. |
   +-----------+--------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

.. _subnet_tag_0002__table13242848193719:

.. table:: **Table 3** **tag** objects

   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                         |
   +=======================+=======================+=====================================================================+
   | key                   | String                | -  Specifies the tag key.                                           |
   |                       |                       | -  Cannot be left blank.                                            |
   |                       |                       | -  Can contain a maximum of 36 characters.                          |
   |                       |                       | -  Can contain only the following character types:                  |
   |                       |                       |                                                                     |
   |                       |                       |    -  Uppercase letters                                             |
   |                       |                       |    -  Lowercase letters                                             |
   |                       |                       |    -  Digits                                                        |
   |                       |                       |    -  Special characters, including hyphens (-) and underscores (_) |
   |                       |                       |                                                                     |
   |                       |                       | -  The tag key of a VPC must be unique.                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | value                 | String                | -  Specifies the tag value.                                         |
   |                       |                       | -  Can contain a maximum of 43 characters.                          |
   |                       |                       | -  Can contain only the following character types:                  |
   |                       |                       |                                                                     |
   |                       |                       |    -  Uppercase letters                                             |
   |                       |                       |    -  Lowercase letters                                             |
   |                       |                       |    -  Digits                                                        |
   |                       |                       |    -  Special characters, including hyphens (-) and underscores (_) |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

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
