:original_name: en-us_topic_0057845640.html

.. _en-us_topic_0057845640:

Querying Permissions of a User Group Corresponding to a Project
===============================================================

Function
--------

This API is used to query the permissions of a specified user group corresponding to a project. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   GET /v3/projects/{project_id}/groups/{group_id}/roles

-  URI parameters

   ========== ========= ====== ===================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================
   project_id Yes       String Project ID.
   group_id   Yes       String ID of a user group.
   ========== ========= ====== ===================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Accept       | Yes       | String | Fill **application/json** in this field.                            |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/projects/073bbf60da374853841cf6624c94de4b/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles

Response Parameters
-------------------

-  Parameters in the response body

   +--------------------------------------------------------------------------+-----------+--------+---------------------+
   | Parameter                                                                | Mandatory | Type   | Description         |
   +==========================================================================+===========+========+=====================+
   | :ref:`links <en-us_topic_0057845640__li19722550193713>`                  | Yes       | Object | Role resource link. |
   +--------------------------------------------------------------------------+-----------+--------+---------------------+
   | :ref:`roles <en-us_topic_0057845640__l6c7badc7da784e62ae4b0b7c757a339a>` | Yes       | Array  | List of roles.      |
   +--------------------------------------------------------------------------+-----------+--------+---------------------+

-  .. _en-us_topic_0057845640__li19722550193713:

   links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845640__l6c7badc7da784e62ae4b0b7c757a339a:

   roles

   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | Parameter                                                 | Type                  | Description                                                           |
   +===========================================================+=======================+=======================================================================+
   | id                                                        | String                | ID of a role.                                                         |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | :ref:`links <en-us_topic_0057845640__li44116129422>`      | Object                | Role resource link.                                                   |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | name                                                      | String                | Name of a role.                                                       |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | domain_id                                                 | String                | ID of the domain to which a role belongs.                             |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | type                                                      | String                | Display mode of a role.                                               |
   |                                                           |                       |                                                                       |
   |                                                           |                       | -  **AX**: A role is displayed at the domain layer.                   |
   |                                                           |                       | -  **XA**: A role is displayed at the project layer.                  |
   |                                                           |                       | -  **AA**: A role is displayed at both the domain and project layers. |
   |                                                           |                       | -  **XX**: A role is not displayed at the domain or project layer.    |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | display_name                                              | String                | Displayed name of a role.                                             |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | catalog                                                   | String                | Directory where a role locates.                                       |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | :ref:`policy <en-us_topic_0057845640__li111941318174218>` | Object                | Policy of a role.                                                     |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | description                                               | String                | Description of a role.                                                |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+

