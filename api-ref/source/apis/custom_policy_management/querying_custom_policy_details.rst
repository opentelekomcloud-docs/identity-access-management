:original_name: iam_02_0012.html

.. _iam_02_0012:

Querying Custom Policy Details
==============================

Function
--------

This API is provided for the administrator to query custom policy details.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

GET /v3.0/OS-ROLE/roles/{role_id}

.. table:: **Table 1** URI parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                      |
   +===========+===========+========+==================================================================================================================+
   | role_id   | Yes       | String | Custom policy ID. For details about how to obtain a custom policy ID, see :ref:`Custom Policy ID <iam_02_0011>`. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------------------------------------------------------------------------------------+--------+----------------------------+
   | Parameter                                                                                           | Type   | Description                |
   +=====================================================================================================+========+============================+
   | :ref:`role <iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritem>` | Object | Custom policy information. |
   +-----------------------------------------------------------------------------------------------------+--------+----------------------------+

.. _iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritem:

.. table:: **Table 4** role

   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                   | Type                  | Description                                                                                                                            |
   +=============================================================================================================+=======================+========================================================================================================================================+
   | domain_id                                                                                                   | String                | Domain ID.                                                                                                                             |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | references                                                                                                  | Integer               | Number of references.                                                                                                                  |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | updated_time                                                                                                | String                | Time when the custom policy was last updated.                                                                                          |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | created_time                                                                                                | String                | Time when the custom policy was created.                                                                                               |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | description_cn                                                                                              | String                | Description of the custom policy.                                                                                                      |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | catalog                                                                                                     | String                | Service catalog.                                                                                                                       |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                                                                        | String                | Name of the custom policy.                                                                                                             |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | description                                                                                                 | String                | Description of the custom policy.                                                                                                      |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`links <iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritemlinks>`   | Object                | Resource link of the custom policy.                                                                                                    |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | id                                                                                                          | String                | Policy ID.                                                                                                                             |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | display_name                                                                                                | String                | Display name of the custom policy.                                                                                                     |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | type                                                                                                        | String                | Display mode.                                                                                                                          |
   |                                                                                                             |                       |                                                                                                                                        |
   |                                                                                                             |                       | .. note::                                                                                                                              |
   |                                                                                                             |                       |                                                                                                                                        |
   |                                                                                                             |                       |    -  **AX**: Account level.                                                                                                           |
   |                                                                                                             |                       |    -  **XA**: Project level.                                                                                                           |
   |                                                                                                             |                       |    -  The display mode of a custom policy can only be **AX** or **XA**. A custom policy must be displayed at either of the two levels. |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`policy <iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicy>` | Object                | Content of custom policy.                                                                                                              |
   +-------------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritemlinks:

.. table:: **Table 5** role.links

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   self      String Resource link.
   ========= ====== ==============

.. _iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicy:

