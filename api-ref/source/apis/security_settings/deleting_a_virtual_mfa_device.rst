:original_name: iam_08_0020.html

.. _iam_08_0020:

Deleting a Virtual MFA Device
=============================

Function
--------

This API is provided for the administrator to delete their own virtual MFA device.

URI
---

DELETE /v3.0/OS-MFA/virtual-mfa-devices

.. table:: **Table 1** Query parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                     |
   +===============+===========+========+=================================================================================================+
   | user_id       | Yes       | String | ID of the user whose virtual MFA device is to be deleted, that is, the administrator's user ID. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------+
   | serial_number | Yes       | String | Serial number of the virtual MFA device.                                                        |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-auth-Token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://sample.domain.com/v3.0/OS-MFA/virtual-mfa-devices?user_id=09f6bd85fc801de41f0cc00ce9172...&serial_number=iam:09f6bd6a96801de40f01c00c85691...:mfa/{device_name}

Example Response
----------------

None

Status Codes
------------

=========== ==================================================
Status Code Description
=========== ==================================================
204         The request is successful.
401         Authentication failed.
403         You do not have permission to perform this action.
500         A system error occurred.
=========== ==================================================
