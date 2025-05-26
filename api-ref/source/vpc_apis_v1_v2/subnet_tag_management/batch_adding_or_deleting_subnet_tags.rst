:original_name: subnet_tag_0004.html

.. _subnet_tag_0004:

Batch Adding or Deleting Subnet Tags
====================================

Function
--------

This API is used to add multiple tags to or delete multiple tags from a subnet at a time.

This API is idempotent.

If there are duplicate keys in the request body when you add tags, an error is reported.

During tag creation, duplicate keys are not allowed. If a key already exists in the database, its value will be overwritten by the new duplicate key.

During tag deletion, if some tags do not exist, the deletion is considered to be successful by default. The character set of the tags will not be checked. When you delete tags, the tag structure cannot be missing, and the key cannot be left blank or be an empty string.

URI
---

POST /v2.0/{project_id}/subnets/{subnet_id}/tags/action

:ref:`Table 1 <subnet_tag_0004__table27380479>` describes the parameters.

.. _subnet_tag_0004__table27380479:

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

   +-----------------+------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                             | Mandatory       | Description                                                                                              |
   +=================+==================================================================+=================+==========================================================================================================+
   | tags            | Array of :ref:`tag <subnet_tag_0004__table244913515593>` objects | Yes             | Specifies the **tag** object list. For details, see :ref:`Table 3 <subnet_tag_0004__table244913515593>`. |
   +-----------------+------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | action          | String                                                           | Yes             | Specifies the operation. Possible values are as follows:                                                 |
   |                 |                                                                  |                 |                                                                                                          |
   |                 |                                                                  |                 | -  **create**                                                                                            |
   |                 |                                                                  |                 | -  **delete**                                                                                            |
   +-----------------+------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------+

.. _subnet_tag_0004__table244913515593:

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

-  Batch create two tags for a subnet.

   .. code-block:: text

      POST https://{Endpoint}/v2.0/{project_id}/subnets/{subnet_id}/tags/action

      {
          "action": "create",
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

-  Batch delete two tags for a subnet.

   .. code-block:: text

      POST https://{Endpoint}/v2.0/{project_id}/subnets/{subnet_id}/tags/action

      {
          "action": "delete",
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