.. table:: **Table 6** role.policy

   +--------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                                      | Type                  | Description                                                                                                                                   |
   +================================================================================================================================+=======================+===============================================================================================================================================+
   | Version                                                                                                                        | String                | Policy version.                                                                                                                               |
   |                                                                                                                                |                       |                                                                                                                                               |
   |                                                                                                                                |                       | .. note::                                                                                                                                     |
   |                                                                                                                                |                       |                                                                                                                                               |
   |                                                                                                                                |                       |    -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                              |
   |                                                                                                                                |                       |    -  **1.1**: Policy. A policy defines the permissions required to perform operations on a specific cloud resource under certain conditions. |
   +--------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicystatementarritem>` | Array of objects      | Statement of the policy. A policy can contain a maximum of eight statements.                                                                  |
   +--------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicystatementarritem:

.. table:: **Table 7** role.policy.Statement

   +-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                                               | Type                  | Description                                                                                                                                                                                                                                |
   +=========================================================================================================================================+=======================+============================================================================================================================================================================================================================================+
   | Action                                                                                                                                  | Array of strings      | Specific operation permission on a resource. A maximum of 100 actions are allowed.                                                                                                                                                         |
   |                                                                                                                                         |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                                         |                       | .. note::                                                                                                                                                                                                                                  |
   |                                                                                                                                         |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                                         |                       |    -  The value format is *Service name*:*Resource type*:*Operation*, for example, **vpc:ports:create**.                                                                                                                                   |
   |                                                                                                                                         |                       |    -  *Service name*: indicates the product name, such as **ecs**, **evs**, or **vpc**. Only lowercase letters are allowed. Resource types and operations are not case-sensitive. You can use an asterisk (*) to represent all operations. |
   |                                                                                                                                         |                       |    -  For a custom policy for agencies, this parameter should be set to *"Action": ["iam:agencies:assume"]*.                                                                                                                               |
   +-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Effect                                                                                                                                  | String                | Effect of the permission. The value can be **Allow** or **Deny**. If both Allow and Deny statements are found in a policy, the authentication starts from the Deny statements.                                                             |
   |                                                                                                                                         |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                                         |                       | Options:                                                                                                                                                                                                                                   |
   |                                                                                                                                         |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                                         |                       | -  Allow                                                                                                                                                                                                                                   |
   |                                                                                                                                         |                       | -  Deny                                                                                                                                                                                                                                    |
   +-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Condition <iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicystatementarritemcondition>` | Object                | Conditions for the permission to take effect. A maximum of 10 conditions are allowed.                                                                                                                                                      |
   +-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource                                                                                                                                | Array of strings      | Cloud resource. The array can contain a maximum of 10 resource strings, and each string cannot exceed 128 characters.                                                                                                                      |
   |                                                                                                                                         |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                                         |                       | .. note::                                                                                                                                                                                                                                  |
   |                                                                                                                                         |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                                         |                       |    -  Format: *::::*. For example, **obs:::bucket:\***. Asterisks are allowed.                                                                                                                                                             |
   |                                                                                                                                         |                       |    -  The region segment can be **\*** or a region accessible to the user. The specified resource must belong to the corresponding service that actually exists.                                                                           |
   |                                                                                                                                         |                       |    -  In the case of a custom policy for agencies, the type of this parameter is Object, and the value should be set to *"Resource": {"uri": ["/iam/agencies/07805acaba800fdd4fbdc00b8f888c7c"]}*.                                         |
   +-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicystatementarritemcondition:

.. table:: **Table 8** role.policy.Statement.Condition

   +------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------+
   | Parameter                                                                                                                                      | Type                  | Description                                   |
   +================================================================================================================================================+=======================+===============================================+
   | :ref:`operator <iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicystatementarritemconditionoperator>` | Object                | Operator, for example, Bool and StringEquals. |
   |                                                                                                                                                |                       |                                               |
   |                                                                                                                                                |                       | -  The parameter type is custom object.       |
   +------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------+

.. _iam_02_0012__en-us_topic_0222393170_en-us_topic_0222037549_response_rs111rolesarritempolicystatementarritemconditionoperator:

.. table:: **Table 9** role.policy.Statement.Condition.operator

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                             |
   +=======================+=======================+=========================================================================================================================+
   | attribute             | Array of strings      | Condition key. The condition key must correspond to the specified operator. A maximum of 10 condition keys are allowed. |
   |                       |                       |                                                                                                                         |
   |                       |                       | -  The parameter type is custom character string array.                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://iam.eu-de.otc.t-systems.com/v3.0/OS-ROLE/roles/{role_id}

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
       "role": {
           "domain_id": "d78cbac186b744899480f25bd02...",
           "references": 0,
           "description_cn": "Policy description",
           "catalog": "CUSTOMED",
           "name": "custom_d78cbac186b744899480f25bd022f468_11",
           "description": "IAMDescription",
           "links": {
               "self": "https://iam.eu-de.otc.t-systems.com/v3/roles/a24a71dcc41f4da989c2a1c900b52d1a"
           },
           "id": "a24a71dcc41f4da989c2a1c900b52d1a",
           "display_name": "IAMCloudServicePolicy",
           "type": "AX",
           "policy": {
               "Version": "1.1",
               "Statement": [
                   {
                       "Condition": {
                           "StringStartWith": {
                               "g:ProjectName": [
                                   "eu-de"
                               ]
                           }
                       },
                       "Action": [
                           "obs:bucket:GetBucketAcl"
                       ],
                       "Resource": [
                           "obs:*:*:bucket:*"
                       ],
                       "Effect": "Allow"
                   }
               ]
           }
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
500         Internal server error.
=========== =========================================

Error Codes
-----------

None
