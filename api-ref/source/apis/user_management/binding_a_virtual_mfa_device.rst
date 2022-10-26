:original_name: iam_08_0017.html

.. _iam_08_0017:

Binding a Virtual MFA Device
============================

Function
--------

This API is provided for IAM users to bind a virtual MFA device.

URI
---

PUT /v3.0/OS-MFA/mfa-devices/bind

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                |
   +==============+===========+========+============================================================================================================================+
   | X-Auth-token | Yes       | String | Token (no special permission requirements) of the IAM user corresponding to the **user_id** specified in the request body. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters in the request body

   +----------------------------+-----------+--------+--------------------------------------------------------------+
   | Parameter                  | Mandatory | Type   | Description                                                  |
   +============================+===========+========+==============================================================+
   | user_id                    | Yes       | String | ID of the user to whom you will bind the virtual MFA device. |
   +----------------------------+-----------+--------+--------------------------------------------------------------+
   | serial_number              | Yes       | String | Serial number of the virtual MFA device.                     |
   +----------------------------+-----------+--------+--------------------------------------------------------------+
   | authentication_code_first  | Yes       | String | Verification code 1.                                         |
   +----------------------------+-----------+--------+--------------------------------------------------------------+
   | authentication_code_second | Yes       | String | Verification code 2.                                         |
   +----------------------------+-----------+--------+--------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-MFA/mfa-devices/bind

   {
     "user_id" : "09f99d8f6a001d4f1f01c00c31968...",
     "authentication_code_first" : "977931",
     "authentication_code_second" : "527347",
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
