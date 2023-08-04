:original_name: en-us_topic_0057845591.html

.. _en-us_topic_0057845591:

Querying a Role List
====================

Function
--------

This API is used to query a role list, including the permissions policies of a role. A role is a set of permissions and represents a group of actions.

URI
---

GET /v3/roles

.. table:: **Table 1** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================+
   | domain_id       | No              | String          | Domain ID.                                                                                                                       |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | .. note::                                                                                                                        |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 |    -  If this parameter is specified, only custom policies of the account will be returned.                                      |
   |                 |                 |                 |    -  If this parameter is not specified, all system permissions (including system-defined policies and roles) will be returned. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Permission name for internal use. It may be different from the **display_name** displayed on the console.                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions.    |
   +--------------+-----------+--------+-------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Parameters in the response body

   +------------------------------------------------------------------------------------------+------------------+------------------------------+
   | Parameter                                                                                | Type             | Description                  |
   +==========================================================================================+==================+==============================+
   | :ref:`links <en-us_topic_0057845591__en-us_topic_0222037529_response_rs101links>`        | Object           | Resource link information.   |
   +------------------------------------------------------------------------------------------+------------------+------------------------------+
   | :ref:`roles <en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritem>` | Array of objects | Permission information.      |
   +------------------------------------------------------------------------------------------+------------------+------------------------------+
   | total_number                                                                             | Integer          | Total number of permissions. |
   +------------------------------------------------------------------------------------------+------------------+------------------------------+

.. _en-us_topic_0057845591__en-us_topic_0222037529_response_rs101links:

.. table:: **Table 4** links

   ========= ====== =======================
   Parameter Type   Description
   ========= ====== =======================
   self      String Resource link.
   previous  String Previous resource link.
   next      String Next resource link.
   ========= ====== =======================

.. _en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritem:

.. table:: **Table 5** roles

   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                       | Type                  | Description                                                                                                                                                        |
   +=================================================================================================+=======================+====================================================================================================================================================================+
   | domain_id                                                                                       | String                | ID of the domain to which the permission belongs.                                                                                                                  |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flag                                                                                            | String                | If this parameter is set to **fine_grained**, the permission is a system-defined policy.                                                                           |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description_cn                                                                                  | String                | Description of the permission in Chinese.                                                                                                                          |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | catalog                                                                                         | String                | Service catalog of the permission.                                                                                                                                 |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                                                            | String                | Permission name. This parameter is carried in the token of a user. The cloud service determines whether the user has the access permission based on the role name. |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                                                                                     | String                | Description of the permission.                                                                                                                                     |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`links <en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritemlinks>`   | Object                | Permission resource link.                                                                                                                                          |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                                                                                              | String                | Permission ID.                                                                                                                                                     |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name                                                                                    | String                | Display name of the permission.                                                                                                                                    |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                                                                                            | String                | Display mode of the permission.                                                                                                                                    |
   |                                                                                                 |                       |                                                                                                                                                                    |
   |                                                                                                 |                       | .. note::                                                                                                                                                          |
   |                                                                                                 |                       |                                                                                                                                                                    |
   |                                                                                                 |                       |    -  **AX**: Account level.                                                                                                                                       |
   |                                                                                                 |                       |    -  **XA**: Project level.                                                                                                                                       |
   |                                                                                                 |                       |    -  **AA**: Both the account level and project level.                                                                                                            |
   |                                                                                                 |                       |    -  **XX**: Neither the account level nor project level.                                                                                                         |
   |                                                                                                 |                       |    -  The display mode of a custom policy can only be **AX** or **XA**. A custom policy must be displayed at either of the two levels.                             |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`policy <en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritempolicy>` | Object                | Content of the permission.                                                                                                                                         |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_time                                                                                    | String                | Time when the permission was last updated.                                                                                                                         |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_time                                                                                    | String                | Time when the permission was created.                                                                                                                              |
   +-------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritemlinks:

.. table:: **Table 6** roles.links

   ========= ====== =======================
   Parameter Type   Description
   ========= ====== =======================
   self      String Resource link.
   previous  String Previous resource link.
   next      String Next resource link.
   ========= ====== =======================

.. _en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritempolicy:

