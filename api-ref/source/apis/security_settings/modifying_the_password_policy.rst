:original_name: iam_02_0023.html

.. _iam_02_0023:

Modifying the Password Policy
=============================

Function
--------

This API is provided for the administrator to modify the password policy.

URI
---

PUT /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/password-policy

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

   +---------------------------------------------------------+-----------+--------+------------------+
   | Parameter                                               | Mandatory | Type   | Description      |
   +=========================================================+===========+========+==================+
   | :ref:`password_policy <iam_02_0023__table228513912190>` | Yes       | object | Password policy. |
   +---------------------------------------------------------+-----------+--------+------------------+

.. _iam_02_0023__table228513912190:

.. table:: **Table 4** password_policy

   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | Parameter                             | Mandatory | Type    | Description                                                                                                      |
   +=======================================+===========+=========+==================================================================================================================+
   | maximum_consecutive_identical_chars   | No        | Integer | Maximum number of times that a character is allowed to consecutively present in a password. Value range: 0-32.   |
   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | minimum_password_age                  | No        | Integer | Minimum period (minutes) after which users are allowed to make a password change. Value range: 0-1440.           |
   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | minimum_password_length               | No        | Integer | Minimum number of characters that a password must contain. Value range: 6-32.                                    |
   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | number_of_recent_passwords_disallowed | No        | Integer | Number of previously used passwords that are not allowed. Value range: 0-10.                                     |
   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | password_not_username_or_invert       | No        | Boolean | Indicates whether the password can be the username or the username spelled backwards.                            |
   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | password_validity_period              | No        | Integer | Password validity period (days). Value range: 0-180. Value **0** indicates that this requirement does not apply. |
   +---------------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 5** Parameters in the response body

   +--------------------------------------------------------+--------+------------------+
   | Parameter                                              | Type   | Description      |
   +========================================================+========+==================+
   | :ref:`password_policy <iam_02_0023__table73081394194>` | object | Password policy. |
   +--------------------------------------------------------+--------+------------------+

.. _iam_02_0023__table73081394194:

.. table:: **Table 6** password_policy

   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | Parameter                             | Type    | Description                                                                                 |
   +=======================================+=========+=============================================================================================+
   | maximum_consecutive_identical_chars   | Integer | Maximum number of times that a character is allowed to consecutively present in a password. |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | maximum_password_length               | Integer | Maximum number of characters that a password can contain.                                   |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | minimum_password_age                  | Integer | Minimum period (minutes) after which users are allowed to make a password change.           |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | minimum_password_length               | Integer | Minimum number of characters that a password must contain.                                  |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | number_of_recent_passwords_disallowed | Integer | Number of previously used passwords that are not allowed.                                   |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | password_not_username_or_invert       | Boolean | Indicates whether the password can be the username or the username spelled backwards.       |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | password_requirements                 | String  | Characters that a password must contain.                                                    |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+
   | password_validity_period              | Integer | Password validity period (days).                                                            |
   +---------------------------------------+---------+---------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/password_policy

   {
     "password_policy" : {
       "minimum_password_length" : 6,
       "number_of_recent_passwords_disallowed" : 2,
       "minimum_password_age" : 20,
       "password_validity_period" : 60,
       "maximum_consecutive_identical_chars" : 3,
       "password_not_username_or_invert" : false
     }
   }

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "password_policy" : {
       "password_requirements" : "A password must contain at least two of the following: uppercase letters, lowercase letters, digits, and special characters.",
       "minimum_password_age" : 20,
       "minimum_password_length" : 8,
       "maximum_password_length" : 32,
       "number_of_recent_passwords_disallowed" : 2,
       "password_validity_period" : 60,
       "maximum_consecutive_identical_chars" : 3,
       "password_not_username_or_invert" : true
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
