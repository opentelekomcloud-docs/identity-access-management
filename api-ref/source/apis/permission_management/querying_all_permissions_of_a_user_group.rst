:original_name: iam_10_0011.html

.. _iam_10_0011:

Querying All Permissions of a User Group
========================================

Function
--------

This API is provided for the administrator to query all permissions that have been assigned to a user group.

URI
---

GET /v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/inherited_to_projects

.. table:: **Table 1** URI parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                               |
   +===========+===========+========+===========================================================================================================================================================================+
   | domain_id | Yes       | String | Domain ID. For details about how to obtain the ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`.              |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id  | Yes       | String | User group ID. For details about how to obtain a user group ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Parameters in the response body

   +------------------------------------------------------------------------+------------------+----------------------------+
   | Parameter                                                              | Type             | Description                |
   +========================================================================+==================+============================+
   | :ref:`links <iam_10_0011__en-us_topic_0289135272_table172743139494>`   | object           | Resource link information. |
   +------------------------------------------------------------------------+------------------+----------------------------+
   | :ref:`roles <iam_10_0011__en-us_topic_0289135272_table16249181318490>` | Array of objects | Permission information.    |
   +------------------------------------------------------------------------+------------------+----------------------------+

.. _iam_10_0011__en-us_topic_0289135272_table16249181318490:

.. table:: **Table 4** roles

   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                               | Type                  | Description                                                                                                                                                              |
   +=========================================================================+=======================+==========================================================================================================================================================================+
   | flag                                                                    | String                | If this parameter is set to **fine_grained**, the permission is a system-defined policy.                                                                                 |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description_cn                                                          | String                | Description of the permission in Chinese. This parameter is returned in the response only when **description_cn** is specified during policy creation.                   |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | catalog                                                                 | String                | Service catalog of the permission.                                                                                                                                       |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                                    | String                | Permission name. This parameter is carried in the token of a user, allowing the system to determine whether the user has permissions to access a specific cloud service. |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                                                             | String                | Description of the permission.                                                                                                                                           |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`links <iam_10_0011__en-us_topic_0289135272_table172743139494>`    | object                | Permission resource link.                                                                                                                                                |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                                                                      | String                | Permission ID.                                                                                                                                                           |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name                                                            | String                | Display name of the permission.                                                                                                                                          |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                                                                    | String                | Display mode of the permission.                                                                                                                                          |
   |                                                                         |                       |                                                                                                                                                                          |
   |                                                                         |                       | .. note::                                                                                                                                                                |
   |                                                                         |                       |                                                                                                                                                                          |
   |                                                                         |                       |    -  **AX**: Account level.                                                                                                                                             |
   |                                                                         |                       |    -  **XA**: Project level.                                                                                                                                             |
   |                                                                         |                       |    -  **AA**: Both the account level and project level.                                                                                                                  |
   |                                                                         |                       |    -  **XX**: Neither the account level nor project level.                                                                                                               |
   |                                                                         |                       |    -  The display mode of a custom policy can only be **AX** or **XA**. A custom policy must be displayed at either of the two levels.                                   |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`policy <iam_10_0011__en-us_topic_0289135272_table19278113194913>` | object                | Content of the permission.                                                                                                                                               |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_time                                                            | String                | Time when the permission was last updated.                                                                                                                               |
   |                                                                         |                       |                                                                                                                                                                          |
   |                                                                         |                       | .. note::                                                                                                                                                                |
   |                                                                         |                       |                                                                                                                                                                          |
   |                                                                         |                       |    The value is a Unix timestamp in millisecond, for example, 1687913793000.                                                                                             |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_time                                                            | String                | Time when the permission was created.                                                                                                                                    |
   |                                                                         |                       |                                                                                                                                                                          |
   |                                                                         |                       | .. note::                                                                                                                                                                |
   |                                                                         |                       |                                                                                                                                                                          |
   |                                                                         |                       |    The value is a Unix timestamp in millisecond, for example, 1687913793000.                                                                                             |
   +-------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_10_0011__en-us_topic_0289135272_table172743139494:

.. table:: **Table 5** links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

.. _iam_10_0011__en-us_topic_0289135272_table19278113194913:

.. table:: **Table 6** roles.policy

   +---------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                 | Type                  | Description                                                                                                                                   |
   +===========================================================================+=======================+===============================================================================================================================================+
   | :ref:`Depends <iam_10_0011__en-us_topic_0289135272_table182851413184913>` | Array of objects      | Dependent permissions.                                                                                                                        |
   +---------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <iam_10_0011__en-us_topic_0289135272_table0288151316493>` | Array of objects      | Statement of the permission.                                                                                                                  |
   +---------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Version                                                                   | String                | Policy version.                                                                                                                               |
   |                                                                           |                       |                                                                                                                                               |
   |                                                                           |                       | .. note::                                                                                                                                     |
   |                                                                           |                       |                                                                                                                                               |
   |                                                                           |                       |    -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                              |
   |                                                                           |                       |    -  **1.1**: Policy. A policy defines the permissions required to perform operations on a specific cloud resource under certain conditions. |
   +---------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_10_0011__en-us_topic_0289135272_table182851413184913:

