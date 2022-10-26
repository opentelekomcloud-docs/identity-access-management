:original_name: en-us_topic_0097949518.html

.. _en-us_topic_0097949518:

Obtaining a Temporary AK/SK
===========================

Function
--------

You can obtain a temporary AK/SK and security token (offline AK/SK) by using a user token, agency token, and federated token. A temporary AK/SK is a token with temporary permissions issued to users. It conforms to the principle of least privilege and can be used to temporarily access OBS.

URI
---

POST /v3.0/OS-CREDENTIAL/securitytokens

Request Parameters
------------------

-  Parameters in the request header

   -  Obtaining a temporary AK/SK with an agency token (**methods** is set to **assume_role**)

      +--------------+-----------+--------+----------------------------------------------------------+
      | Parameter    | Mandatory | Type   | Description                                              |
      +==============+===========+========+==========================================================+
      | X-Auth-Token | Yes       | String | Token with permissions of the **Agent Operator** policy. |
      +--------------+-----------+--------+----------------------------------------------------------+
      | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.    |
      +--------------+-----------+--------+----------------------------------------------------------+

   -  Obtaining a temporary AK/SK with a user token or a federated token (**methods** is set to **token**)

      +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                 |
      +==============+===========+========+=============================================================================================================================================================================================+
      | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.                                                                                                                                       |
      +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | X-Auth-Token | No        | String | User token or federated token required for obtaining a temporary AK/SK. You need to specify either this parameter or the token ID in the request body. This parameter takes the precedence. |
      +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameters in the request body

   -  Obtaining a temporary AK/SK with an agency token (**methods** is set to **assume_role**)

      +--------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Mandatory       | Type            | Description                                                                                                                                                                                                                                                             |
      +==========================+=================+=================+=========================================================================================================================================================================================================================================================================+
      | methods                  | Yes             | String Array    | Fill **assume_role** in this field.                                                                                                                                                                                                                                     |
      +--------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | agency_name              | Yes             | String          | Name of the agency created by a delegating party.                                                                                                                                                                                                                       |
      +--------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | domain_name or domain_id | Yes             | String          | **domain.name**: Name of the domain to which the delegating party belongs.                                                                                                                                                                                              |
      +--------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | duration_seconds         | No              | Int             | Validity period (in seconds) of an AK/SK and security token. The value ranges from 15 minutes to 24 hours. The default value is 15 minutes.                                                                                                                             |
      +--------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scope                    | No              | Object          | AK/SK and security token. If this parameter is left blank, the generated security token does not contain the scope information. You are advised to leave this parameter blank. To set the scope of the temporary AK/SK and security token, specify a project or domain. |
      |                          |                 |                 |                                                                                                                                                                                                                                                                         |
      |                          |                 |                 | -  If this field is set to **project**, the temporary AK/SK and security token can only be used to access resources in the project of a specified ID or name.                                                                                                           |
      |                          |                 |                 |                                                                                                                                                                                                                                                                         |
      |                          |                 |                 |    .. code-block::                                                                                                                                                                                                                                                      |
      |                          |                 |                 |                                                                                                                                                                                                                                                                         |
      |                          |                 |                 |       "scope": {                                                                                                                                                                                                                                                        |
      |                          |                 |                 |             "project": {                                                                                                                                                                                                                                                |
      |                          |                 |                 |             "id": "0b95b78b67fa045b38104c12fb..."                                                                                                                                                                                                                       |
      |                          |                 |                 |             }                                                                                                                                                                                                                                                           |
      |                          |                 |                 |           }                                                                                                                                                                                                                                                             |
      |                          |                 |                 |                                                                                                                                                                                                                                                                         |
      |                          |                 |                 | -  If this field is set to **domain**, the temporary AK/SK and security token can be used to access all resources under the domain of a specified ID or name.                                                                                                           |
      |                          |                 |                 |                                                                                                                                                                                                                                                                         |
      |                          |                 |                 |    .. code-block::                                                                                                                                                                                                                                                      |
      |                          |                 |                 |                                                                                                                                                                                                                                                                         |
      |                          |                 |                 |       "scope": {                                                                                                                                                                                                                                                        |
      |                          |                 |                 |             "domain": {                                                                                                                                                                                                                                                 |
      |                          |                 |                 |             "name": " domain A"                                                                                                                                                                                                                                         |
      |                          |                 |                 |             }                                                                                                                                                                                                                                                           |
      |                          |                 |                 |           }                                                                                                                                                                                                                                                             |
      +--------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  Obtaining a temporary AK/SK with a user token or a federated token (**methods** is set to **token**)

      +------------------+-----------+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Mandatory | Type         | Description                                                                                                                                                                                                                      |
      +==================+===========+==============+==================================================================================================================================================================================================================================+
      | methods          | Yes       | String Array | Fill **token** in this field.                                                                                                                                                                                                    |
      +------------------+-----------+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | token            | No        | JSON object  | Common token or federated token required for obtaining a temporary AK/SK. You need to choose either the ID in this object or **X-Auth-Token** in the request header. **X-Auth-Token** takes priority over the ID in this object. |
      +------------------+-----------+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | duration_seconds | No        | Int          | Validity period (in seconds) of an AK/SK and security token. The value ranges from 15 minutes to 24 hours. The default value is 15 minutes.                                                                                      |
      +------------------+-----------+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   -  When the **methods** parameter is set to **assume_role**

      .. code-block::

         {
             "auth": {
                 "identity": {
                     "methods": [
                         "assume_role"
                     ],
                     "assume_role": {
                         "domain_id": "411edb4b634144f587ffc88f9bbdxxx",
                         "xrole_name": "testagency",
                         "duration_seconds": "3600"
                     }
                 }
             }
         }

   -  When the **methods** parameter is set to **token**

      .. code-block::

         {
             "auth": {
                 "identity": {
                     "methods": [
                         "token"
                     ],
                     "token": {
                         "id": "MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...",
                         "duration_seconds": "900"
                     }
                 }
             }
         }

Response Parameters
-------------------

-  Parameters in the response body

   ========== ========= ====== ===========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================
   credential Yes       Object Authentication information.
   ========== ========= ====== ===========================

-  Description about the credential content.

   +---------------+-----------+--------+----------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                        |
   +===============+===========+========+====================================================+
   | expires_at    | Yes       | String | Expiration time.                                   |
   +---------------+-----------+--------+----------------------------------------------------+
   | access        | Yes       | String | AK.                                                |
   +---------------+-----------+--------+----------------------------------------------------+
   | secret        | Yes       | String | SK.                                                |
   +---------------+-----------+--------+----------------------------------------------------+
   | securitytoken | Yes       | String | Used for subsequent replacement of an SK or token. |
   +---------------+-----------+--------+----------------------------------------------------+

-  Example response

   .. code-block::

      {
        "credential": {
          "access": "NQC51NFINJS1JXX...",
          "secret": "EY74MByPZ46kTRJL9ay5DskqXX...",
          "expires_at": "2017-04-17T07:55:18.575000Z",
          "securitytoken": "gAAAAABY9GbWUaGtoa9DPj7_dE4qUSnAXXX..."
        }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
201         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
500         The system is abnormal.
=========== =========================================
