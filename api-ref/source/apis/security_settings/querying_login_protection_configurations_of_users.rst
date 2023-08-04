:original_name: iam_08_0014.html

.. _iam_08_0014:

Querying Login Protection Configurations of Users
=================================================

Function
--------

This API is provided for the administrator to query the login protection configurations of users.

URI
---

GET /v3.0/OS-USER/login-protects

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 2** Parameters in the response body

   +----------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                | Type                  | Description                                                                                                               |
   +==========================================================+=======================+===========================================================================================================================+
   | :ref:`login_protects <iam_08_0014__table12484173313717>` | Array of objects      | Login protection configurations.                                                                                          |
   |                                                          |                       |                                                                                                                           |
   |                                                          |                       | .. note::                                                                                                                 |
   |                                                          |                       |                                                                                                                           |
   |                                                          |                       |    The response only includes the login protection configurations of users for whom login protection has been configured. |
   +----------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

.. _iam_08_0014__table12484173313717:

.. table:: **Table 3** login_protects

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                             |
   +=======================+=======================+=========================================================================================================+
   | enabled               | Boolean               | Indicates whether login protection has been enabled for a user. The value can be **true** or **false**. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | user_id               | String                | User ID.                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | verification_method   | String                | Login authentication method of the user.                                                                |
   |                       |                       |                                                                                                         |
   |                       |                       | -  **email**: email verification code                                                                   |
   |                       |                       | -  **vmfa**: virtual MFA verification code                                                              |
   |                       |                       | -  **SMS**: SMS verification code                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-USER/login-protects

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "login_protects" : [
             {
               "user_id" : "75226081f43d4c628c4bb88cf32e9...",
               "enabled" : true,
               "verification_method" : "email"
               },
             {
               "user_id" : "16b26081f43d4c628c4bb88cf32e9...",
               "enabled" : true,
               "verification_method" : "vmfa"
               },
             {
               "user_id" : "56b26081f43d4c628c4bb88cf32e9...",
               "enabled" : true,
               "verification_method" : "sms"
               }
             {
               "user_id" : "08c16cb6c58010691f81c0028dd94...",
               "enabled" : false,
               "verification_method" : "none"
               }
          ]
   }

.. note::

   If login protection has never been configured for a user, you cannot use this API to obtain the login protection configuration of the user.

**Status code: 403**

Access denied.

-  Example 1

.. code-block::

   {
      "error_msg" : "You are not authorized to perform the requested action.",
      "error_code" : "IAM.0002"
    }

-  Example 2

.. code-block::

   {
      "error_msg" : "Policy doesn't allow %(actions)s to be performed.",
      "error_code" : "IAM.0003"
    }

**Status code: 404**

The requested resource cannot be found.

.. code-block::

   {
     "error_msg" : "Could not find %(target)s: %(target_id)s.",
     "error_code" : "IAM.0004"
   }

**Status code: 500**

Internal server error.

.. code-block::

   {
     "error_msg" : "An unexpected error prevented the server from fulfilling your request.",
     "error_code" : "IAM.0006"
   }

Status Codes
------------

=========== =======================================
Status Code Description
=========== =======================================
200         The request is successful.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =======================================
