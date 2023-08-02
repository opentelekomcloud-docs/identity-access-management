:original_name: en-us_topic_0057845637.html

.. _en-us_topic_0057845637:

Creating a User
===============

Function
--------

This API is used to create a user under a domain.

URI
---

POST /v3/users

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.               |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Parameters in the request body

   .. table:: **Table 1** Description for the user format

      +---------------------------------------------------------+-----------+--------+-------------------+
      | Parameter                                               | Mandatory | Type   | Description       |
      +=========================================================+===========+========+===================+
      | :ref:`user <en-us_topic_0057845637__table470015453550>` | Yes       | Object | User information. |
      +---------------------------------------------------------+-----------+--------+-------------------+

   .. _en-us_topic_0057845637__table470015453550:

   .. table:: **Table 2** user

      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                        |
      +====================+=================+=================+====================================================================================================================================================================================+
      | name               | Yes             | String          | A username with 5 to 32 characters. The username can contain special characters, but only hyphens (-), underscores (_), and periods (.) are allowed. It cannot start with a digit. |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | domain_id          | No              | String          | ID of the domain where a user is located.                                                                                                                                          |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enabled            | No              | Boolean         | Whether a user is enabled.                                                                                                                                                         |
      |                    |                 |                 |                                                                                                                                                                                    |
      |                    |                 |                 | The value can be **true** or **false**. **true** indicates the user is enabled and **false** indicates the user is not enabled. The default value is **true**.                     |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password           | No              | String          | Password of the user. The password must meet the following requirements:                                                                                                           |
      |                    |                 |                 |                                                                                                                                                                                    |
      |                    |                 |                 | -  Can contain 6 to 32 characters. The system default minimum password length is 6 characters, and you can change the minimum password length.                                     |
      |                    |                 |                 | -  Must contain at least two of the following character types: uppercase letters, lowercase letters, digits, and special characters.                                               |
      |                    |                 |                 | -  Cannot be the username or the username spelled backwards.                                                                                                                       |
      |                    |                 |                 | -  Cannot contain the user's mobile phone number or email address.                                                                                                                 |
      |                    |                 |                 | -  Must comply with the password policies under **Account Settings**.                                                                                                              |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | default_project_id | No              | String          | Default project ID of a user.                                                                                                                                                      |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description        | No              | String          | Description of the user.                                                                                                                                                           |
      +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      1. Create the temporary file ${filename}.json based on the following template. ${filename} indicates the temporary file name, which is user-defined.
      {
          "user": {
              "default_project_id": "acf2ffabba974fae8f30378ffde2cfa6",
              "domain_id": "88b16b6440684467b8825d7d96e154d8",
              "enabled": true,
              "name": "jamesdoe",
              "password": "********"
          }
      }
      2. Run the following command under the directory storing the ${filename}.json file.
      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X POST -d @${filename}.json https://sample.domain.com/v3/users
      3. Run the following command under the directory of the ${filename}.json file to delete the ${filename}.json file.
      rm ${filename}.json

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== ============
   Parameter Mandatory Type        Description
   ========= ========= =========== ============
   user      Yes       JSON object User object.
   ========= ========= =========== ============

-  Description for the user format

   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                                                                    |
   +=====================+=================+=================+================================================================================================================================================================+
   | enabled             | Yes             | Boolean         | Whether a user is enabled.                                                                                                                                     |
   |                     |                 |                 |                                                                                                                                                                |
   |                     |                 |                 | The value can be **true** or **false**. **true** indicates the user is enabled and **false** indicates the user is not enabled. The default value is **true**. |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                  | Yes             | String          | User ID.                                                                                                                                                       |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id           | Yes             | String          | ID of the domain where a user is located.                                                                                                                      |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                | Yes             | String          | Username.                                                                                                                                                      |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links               | Yes             | JSON object     | User resource link.                                                                                                                                            |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_project_id  | No              | String          | Default project ID of a user.                                                                                                                                  |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password_expires_at | Yes             | String          | UTC when the password will expire. **null** indicates that the password will not expire.                                                                       |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "user": {
              "name": "jamesdoe",
              "links": {
                  "self": "https://sample.domain.com/v3/users/614d1d2fb86940faab8f350bf1b9dbac"
              },
              "domain_id": "88b16b6440684467b8825d7d96e154d8",
              "enabled": true,
              "id": "614d1d2fb86940faab8f350bf1b9dbac",
              "default_project_id": "acf2ffabba974fae8f30378ffde2cfa6",
              "password_expires_at": null
          }
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 201         | The user is successfully created.                                              |
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
| 409         | A resource conflict occurs.                                                    |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
