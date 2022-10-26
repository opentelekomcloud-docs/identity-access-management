:original_name: iam_08_0021.html

.. _iam_08_0021:

Modifying the Login Protection Configuration of a User
======================================================

Function
--------

This API is provided for the administrator to modify the login protection configuration of a user.

URI
---

PUT /v3.0/OS-USER/users/{user_id}/login-protect

.. table:: **Table 1** URI parameters

   +-----------+-----------+--------+------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                            |
   +===========+===========+========+========================================================================+
   | user_id   | Yes       | String | ID of the user whose login protection configuration is to be modified. |
   +-----------+-----------+--------+------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-Auth-token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

.. table:: **Table 3** Parameters in the request body

   +---------------------------------------------------------+-----------+--------+---------------------------------+
   | Parameter                                               | Mandatory | Type   | Description                     |
   +=========================================================+===========+========+=================================+
   | :ref:`login_protect <iam_08_0021__table14291172683815>` | Yes       | object | Login protection configuration. |
   +---------------------------------------------------------+-----------+--------+---------------------------------+

.. _iam_08_0021__table14291172683815:

.. table:: **Table 4** Login_project

   +---------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type    | Description                                                                                               |
   +=====================+===========+=========+===========================================================================================================+
   | enabled             | Yes       | Boolean | Indicates whether login protection has been enabled for the user. The value can be **true** or **false**. |
   +---------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------+
   | verification_method | Yes       | String  | Login authentication method of the user. Options: **sms**, **email**, and **vmfa**.                       |
   +---------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Parameters in the response body

   +---------------------------------------------------------+--------+---------------------------------+
   | Parameter                                               | Type   | Description                     |
   +=========================================================+========+=================================+
   | :ref:`login_protect <iam_08_0021__table13297726203815>` | object | Login protection configuration. |
   +---------------------------------------------------------+--------+---------------------------------+

.. _iam_08_0021__table13297726203815:

.. table:: **Table 6** login_protect

   +---------------------+---------+-----------------------------------------------------------------------------------------------------------+
   | Parameter           | Type    | Description                                                                                               |
   +=====================+=========+===========================================================================================================+
   | user_id             | String  | User ID.                                                                                                  |
   +---------------------+---------+-----------------------------------------------------------------------------------------------------------+
   | enabled             | Boolean | Indicates whether login protection has been enabled for the user. The value can be **true** or **false**. |
   +---------------------+---------+-----------------------------------------------------------------------------------------------------------+
   | verification_method | String  | Login authentication method of the user. Options: **sms**, **email**, and **vmfa**.                       |
   +---------------------+---------+-----------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-USER/users/{user_id}/login-protect
   {
     "login_protect" : {
       "enabled" : true,
       "verification_method" : "vmfa"
     }
   }

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "login_protect" : {
       "user_id": "16b26081f43d4c628c4bb88cf32e9...",
       "enabled" : true,
       "verification_method" : "vmfa"
     }
   }

Status Codes
------------

=========== ==================================================
Status Code Description
=========== ==================================================
200         The request is successful.
400         The request is invalid.
401         Authentication failed.
403         You do not have permission to perform this action.
404         The requested resource cannot be found.
500         A system error occurred.
=========== ==================================================
