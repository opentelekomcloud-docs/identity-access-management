:original_name: iam_08_0018.html

.. _iam_08_0018:

Unbinding a Virtual MFA Device
==============================

Function
--------

This API is used by the administrator to unbind a virtual MFA device from an IAM user, or used by an IAM user to unbind their own virtual MFA device.

URI
---

PUT /v3.0/OS-MFA/mfa-devices/unbind

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                               |
   +=================+=================+=================+===========================================================================================================================+
   | X-Auth-Token    | Yes             | String          | -  Administrator: Provide a token with **Security Administrator** permissions.                                            |
   |                 |                 |                 | -  User: Provide the token (no special permission requirements) of the user specified in **user_id** of the request body. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters in the request body

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                              |
   +=====================+=================+=================+==========================================================================================+
   | user_id             | Yes             | String          | ID of the user from whom you will unbind the MFA device.                                 |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | authentication_code | Yes             | String          | -  Administrator: Set this parameter to any value, because verification is not required. |
   |                     |                 |                 | -  IAM user: Enter the MFA verification code.                                            |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | serial_number       | Yes             | String          | Serial number of the MFA device.                                                         |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   PUT  https://sample.domain.com/v3.0/OS-MFA/mfa-devices/unbind

   {
     "user_id" : "09f99d8f6a001d4f1f01c00c31968...",
     "authentication_code" : "373658",
     "serial_number" : "iam:09f6bd6a96801de40f01c00c85691...:mfa/{device_name}"
   }

Example Response
----------------

None

Status Codes
------------

=========== =======================================================
Status Code Description
=========== =======================================================
204         The request is successful.
400         The request is invalid.
401         Authentication failed.
403         You do not have permission to perform this action.
404         The requested resource cannot be found.
409         A conflict occurs when the requested resource is saved.
500         A system error occurred.
=========== =======================================================