.. table:: **Table 7** roles.policy

   +--------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                          | Type                  | Description                                                                                                                                   |
   +====================================================================================================================+=======================+===============================================================================================================================================+
   | :ref:`Depends <en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritempolicydependsarritem>`     | Array of objects      | Dependence permissions.                                                                                                                       |
   +--------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritempolicystatementarritem>` | Array of objects      | Statement of the permission.                                                                                                                  |
   +--------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Version                                                                                                            | String                | Permission version.                                                                                                                           |
   |                                                                                                                    |                       |                                                                                                                                               |
   |                                                                                                                    |                       | .. note::                                                                                                                                     |
   |                                                                                                                    |                       |                                                                                                                                               |
   |                                                                                                                    |                       |    -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                              |
   |                                                                                                                    |                       |    -  **1.1**: Policy. A policy defines the permissions required to perform operations on a specific cloud resource under certain conditions. |
   +--------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritempolicydependsarritem:

.. table:: **Table 8** roles.policy.Depends

   ============ ====== ==================================
   Parameter    Type   Description
   ============ ====== ==================================
   catalog      String Service catalog of the permission.
   display_name String Display name of the permission.
   ============ ====== ==================================

.. _en-us_topic_0057845591__en-us_topic_0222037529_response_rs101rolesarritempolicystatementarritem:

.. table:: **Table 9** roles.policy.Statement

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                |
   +=======================+=======================+============================================================================================================================================================================================================================================+
   | Action                | Array of strings      | Specific operation permission on a resource. A maximum of 100 actions are allowed.                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | .. note::                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |    -  The value format is *Service name*:*Resource type*:*Operation*, for example, **vpc:ports:create**.                                                                                                                                   |
   |                       |                       |    -  *Service name*: indicates the product name, such as **ecs**, **evs**, or **vpc**. Only lowercase letters are allowed. Resource types and operations are not case-sensitive. You can use an asterisk (*) to represent all operations. |
   |                       |                       |    -  For a custom agency policy, this parameter should be set to *"Action": ["iam:agencies:assume"]*.                                                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Effect                | String                | Effect of the permission. The value can be **Allow** or **Deny**. If both Allow and Deny statements are found in a policy, the authentication starts from the Deny statements.                                                             |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | Options:                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | -  Allow                                                                                                                                                                                                                                   |
   |                       |                       | -  Deny                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Condition             | Object                | Conditions for the permission to take effect. A maximum of 10 conditions are allowed.                                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource              | Array of strings      | Cloud resource. The array can contain a maximum of 10 resource strings, and each string cannot exceed 128 characters.                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | .. note::                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |    -  Format: *::::*. For example, **obs:::bucket:\***. Asterisks are allowed.                                                                                                                                                             |
   |                       |                       |    -  The region segment can be **\*** or a region accessible to the user. The specified resource must belong to the corresponding service that actually exists.                                                                           |
   |                       |                       |    -  In the case of a custom policy for agencies, the type of this parameter is object, and the value should be set to *"Resource": {"uri": ["/iam/agencies/07805acaba800fdd4fbdc00b8f888c7c"]}*.                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 10** roles.policy.Statement.Condition.operator

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                             |
   +=======================+=======================+=========================================================================================================================+
   | attribute             | Array of strings      | Condition key. The condition key must correspond to the specified operator. A maximum of 10 condition keys are allowed. |
   |                       |                       |                                                                                                                         |
   |                       |                       | The parameter type is custom character string array.                                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3/roles

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "roles" : [ {
       "domain_id" : null,
       "description_cn" : "Description of the permission in Chinese",
       "catalog" : "VulnScan",
       "name" : "wscn_adm",
       "description" : "Vulnerability Scan Service administrator of tasks and reports.",
       "links" : {
         "next" : null,
         "previous" : null,
         "self" : "https://sample.domain.com/v3/roles/0af84c1502f447fa9c2fa18083fbb..."
       },
       "id" : "0af84c1502f447fa9c2fa18083fbb...",
       "display_name" : "VSS Administrator",
       "type" : "XA",
       "policy" : {
         "Version" : "1.0",
         "Statement" : [ {
           "Action" : [ "WebScan:*:*" ],
           "Effect" : "Allow"
         } ],
         "Depends" : [ {
           "catalog" : "BASE",
           "display_name" : "Server Administrator"
         }, {
           "catalog" : "BASE",
           "display_name" : "Tenant Guest"
         } ]
       }
     }, {
       "domain_id" : null,
       "flag" : "fine_grained",
       "description_cn" : "Description of the permission in Chinese",
       "catalog" : "CSE",
       "name" : "system_all_34",
       "description" : "All permissions of CSE service.",
       "links" : {
         "next" : null,
         "previous" : null,
         "self" : "https://sample.domain.com/v3/roles/0b5ea44ebdc64a24a9c372b2317f7..."
       },
       "id" : "0b5ea44ebdc64a24a9c372b2317f7...",
       "display_name" : "CSE Admin",
       "type" : "XA",
       "policy" : {
         "Version" : "1.1",
         "Statement" : [ {
           "Action" : [ "cse:*:*", "ecs:*:*", "evs:*:*", "vpc:*:*" ],
           "Effect" : "Allow"
         } ]
       }
     } ],
     "links" : {
       "next" : null,
       "previous" : null,
       "self" : "https://sample.domain.com/v3/roles"
     },
     "total_number" : 300
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
=========== =========================================
