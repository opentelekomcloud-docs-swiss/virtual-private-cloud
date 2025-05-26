:original_name: vpc_api00_0010.html

.. _vpc_api00_0010:

Authentication
==============

Requests for calling an API can be authenticated using a token.

Token Authentication
--------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API. You can obtain a token by calling the `Obtaining User Token <https://docs.sc.otc.t-systems.com/api/iam/en-us_topic_0057845583.html>`__ API.

VPC is a project-level service. When you call the API, set **auth.scope** in the request body to **project**.

.. code-block::

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",   // IAM user name
                       "password": "********",  // IAM user password
                       "domain": {
                           "name": "domainname"  // Name of an IAM account
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxx"    // Project name
               }
           }
       }
   }

After a token is obtained, the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:

.. code-block:: text

   GETT https://{{endpoint}}/v3/auth/projects
   Content-Type: application/json
   X-Auth-Token: ABCDEFG....
