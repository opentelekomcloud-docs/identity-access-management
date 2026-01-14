:original_name: en-us_topic_0079578166.html

.. _en-us_topic_0079578166:

Querying the List of Permissions of an Agency on a Domain
=========================================================

Function
--------

This API is used to query the list of permissions of an agency on a domain.

URI
---

-  URI format

   GET /v3.0/OS-AGENCY/domains/{domain_id}/agencies/{agency_id}/roles

-  URI parameters

   ========= ========= ====== =========================
   Parameter Mandatory Type   Description
   ========= ========= ====== =========================
   domain_id Yes       String ID of the current domain.
   agency_id Yes       String ID of an agency.
   ========= ========= ====== =========================

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3.0/OS-AGENCY/domains/b32d99a7778d4fd9aa5bc616c3dc4e5f/agencies/37f90258b820472bbc8a0f4f0bfd720d/roles

Response Parameters
-------------------

-  Parameters in the response body

   +-------------------------------------------------------+-----------+-------+----------------+
   | Parameter                                             | Mandatory | Type  | Description    |
   +=======================================================+===========+=======+================+
   | :ref:`roles <en-us_topic_0079578166__li181366349618>` | Yes       | Array | List of roles. |
   +-------------------------------------------------------+-----------+-------+----------------+

-  .. _en-us_topic_0079578166__li181366349618:

   roles

   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | Parameter                                              | Type                  | Description                                                           |
   +========================================================+=======================+=======================================================================+
   | catalog                                                | String                | Directory where a role locates.                                       |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | display_name                                           | String                | Displayed name of a role.                                             |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | name                                                   | String                | Name of a role.                                                       |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | :ref:`policy <en-us_topic_0079578166__li104346301296>` | Dict                  | Policy of a role.                                                     |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | domain_id                                              | String                | ID of the domain to which a role belongs.                             |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | type                                                   | String                | Display mode of a role.                                               |
   |                                                        |                       |                                                                       |
   |                                                        |                       | -  **AX**: A role is displayed at the domain layer.                   |
   |                                                        |                       | -  **XA**: A role is displayed at the project layer.                  |
   |                                                        |                       | -  **AA**: A role is displayed at both the domain and project layers. |
   |                                                        |                       | -  **XX**: A role is not displayed at the domain or project layer.    |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | id                                                     | String                | ID of a role.                                                         |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+
   | description                                            | String                | Description of a role.                                                |
   +--------------------------------------------------------+-----------------------+-----------------------------------------------------------------------+

-  roles.links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0079578166__li104346301296:

   roles.policy

   +------------------------------------------------------------+----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                  | Type                             | Description                                                                                                                             |
   +============================================================+==================================+=========================================================================================================================================+
   | :ref:`Depends <en-us_topic_0079578166__li15880832182915>`  | Array of PolicyDepends objects   | Dependency permissions.                                                                                                                 |
   +------------------------------------------------------------+----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <en-us_topic_0079578166__li4700143314291>` | Array of PolicyStatement objects | Statement of the permission.                                                                                                            |
   +------------------------------------------------------------+----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Version                                                    | String                           | Policy version.                                                                                                                         |
   |                                                            |                                  |                                                                                                                                         |
   |                                                            |                                  | -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                           |
   |                                                            |                                  | -  **1.1**: Policy. A policy defines the permissions required to perform actions on a specific cloud resource under certain conditions. |
   +------------------------------------------------------------+----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0079578166__li15880832182915:

   roles.policy.Depends

   ============ ====== ==================================
   Parameter    Type   Description
   ============ ====== ==================================
   catalog      String Service catalog of the permission.
   display_name String Display name of the permission.
   ============ ====== ==================================

-  .. _en-us_topic_0079578166__li4700143314291:

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
   | Condition             | Object                | Conditions for the permission to take effect.                                                                                                                                                                                        |
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
   | Resource              | Object                | Cloud resource.                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       | .. note::                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                      |
   |                       |                       |    -  Five-segment format that can contain asterisks (*): *::::*, for example, **obs:::bucket:\***.                                                                                                                                  |
   |                       |                       |    -  The region segment can be **\*** or a region accessible to the user. The service must exist and the specified resource must belong to the service.                                                                             |
   |                       |                       |    -  In the case of a custom policy for agencies, the type of this parameter is **Object**, and the value should be *"Resource": {"uri": ["/iam/agencies/agencyTest"]}*.                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response (successful request)

   .. code-block::

      {
        "roles": [
          {
            "catalog": "BASE",
            "display_name": "Tenant Guest",
            "name": "readonly",
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
            "domain_id": null,
            "type": "AA",
            "id": "b32d99a7778d4fd9aa5bc616c3dc4e5f",
            "description": "Tenant Guest"
          }
        ]
      }

-  Example response (request failed)

   .. code-block::

      {
        "error": {
          "message": "You are not authorized to perform the requested action: identity:list_domain_grants",
          "code": 403,
          "title": "Forbidden"
        }
      }

Status Codes
------------

=========== =======================================
Status Code Description
=========== =======================================
200         The request is successful.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =======================================
