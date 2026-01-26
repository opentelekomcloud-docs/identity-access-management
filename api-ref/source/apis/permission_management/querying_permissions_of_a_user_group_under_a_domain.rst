:original_name: en-us_topic_0057845571.html

.. _en-us_topic_0057845571:

Querying Permissions of a User Group Under a Domain
===================================================

Function
--------

This API is used to query the permissions of a user group under a domain. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   GET /v3/domains/{domain_id}/groups/{group_id}/roles

-  URI parameters

   ========= ========= ====== ==============
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============
   domain_id Yes       String Domain ID.
   group_id  Yes       String User group ID.
   ========= ========= ====== ==============

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

      curl -i -k -H "Accept:application/json" -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/domains/d54061ebcb5145dd814f8eb3fe9b7ac0/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles

Response Parameters
-------------------

-  Parameters in the response body

   +--------------------------------------------------------------------------+-----------+--------+--------------------------------------------------------------+
   | Parameter                                                                | Mandatory | Type   | Description                                                  |
   +==========================================================================+===========+========+==============================================================+
   | :ref:`links <en-us_topic_0057845571__li876519491423>`                    | Yes       | Object | Role resource link of a specified user group under a domain. |
   +--------------------------------------------------------------------------+-----------+--------+--------------------------------------------------------------+
   | :ref:`roles <en-us_topic_0057845571__l6c7badc7da784e62ae4b0b7c757a339a>` | Yes       | Array  | Role of a specified user group under a domain.               |
   +--------------------------------------------------------------------------+-----------+--------+--------------------------------------------------------------+

-  .. _en-us_topic_0057845571__li876519491423:

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

-  .. _en-us_topic_0057845571__l6c7badc7da784e62ae4b0b7c757a339a:

   roles

   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | Parameter                                              | Type                  | Description                                                                                 |
   +========================================================+=======================+=============================================================================================+
   | id                                                     | String                | ID of a role of a specified user group under a domain.                                      |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | :ref:`links <en-us_topic_0057845571__li104811756121>`  | Object                | Role resource link.                                                                         |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | name                                                   | String                | Name of a role.                                                                             |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | domain_id                                              | String                | ID of the domain to which a role belongs.                                                   |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | type                                                   | String                | Display mode of a role.                                                                     |
   |                                                        |                       |                                                                                             |
   |                                                        |                       | -  **AX**: A role is displayed at the domain layer.                                         |
   |                                                        |                       | -  **XA**: A role is displayed at the project layer.                                        |
   |                                                        |                       | -  **AA**: A role is displayed at both the domain and project layers.                       |
   |                                                        |                       | -  **XX**: A role is not displayed at the domain or project layer.                          |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | display_name                                           | String                | Displayed name of a role.                                                                   |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | catalog                                                | String                | Directory where a role locates.                                                             |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | :ref:`policy <en-us_topic_0057845571__li293016340129>` | Object                | Policy of a role.                                                                           |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | description                                            | String                | Description of a role.                                                                      |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | flag                                                   | String                | The return value **fine_grained** indicates that the permission is a system-defined policy. |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | updated_time                                           | String                | Time when the permission was last updated.                                                  |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+
   | created_time                                           | String                | Time when the permission was created.                                                       |
   +--------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845571__li104811756121:

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

-  .. _en-us_topic_0057845571__li293016340129:

   roles.policy

   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                   | Type                  | Description                                                                                                                             |
   +=============================================================+=======================+=========================================================================================================================================+
   | :ref:`Depends <en-us_topic_0057845571__li289045071219>`     | Array of objects      | Dependency permissions.                                                                                                                 |
   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <en-us_topic_0057845571__li11449454121218>` | Array of objects      | Statement of the permission.                                                                                                            |
   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Version                                                     | String                | Policy version.                                                                                                                         |
   |                                                             |                       |                                                                                                                                         |
   |                                                             |                       | -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                           |
   |                                                             |                       | -  **1.1**: Policy. A policy defines the permissions required to perform actions on a specific cloud resource under certain conditions. |
   +-------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845571__li289045071219:

   roles.policy.Depends

   ============ ====== ==================================
   Parameter    Type   Description
   ============ ====== ==================================
   catalog      String Service catalog of the permission.
   display_name String Display name of the permission.
   ============ ====== ==================================

-  .. _en-us_topic_0057845571__li11449454121218:

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
          "self": "https://sample.domain.com/v3/domains/d54061ebcb5145dd814f8eb3fe9b7ac0/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles",
          "previous": null,
          "next": null
        },
        "roles": [
          {
            "display_name": "Security Administrator",
            "description": "Security Administrator",
            "links": {
              "self": "https://sample.domain.com/v3/roles/005cf92cfd364105afaa5df2eec25012"
            },
            "domain_id": null,
            "name": "secu_admin",
            "type": "AX",
            "catalog": "BASE",
            "policy": {
              "Version": "1.0",
              "Statement": [
                {
                  "Action": [
                    "identity:*"
                  ],
                  "Effect": "Allow"
                }
              ]
            },
            "id": "005cf92cfd364105afaa5df2eec25012"
          },
          {
            "display_name": "Agent Operator",
            "description": "Agent Operator",
            "links": {
              "self": "https://sample.domain.com/v3/roles/d160d30477c642a486ad10e3b4d9820f"
            },
            "domain_id": null,
            "name": "te_agency",
            "type": "AX",
            "catalog": "IAM",
            "policy": {
              "Version": "1.0",
              "Statement": [
                {
                  "Action": [
                    "identity:assume role"
                  ],
                  "Effect": "Allow"
                }
              ]
            },
            "id": "d160d30477c642a486ad10e3b4d9820f"
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
