:original_name: iam_08_0025.html

.. _iam_08_0025:

Sending a Welcome Email to a User
=================================

Function
--------

This API is used by the administrator to send a welcome email to a user.

.. note::

   The welcome email contains a one-time password-free login link, which can be used by the user to set a password. This API is recommended when you create a new user or reset the password of an existing user.

URI
---

POST /v3.0/OS-USER/users/{user_id}/welcome

.. table:: **Table 1** URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   Yes       String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Conent-Type  | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-token | Yes       | String | Token with **Security Administrator** permissions.    |
   +--------------+-----------+--------+-------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   POST https://sample.domain.com/v3.0/OS-USER/users/{user_id}/welcome

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
      "success"
   }

Status Codes
------------

=========== ===========================================
Status Code Description
=========== ===========================================
200         The email is sent to the user successfully.
400         The email address does not exist.
403         Access denied.
500         Internal system error.
=========== ===========================================

Error Codes
-----------

For details, see :ref:`Error Codes <iam_02_0006>`.
