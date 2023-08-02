:original_name: iam_08_0013.html

.. _iam_08_0013:

Querying the MFA Device Information of a User
=============================================

Function
--------

This API can be used by the administrator to query the MFA device information of a specified user or used by a user to query their MFA device information.

URI
---

GET /v3.0/OS-MFA/users/{user_id}/virtual-mfa-device

.. table:: **Table 1** URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   Yes       String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator** permissions is required if the administrator is requesting to query the MFA device information of a specified user. |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | If a user is requesting to query their MFA device information, the user token (no special permission requirements) of the user is required.                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Parameters in the response body

   +--------------------------------------------------------------+--------+---------------------------------+
   | Parameter                                                    | Type   | Description                     |
   +==============================================================+========+=================================+
   | :ref:`virtual_mfa_device <iam_08_0013__table64771918103713>` | object | Virtual MFA device information. |
   +--------------------------------------------------------------+--------+---------------------------------+

.. _iam_08_0013__table64771918103713:

.. table:: **Table 4** virtual_mfa_device

   ============= ====== =================================
   Parameter     Type   Description
   ============= ====== =================================
   serial_number String Virtual MFA device serial number.
   user_id       String User ID.
   ============= ====== =================================

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-MFA/users/{user_id}/virtual-mfa-device

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "virtual_mfa_device" :
       {
         "user_id" : "16b26081f43d4c628c4bb88cf32e9...",
         "serial_number" : "iam/mfa/16b26081f43d4c628c4bb88cf32e9..."
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
