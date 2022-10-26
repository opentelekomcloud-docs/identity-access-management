:original_name: iam_02_0024.html

.. _iam_02_0024:

Querying the Password Policy
============================

Function
--------

This API is used to query the password policy.

URI
---

GET /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/password-policy

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

   +---------------------------------------------------------+--------+------------------+
   | Parameter                                               | Type   | Description      |
   +=========================================================+========+==================+
   | :ref:`password_policy <iam_02_0024__table321455061914>` | object | Password policy. |
   +---------------------------------------------------------+--------+------------------+

.. _iam_02_0024__table321455061914:

.. table:: **Table 4** password_policy

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

   GET https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/password-policy

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