-  .. _en-us_topic_0057845640__li44116129422:

   roles.links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845640__li111941318174218:

   roles.policy

   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                   | Type                  | Description                                                                                                                             |
   +=============================================================+=======================+=========================================================================================================================================+
   | :ref:`Depends <en-us_topic_0057845640__li826817221428>`     | Array of objects      | Dependency permissions.                                                                                                                 |
   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <en-us_topic_0057845640__li14989172364217>` | Array of objects      | Statement of the permission.                                                                                                            |
   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Version                                                     | String                | Policy version.                                                                                                                         |
   |                                                             |                       |                                                                                                                                         |
   |                                                             |                       | -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                           |
   |                                                             |                       | -  **1.1**: Policy. A policy defines the permissions required to perform actions on a specific cloud resource under certain conditions. |
   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845640__li826817221428:

   roles.policy.Depends

   ============ ====== ==================================
   Parameter    Type   Description
   ============ ====== ==================================
   catalog      String Service catalog of the permission.
   display_name String Permission name.
   ============ ====== ==================================

-  .. _en-us_topic_0057845640__li14989172364217:

   roles.policy.Statement

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================================================+
   | Action                | Array of strings      | Specific operation permissions on a resource. For details about supported actions, see "Permissions and Supported Actions" in the API Reference of cloud services.                                                                   |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       | .. note::                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       |    -  Format: *Service name*:*Resource type*:*Action*, for example, **vpc:ports:create**                                                                                                                                             |
   |                       |                       |    -  *Service name*: indicates the service name, such as **ecs**, **evs**, or **vpc**. Only lowercase letters are allowed. Resource types and actions are not case-sensitive. You can use an asterisk (*) to represent all actions. |
   |                       |                       |    -  In the case of a custom policy for agencies, this parameter value should be *"Action": ["``iam:tokens:assume``"]*.                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Effect                | String                | Effect of the permission. The value can be **Allow** or **Deny**. If both Allow and Deny statements are found in a policy, the authentication starts from the Deny statements.                                                       |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       | The options are as follows:                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       | -  Allow                                                                                                                                                                                                                             |
   |                       |                       | -  Deny                                                                                                                                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Condition             | Object                | Conditions for the permission to take effect. If this parameter is not specified during policy creation, it will not be returned in the response.                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       | .. note::                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       |    Take the condition in the sample request as an example, the values of the condition key (**obs:prefix**) and string (**public**) must be equal (**StringEquals**).                                                                |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       |    .. code-block::                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       |        "Condition": {                                                                                                                                                                                                                |
   |                       |                       |                     "StringEquals": {                                                                                                                                                                                                |
   |                       |                       |                       "obs:prefix": [                                                                                                                                                                                                |
   |                       |                       |                         "public"                                                                                                                                                                                                     |
   |                       |                       |                       ]                                                                                                                                                                                                              |
   |                       |                       |                     }                                                                                                                                                                                                                |
   |                       |                       |                   }                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource              | Object                | Cloud resource. If this parameter is not specified during policy creation, it will not be returned in the response.                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       | .. note::                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       |    -  Five-segment format that can contain asterisks (*): *::::*, for example, **obs:::bucket:\***.                                                                                                                                  |
   |                       |                       |    -  The region segment can be **\*** or a region accessible to the user. The service must exist and the specified resource must belong to the service.                                                                             |
   |                       |                       |    -  In the case of a custom policy for agencies, the type of this parameter is **Object**, and the value should be *"Resource": {"uri": ["/iam/agencies/agencyTest"]}*.                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "links": {
              "self": " https://sample.domain.com/v3/projects/3a4cd4d559d8492bbe7bd355643f9763/groups/728da352c017480f80b5a96beb15f0e6/roles",
              "previous": null,
              "next": null
          },
          "roles": [
              {
                  "catalog": "BASE",
                  "display_name": "Guest",
                  "name": "readonly",
                  "links": {
                      "self": " https://sample.domain.com/v3/roles/13d132b7856945788f6df7eb3ed5c35e"
                  },
                  "policy": {
                      "Version": "1.0",
                      "Statement": [
                          {
                              "Action": [
                                  "*:*:Get*",
                                  "*:*:List*"
                              ],
                              "Effect": "Allow"
                          },
                          {
                              "Action": [
                                  "identity:*"
                              ],
                              "Effect": "Deny"
                          }
                      ]
                  },
                  "domain_id": null,
                  "type": "AA",
                  "id": "13d132b7856945788f6df7eb3ed5c35e",
                  "description": "Guest"
              },
              {
                  "catalog": "BASE",
                  "display_name": "Tenant Administrator",
                  "name": "te_admin",
                  "links": {
                      "self": " https://sample.domain.com/v3/roles/1def304b73f14e8eb8d1eb9bf8337ae6"
                  },
                  "policy": {
                      "Version": "1.0",
                      "Statement": [
                          {
                              "Action": [
                                  "*"
                              ],
                              "Effect": "Allow"
                          },
                          {
                              "Action": [
                                  "identity:*"
                              ],
                              "Effect": "Deny"
                          }
                      ]
                  },
                  "domain_id": null,
                  "type": "AA",
                  "id": "1def304b73f14e8eb8d1eb9bf8337ae6",
                  "description": "Tenant Administrator"
              }
          ]
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
