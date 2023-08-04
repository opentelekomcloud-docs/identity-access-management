:original_name: iam_08_0016.html

.. _iam_08_0016:

Querying the Login Protection Configuration of a User
=====================================================

Function
--------

This API can be used by the administrator to query the login protection configuration of a specified user or used by a user to query their login protection configuration.

URI
---

GET /v3.0/OS-USER/users/{user_id}/login-protect

.. table:: **Table 1** URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   Yes       String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator** permissions is required if the administrator is requesting to query the login protection configuration of a specified user. |
   |                 |                 |                 |                                                                                                                                                                     |
   |                 |                 |                 | If a user is requesting to query their login protection configuration, the user token (no special permission requirements) of the user is required.                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Parameters in the response body

   +--------------------------------------------------------+--------+---------------------------------+
   | Parameter                                              | Type   | Description                     |
   +========================================================+========+=================================+
   | :ref:`login_protect <iam_08_0016__table7414450103712>` | object | Login protection configuration. |
   +--------------------------------------------------------+--------+---------------------------------+

.. _iam_08_0016__table7414450103712:

.. table:: **Table 4** login_protect

   +---------------------+---------+---------------------------------------------------------------------------------------------------------+
   | Parameter           | Type    | Description                                                                                             |
   +=====================+=========+=========================================================================================================+
   | enabled             | Boolean | Indicates whether login protection has been enabled for a user. The value can be **true** or **false**. |
   +---------------------+---------+---------------------------------------------------------------------------------------------------------+
   | user_id             | String  | User ID.                                                                                                |
   +---------------------+---------+---------------------------------------------------------------------------------------------------------+
   | verification_method | String  | Login authentication method of the user.                                                                |
   +---------------------+---------+---------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-USER/users/{user_id}/login-protect

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "login_protect" : {
       "user_id" : "16b26081f43d4c628c4bb88cf32e9...",
       "enabled" : true,
       "verification_method" : "vmfa"
     }
   }

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

.. note::

   If login protection has never been configured for a user, you cannot use this API to obtain the login protection configuration of the user. Otherwise, the error code IAM.0004 will be returned.

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
