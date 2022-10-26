:original_name: en-us_topic_0057845561.html

.. _en-us_topic_0057845561:

Querying Users in a User Group
==============================

Function
--------

This API is used to query users in a user group.

URI
---

-  URI format

   GET /v3/groups/{group_id}/users

-  URI parameters

   ========= ========= ====== ===================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================
   group_id  Yes       String ID of a user group.
   ========= ========= ====== ===================

-  Query parameters

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                                                                |
   +=====================+=================+=================+============================================================================================================================================================+
   | domain_id           | No              | String          | ID of the domain to which a user group belongs.                                                                                                            |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                | No              | String          | Name of a user. The maximum length is 64 characters.                                                                                                       |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enabled             | No              | String          | Whether a user is enabled. The value can be **true** or **false**. **true** indicates the user is enabled and **false** indicates the user is not enabled. |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password_expires_at | No              | String          | Password expiration time. The format is **password_expires_at=**\ *operator*\ **:**\ *timestamp*.                                                          |
   |                     |                 |                 |                                                                                                                                                            |
   |                     |                 |                 | Example:                                                                                                                                                   |
   |                     |                 |                 |                                                                                                                                                            |
   |                     |                 |                 | .. code-block::                                                                                                                                            |
   |                     |                 |                 |                                                                                                                                                            |
   |                     |                 |                 |    password_expires_at=lt:2016-12-08T22:02:00Z                                                                                                             |
   |                     |                 |                 |                                                                                                                                                            |
   |                     |                 |                 | -  The value of **operator** can be **lt**, **lte**, **gt**, **gte**, **eq**, or **neq**.                                                                  |
   |                     |                 |                 |                                                                                                                                                            |
   |                     |                 |                 |    -  **lt**: The expiration time is earlier than *timestamp*.                                                                                             |
   |                     |                 |                 |    -  **lte**: The expiration time is earlier than or equal to *timestamp*.                                                                                |
   |                     |                 |                 |    -  **gt**: The expiration time is later than *timestamp*.                                                                                               |
   |                     |                 |                 |    -  **gte**: The expiration time is equal to or later than *timestamp*.                                                                                  |
   |                     |                 |                 |    -  **eq**: The expiration time is equal to *timestamp*.                                                                                                 |
   |                     |                 |                 |    -  **neq**: The expiration time is not equal to *timestamp*.                                                                                            |
   |                     |                 |                 |                                                                                                                                                            |
   |                     |                 |                 | -  The **timestamp** format is **YYYY-MM-DDTHH:mm:ssZ**.                                                                                                   |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/groups/00007111583e457389b0d4252643181b/users

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== ===================================
   Parameter Mandatory Type        Description
   ========= ========= =========== ===================================
   links     Yes       JSON object User resource link of a user group.
   users     Yes       JSONArray   List of users in a user group.
   ========= ========= =========== ===================================

-  Description for the user format

   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type        | Description                                                                                                             |
   +=====================+===========+=============+=========================================================================================================================+
   | description         | Yes       | String      | Description for a user.                                                                                                 |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | domain_id           | Yes       | String      | ID of the tenant that the user belongs to.                                                                              |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | enabled             | Yes       | Boolean     | Indicates whether the user is enabled. The value can be **true** or **false**. The default value is **true**.           |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | id                  | Yes       | String      | User ID.                                                                                                                |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | links               | Yes       | JSON object | User resource link.                                                                                                     |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | name                | Yes       | String      | Username.                                                                                                               |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | password_expires_at | Yes       | String      | UTC time when the password will expire. **null** indicates that the password will not expire.                           |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | pwd_status          | No        | Boolean     | Password status. **true** means that the password needs to be changed, and **false** means that the password is normal. |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | pwd_strength        | No        | String      | Password strength. The value can be **high**, **mid**, or **low**.                                                      |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | default_project_id  | No        | String      | ID of the project that is displayed by default when the user logs in to the console.                                    |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | last_project_id     | No        | String      | ID of the project that the user lastly accessed before exiting the system.                                              |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+
   | email               | No        | String      | User email address.                                                                                                     |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "users": [{
              "name": "username",
              "links": {
                  "self": "https://sample.domain.com/v3/users/6d8b04e3bf99445b8f76300xxx"
              },
              "description": "1234",
              "domain_id": "88b16b6440684467b8825d7xxx",
              "enabled": false,
              "id": "6d8b04e3bf99445b8f763009xxx",
              "email" : ""
              "default_project_id": "263fd9",
              "password_expires_at": "2016-12-07T00:00:00.000000Z",
              "pwd_status": true,
              "pwd_strength": "high",
              "last_project_id": ""
          }],
          "links": {
              "self": "https://sample.domain.com/v3/users?domain_id=88b16b6440684467b882xxx154d8&enabled=false",
              "previous": null,
              "next": null
          }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
=========== =========================================
