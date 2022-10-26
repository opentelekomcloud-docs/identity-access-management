:original_name: iam_08_0012.html

.. _iam_08_0012:

Querying MFA Device Information of Users
========================================

Function
--------

This API is provided for the administrator to query the MFA device information of users.

URI
---

GET /v3.0/OS-MFA/virtual-mfa-devices

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

   +-------------------------------------------------------------+------------------+---------------------------------+
   | Parameter                                                   | Type             | Description                     |
   +=============================================================+==================+=================================+
   | :ref:`virtual_mfa_devices <iam_08_0012__table578318529362>` | Array of objects | Virtual MFA device information. |
   +-------------------------------------------------------------+------------------+---------------------------------+

.. _iam_08_0012__table578318529362:

.. table:: **Table 3** virtual_mfa_devices

   ============= ====== =================================
   Parameter     Type   Description
   ============= ====== =================================
   serial_number String Virtual MFA device serial number.
   user_id       String User ID.
   ============= ====== =================================

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-MFA/virtual-mfa-devices

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "virtual_mfa_devices" : [
             {
                 "user_id" : "16b26081f43d4c628c4bb88cf32e9...",
                 "serial_number" : "iam/mfa/16b26081f43d4c628c4bb88cf32e9..."
               },
              {
                 "user_id" : "47026081f43d4c628c4bb88cf32e9...",
                 "serial_number" : "iam/mfa/75226081f43d4c628c4bb88cf32e9..."
                }
             ]
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
