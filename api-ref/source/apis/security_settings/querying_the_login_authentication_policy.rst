:original_name: iam_02_0026.html

.. _iam_02_0026:

Querying the Login Authentication Policy
========================================

Function
--------

This API is used to query the login authentication policy.

URI
---

GET /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/login-policy

.. table:: **Table 1** URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   domain_id Yes       String Domain ID.
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Parameters in the response body

   +-------------------------------------------------------+--------+------------------------------+
   | Parameter                                             | Type   | Description                  |
   +=======================================================+========+==============================+
   | :ref:`login_policy <iam_02_0026__table1311331112013>` | object | Login authentication policy. |
   +-------------------------------------------------------+--------+------------------------------+

.. _iam_02_0026__table1311331112013:

.. table:: **Table 4** login_policy

   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type    | Description                                                                                                                                                                                                                                                  |
   +============================+=========+==============================================================================================================================================================================================================================================================+
   | account_validity_period    | Integer | Validity period (days) to disable users if they have not logged in within the period. Value range: 0-240. Validity period (days) to disable users if they have not logged in within the period If this parameter is set to **0**, no users will be disabled. |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | custom_info_for_login      | String  | Custom information that will be displayed upon successful login.                                                                                                                                                                                             |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lockout_duration           | Integer | Duration (minutes) to lock users out.                                                                                                                                                                                                                        |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | login_failed_times         | Integer | Number of unsuccessful login attempts to lock users out.                                                                                                                                                                                                     |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period_with_login_failures | Integer | Period (minutes) to count the number of unsuccessful login attempts.                                                                                                                                                                                         |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | session_timeout            | Integer | Session timeout (minutes) that will apply if you or users created using your account do not perform any operations within a specific period.                                                                                                                 |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | show_recent_login_info     | Boolean | Indicates whether to display last login information upon successful login.                                                                                                                                                                                   |
   +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/login-policy

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "login_policy" : {
       "custom_info_for_login" : "",
       "period_with_login_failures" : 15,
       "lockout_duration" : 15,
       "account_validity_period" : 99,
       "login_failed_times" : 3,
       "session_timeout" : 16,
       "show_recent_login_info" : true
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