.. table:: **Table 7** roles.policy.Depends

   ============ ====== ==================================
   Parameter    Type   Description
   ============ ====== ==================================
   catalog      String Service catalog of the permission.
   display_name String Display name of the permission.
   ============ ====== ==================================

.. _iam_10_0011__en-us_topic_0289135272_table0288151316493:

.. table:: **Table 8** roles.policy.Statement

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                |
   +=======================+=======================+============================================================================================================================================================================================================================================+
   | Action                | Array of strings      | Specific operation permissions on a resource. A maximum of 100 actions are allowed. For details about supported actions, see "Permissions Policies and Supported Actions" in the API Reference of cloud services.                          |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | .. note::                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |    -  The value format is *Service name*:*Resource type*:*Operation*, for example, **vpc:ports:create**.                                                                                                                                   |
   |                       |                       |    -  *Service name*: indicates the product name, such as **ecs**, **evs**, or **vpc**. Only lowercase letters are allowed. Resource types and operations are not case-sensitive. You can use an asterisk (*) to represent all operations. |
   |                       |                       |    -  In the case of a custom policy for agencies, this parameter should be set to *"Action": ["iam:agencies:assume"]*.                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Effect                | String                | Effect of the permission. The value can be **Allow** or **Deny**. If both Allow and Deny statements are found in a policy, the authentication starts from the Deny statements.                                                             |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | Enumerated values:                                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | -  Allow                                                                                                                                                                                                                                   |
   |                       |                       | -  Deny                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Condition             | Object                | Conditions for the permission to take effect. The number of conditions cannot exceed 10. If this parameter is not specified during policy creation, it will not be returned in the response.                                               |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | .. note::                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |    Take the condition in the sample request as an example, the values of the condition key (**obs:prefix**) and string (**public**) must be equal (**StringEquals**).                                                                      |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |    .. code-block::                                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |        "Condition": {                                                                                                                                                                                                                      |
   |                       |                       |                     "StringEquals": {                                                                                                                                                                                                      |
   |                       |                       |                       "obs:prefix": [                                                                                                                                                                                                      |
   |                       |                       |                         "public"                                                                                                                                                                                                           |
   |                       |                       |                       ]                                                                                                                                                                                                                    |
   |                       |                       |                     }                                                                                                                                                                                                                      |
   |                       |                       |                   }                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource              | Object                | Cloud resource. If this parameter is not specified during policy creation, it will not be returned in the response. The object can contain a maximum of 10 resource strings, and each string cannot exceed 128 characters.                 |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       | .. note::                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                            |
   |                       |                       |    -  Format: *::::*. For example, **obs:::bucket:\***. Asterisks are allowed.                                                                                                                                                             |
   |                       |                       |    -  The region segment can be **\*** or a region accessible to the user. The specified resource must belong to the corresponding service that actually exists.                                                                           |
   |                       |                       |    -  In the case of a custom policy for agencies, the type of this parameter is Object, and the value should be set to *"Resource": {"uri": ["/iam/agencies/07805acaba800fdd4fbdc00b8f888c7c"]}*.                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Request for querying all permissions of a user group

.. code-block:: text

   GET https://sample.domain.com/v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/inherited_to_projects

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "roles" : [ {

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
       "flag" : "fine_grained",

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
     }
   }

Status Codes
------------

=========== ==========================
Status Code Description
=========== ==========================
200         The request is successful.
401         Authentication failed.
403         Access denied.
=========== ==========================

Error Codes
-----------

For details, see :ref:`Error Codes <iam_02_0006>`.
