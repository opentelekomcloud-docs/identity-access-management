:original_name: iam_08_0019.html

.. _iam_08_0019:

Creating a Virtual MFA Device
=============================

Function
--------

This API is provided for IAM users to create a virtual MFA device.

URI
---

POST /v3.0/OS-MFA/virtual-mfa-devices

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                |
   +==============+===========+========+============================================================================================================================+
   | X-Auth-Token | Yes       | String | Token (no special permission requirements) of the IAM user corresponding to the **user_id** specified in the request body. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters in the request body

   +--------------------------------------------------------------+-----------+--------+-------------------------+
   | Parameter                                                    | Mandatory | Type   | Description             |
   +==============================================================+===========+========+=========================+
   | :ref:`virtual_mfa_device <iam_08_0019__table12820145444514>` | Yes       | object | MFA device information. |
   +--------------------------------------------------------------+-----------+--------+-------------------------+

.. _iam_08_0019__table12820145444514:

.. table:: **Table 3** virtual_mfa_device

   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                             |
   +=================+=================+=================+=========================================================+
   | name            | Yes             | String          | Device name.                                            |
   |                 |                 |                 |                                                         |
   |                 |                 |                 | Minimum length: 1 character                             |
   |                 |                 |                 |                                                         |
   |                 |                 |                 | Maximum length: 64 characters                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | user_id         | Yes             | String          | ID of the user for whom you will create the MFA device. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Parameters in the response body

   +------------------------------------------------------------+--------+-------------------------+
   | Parameter                                                  | Type   | Description             |
   +============================================================+========+=========================+
   | :ref:`virtual_mfa_device <iam_08_0019__table782775454511>` | object | MFA device information. |
   +------------------------------------------------------------+--------+-------------------------+

.. _iam_08_0019__table782775454511:

.. table:: **Table 5** virtual_mfa_device

   +--------------------+--------+-----------------------------------------------------------------------------+
   | Parameter          | Type   | Description                                                                 |
   +====================+========+=============================================================================+
   | serial_number      | String | Serial number of the MFA device.                                            |
   +--------------------+--------+-----------------------------------------------------------------------------+
   | base32_string_seed | String | Base32 seed, which a third-party system can use to generate a CAPTCHA code. |
   +--------------------+--------+-----------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://sample.domain.com/v3.0/OS-MFA/virtual-mfa-devices

   {
     "virtual_mfa_device" : {
       "name" : "{device_name}",
       "user_id" : "09f99d8f6a001d4f1f01c00c31968..."
     }
   }

Example Response
----------------

**Status code: 201**

The request is successful.

.. code-block::

   {
     "virtual_mfa_device": {
       "serial_number": "iam:09f6bd6a96801de40f01c00c85691...:mfa/{device_name}",
       "base32_string_seed": "{string}"
     }
   }

Status Codes
------------

=========== =======================================================
Status Code Description
=========== =======================================================
201         The request is successful.
400         The request is invalid.
401         Authentication failed.
403         You do not have permission to perform this action.
409         A conflict occurs when the requested resource is saved.
500         A system error occurred.
=========== =======================================================
