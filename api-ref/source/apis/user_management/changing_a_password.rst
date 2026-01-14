:original_name: en-us_topic_0057845653.html

.. _en-us_topic_0057845653:

Changing a Password
===================

Function
--------

This API is used to change the password for a user.

URI
---

-  URI format

   POST /v3/users/{user_id}/password

-  URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   Yes       String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token.                                  |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Parameters in the request body

   +-------------------------------------------------------------------------+-----------+--------+-----------------------+
   | Parameter                                                               | Mandatory | Type   | Description           |
   +=========================================================================+===========+========+=======================+
   | :ref:`user <en-us_topic_0057845653__en-us_topic_0026585112_li29035785>` | Yes       | Object | IAM user information. |
   +-------------------------------------------------------------------------+-----------+--------+-----------------------+

-  .. _en-us_topic_0057845653__en-us_topic_0026585112_li29035785:

   user

   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                          |
   +===================+=================+=================+======================================================================================================================================+
   | original_password | Yes             | String          | Original password of a user.                                                                                                         |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | password          | Yes             | String          | User password after the change. The password must meet the following requirements:                                                   |
   |                   |                 |                 |                                                                                                                                      |
   |                   |                 |                 | -  Can contain 6 to 32 characters. The default minimum password length is 6 characters.                                              |
   |                   |                 |                 | -  Must contain at least two of the following character types: uppercase letters, lowercase letters, digits, and special characters. |
   |                   |                 |                 | -  Cannot be the username or the username spelled backwards.                                                                         |
   |                   |                 |                 | -  Cannot contain the user's mobile phone number or email address.                                                                   |
   |                   |                 |                 | -  Must meet the requirements of the password policy configured on the account settings page.                                        |
   |                   |                 |                 | -  Must be different from the old password.                                                                                          |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      1. Create the temporary file ${filename}.json based on the following template. ${filename} indicates the temporary file name, which is user-defined.
      {
          "user": {
              "password": "********",
              "original_password": "********"
          }
      }
      2. Run the following command under the directory storing the ${filename}.json file.
      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X POST -d @${filename}.json https://sample.domain.com/v3/users/2c1c6c54e59141b889c99e6fada5f19f/password
      3. Run the following command under the directory of the ${filename}.json file to delete the ${filename}.json file.
      rm ${filename}.json

Response Parameters
-------------------

None

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 204         | The password is changed successfully.                                          |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                        |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
