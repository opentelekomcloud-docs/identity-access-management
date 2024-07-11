:original_name: iam_02_0025.html

.. _iam_02_0025:

Modifying the Login Authentication Policy
=========================================

Function
--------

This API is provided for the administrator to modify the login authentication policy.

URI
---

PUT /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/login-policy

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

.. table:: **Table 3** Parameters in the request body

   +-------------------------------------------------------+-----------+--------+------------------------------+
   | Parameter                                             | Mandatory | Type   | Description                  |
   +=======================================================+===========+========+==============================+
   | :ref:`login_policy <iam_02_0025__table1671401152018>` | Yes       | object | Login authentication policy. |
   +-------------------------------------------------------+-----------+--------+------------------------------+

.. _iam_02_0025__table1671401152018:

.. table:: **Table 4** login_policy

   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory | Type    | Description                                                                                                                                                             |
   +============================+===========+=========+=========================================================================================================================================================================+
   | account_validity_period    | No        | Integer | Validity period (days) to disable users if they have not logged in within the period. Value range: 0-240. If this parameter is set to **0**, no users will be disabled. |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | custom_info_for_login      | No        | String  | Custom information that will be displayed upon successful login.                                                                                                        |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lockout_duration           | No        | Integer | Duration (minutes) to lock users out. Value range: 15-30.                                                                                                               |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | login_failed_times         | No        | Integer | Number of unsuccessful login attempts to lock users out. Value range: 3-10.                                                                                             |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period_with_login_failures | No        | Integer | Period (minutes) to count the number of unsuccessful login attempts. Value range: 15-60.                                                                                |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | session_timeout            | No        | Integer | Session timeout (minutes) that will apply if you or users created using your account do not perform any operations within a specific period. Value range: 15-1440.      |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | show_recent_login_info     | No        | Boolean | Indicates whether to display last login information upon successful login. The value can be **true** or **false**.                                                      |
   +----------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 5** Parameters in the response body

   +------------------------------------------------------+--------+------------------------------+
   | Parameter                                            | Type   | Description                  |
   +======================================================+========+==============================+
   | :ref:`login_policy <iam_02_0025__table157388112015>` | object | Login authentication policy. |
   +------------------------------------------------------+--------+------------------------------+

.. _iam_02_0025__table157388112015:

.. table:: **Table 6** login_policy

   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type    | Description                                                                                                                                  |
   +============================+=========+==============================================================================================================================================+
   | account_validity_period    | Integer | Validity period (days) to disable users if they have not logged in within the period.                                                        |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | custom_info_for_login      | String  | Custom information that will be displayed upon successful login.                                                                             |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | lockout_duration           | Integer | Duration (minutes) to lock users out.                                                                                                        |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | login_failed_times         | Integer | Number of unsuccessful login attempts to lock users out.                                                                                     |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | period_with_login_failures | Integer | Period (minutes) to count the number of unsuccessful login attempts.                                                                         |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | session_timeout            | Integer | Session timeout (minutes) that will apply if you or users created using your account do not perform any operations within a specific period. |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | show_recent_login_info     | Boolean | Indicates whether to display last login information upon successful login.                                                                   |
   +----------------------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/login-policy

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

**Status code: 400**

The request body is abnormal.

-  Example 1

.. code-block::

   {
      "error_msg" : "'%(key)s' is a required property.",
      "error_code" : "IAM.0072"
    }

-  Example 2

.. code-block::

   {
      "error_msg" : "Invalid input for field '%(key)s'. The value is '%(value)s'.",
      "error_code" : "IAM.0073"
    }

**Status code: 403**

Access denied.

.. code-block::

   {
     "error_msg" : "You are not authorized to perform the requested action.",
     "error_code" : "IAM.0002"
   }

**Status code: 500**

The system is abnormal.

.. code-block::

   {
     "error_msg" : "An unexpected error prevented the server from fulfilling your request.",
     "error_code" : "IAM.0006"
   }

Status Codes
------------

=========== =============================
Status Code Description
=========== =============================
200         The request is successful.
400         The request body is abnormal.
401         Authentication failed.
403         Access denied.
500         The system is abnormal.
=========== =============================
