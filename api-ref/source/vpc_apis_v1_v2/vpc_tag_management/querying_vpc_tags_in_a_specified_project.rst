:original_name: vpc_tag_0006.html

.. _vpc_tag_0006:

Querying VPC Tags in a Specified Project
========================================

Function
--------

This API is used to query all VPC tags of a tenant in a specified region.

URI
---

GET /v2.0/{project_id}/vpcs/tags

:ref:`Table 1 <vpc_tag_0006__table27380479>` describes the parameters.

.. _vpc_tag_0006__table27380479:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/{project_id}/vpcs/tags

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+----------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                           | Description             |
   +===========+================================================================+=========================+
   | tags      | Array of :ref:`tag <vpc_tag_0006__table1696410062019>` objects | Specifies the tag list. |
   +-----------+----------------------------------------------------------------+-------------------------+

.. _vpc_tag_0006__table1696410062019:

.. table:: **Table 3** Description of the **tag** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                        |
   +=======================+=======================+====================================================================================+
   | key                   | String                | Specifies the tag key.                                                             |
   |                       |                       |                                                                                    |
   |                       |                       | -  Cannot be left blank.                                                           |
   |                       |                       | -  Contain up to 128 characters (36 characters on the console).                    |
   |                       |                       | -  Can contain only the following character types:                                 |
   |                       |                       |                                                                                    |
   |                       |                       |    -  Uppercase letters                                                            |
   |                       |                       |    -  Lowercase letters                                                            |
   |                       |                       |    -  Digits                                                                       |
   |                       |                       |    -  Special characters, including hyphens (-), underscores (_), and at signs (@) |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | values                | Array of strings      | Specifies the tag value list.                                                      |
   |                       |                       |                                                                                    |
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
               "values": [
                   "value1",
                   "value2"
               ]
           },
           {
               "key": "key2",
               "values": [
                   "value1",
                   "value2"
               ]
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
