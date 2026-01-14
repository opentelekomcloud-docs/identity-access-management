:original_name: en-us_topic_0057845603.html

.. _en-us_topic_0057845603:

Querying Role Details
=====================

Function
--------

This API is used to query role details, including the permissions policies of a role. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   GET /v3/roles/{role_id}

-  URI parameters

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   role_id   Yes       String ID of a role.
   ========= ========= ====== =============

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/roles/19bb93eec4ca4f08aefdc02da76d8f3c

Response Parameters
-------------------

-  Parameters in the response body

   +-------------------------------------------------------+-----------+--------+----------------------+
   | Parameter                                             | Mandatory | Type   | Description          |
   +=======================================================+===========+========+======================+
   | :ref:`role <en-us_topic_0057845603__li1393915941710>` | Yes       | Object | Details of the role. |
   +-------------------------------------------------------+-----------+--------+----------------------+

-  .. _en-us_topic_0057845603__li1393915941710:

   role

   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                               | Type                  | Description                                                                                                                                             |
   +=========================================================+=======================+=========================================================================================================================================================+
   | domain_id                                               | String                | ID of the account to which the permission belongs.                                                                                                      |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flag                                                    | String                | The return value **fine_grained** indicates that the permission is a system-defined policy.                                                             |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | catalog                                                 | String                | Service catalog of the permission.                                                                                                                      |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                    | String                | Permission name for internal use. For example, **ccs_user** is the internal name of the **CCS User** role for CCS.                                      |
   |                                                         |                       |                                                                                                                                                         |
   |                                                         |                       | This parameter is carried in the token of a user, allowing the system to determine whether the user has permissions to access a specific cloud service. |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                                             | String                | Permission description.                                                                                                                                 |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`links <en-us_topic_0057845603__li18940155912176>` | Object                | Permission resource link.                                                                                                                               |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                                                      | String                | Permission ID.                                                                                                                                          |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name                                            | String                | Permission name.                                                                                                                                        |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                                                    | String                | Display mode of the permission.                                                                                                                         |
   |                                                         |                       |                                                                                                                                                         |
   |                                                         |                       | -  **AX**: Account level.                                                                                                                               |
   |                                                         |                       | -  **XA**: Project level.                                                                                                                               |
   |                                                         |                       | -  **AA**: Both the account level and project level.                                                                                                    |
   |                                                         |                       | -  **XX**: Neither the account level nor project level.                                                                                                 |
   |                                                         |                       | -  The display mode of a custom policy can only be **AX** or **XA**. A custom policy must be displayed at either of the two levels.                     |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`policy <en-us_topic_0057845603__li9274146131814>` | Object                | Permission content.                                                                                                                                     |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_time                                            | String                | Time when the permission was last updated.                                                                                                              |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_time                                            | String                | Time when the permission was created.                                                                                                                   |
   +---------------------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845603__li18940155912176:

   role.links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845603__li9274146131814:

   role.policy

   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                 | Type                  | Description                                                                                                                             |
   +===========================================================+=======================+=========================================================================================================================================+
   | :ref:`Depends <en-us_topic_0057845603__li1127596141813>`  | Array of objects      | Dependency permissions.                                                                                                                 |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <en-us_topic_0057845603__li065428111818>` | Array of objects      | Statement of the permission.                                                                                                            |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Version                                                   | String                | Policy version.                                                                                                                         |
   |                                                           |                       |                                                                                                                                         |
   |                                                           |                       | -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                           |
   |                                                           |                       | -  **1.1**: Policy. A policy defines the permissions required to perform actions on a specific cloud resource under certain conditions. |
   +-----------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845603__li1127596141813:

   role.policy.Depends

   ============ ====== ==================================
   Parameter    Type   Description
   ============ ====== ==================================
   catalog      String Service catalog of the permission.
   display_name String Display name of the permission.
   ============ ====== ==================================

-  .. _en-us_topic_0057845603__li065428111818:

   role.policy.Statement

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
   |                       |                       |    -  Five-segment format with asterisks (*) allowed: *::::*. For example, **obs:::bucket:\***.                                                                                                                                      |
   |                       |                       |    -  The region segment can be **\*** or a region accessible to the user. The service must exist and the specified resource must belong to the service.                                                                             |
   |                       |                       |    -  In the case of a custom policy for agencies, the type of this parameter is **Object**, and the value should be *"Resource": {"uri": ["/iam/agencies/agencyTest"]}*.                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "role": {
          "display_name": "Tanent Guest",
          "description": "Tanent Guest",
          "links": {
            "self": "https://sample.domain.com/v3/roles/19bb93eec4ca4f08aefdc02da76d8f3c"
          },
          "domain_id": null,
          "catalog": "BASE",
          "policy": {
            "Version": "1.0",
            "Statement": [
              {
                "Action": [
                  "::Get",
                  "::List"
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
          "id": "19bb93eec4ca4f08aefdc02da76d8f3c",
          "type": "AA",
          "name": "readonly"
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
