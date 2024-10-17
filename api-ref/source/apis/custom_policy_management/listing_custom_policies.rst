:original_name: iam_02_0011.html

.. _iam_02_0011:

Listing Custom Policies
=======================

Function
--------

This API is provided for the administrator to list all custom policies.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

GET /v3.0/OS-ROLE/roles

.. table:: **Table 1** Query parameters

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                              |
   +===========+===========+=========+==========================================================================================================================================+
   | page      | No        | Integer | Page number for pagination query. The minimum value is **1**. This parameter must be used together with **per_page**.                    |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------+
   | per_page  | No        | Integer | Number of data records to be displayed on each page. The value ranges from 1 to 300. This parameter must be used together with **page**. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-------------------------------------------------------------------------------+------------------+-------------------------------------------+
   | Parameter                                                                     | Type             | Description                               |
   +===============================================================================+==================+===========================================+
   | :ref:`links <iam_02_0011__en-us_topic_0222037472_response_rs111links>`        | Object           | Resource link information.                |
   +-------------------------------------------------------------------------------+------------------+-------------------------------------------+
   | :ref:`roles <iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritem>` | Array of objects | Custom policy information.                |
   +-------------------------------------------------------------------------------+------------------+-------------------------------------------+
   | total_number                                                                  | Integer          | Total number of custom policies returned. |
   +-------------------------------------------------------------------------------+------------------+-------------------------------------------+

.. _iam_02_0011__en-us_topic_0222037472_response_rs111links:

.. table:: **Table 4** links

   ========= ====== =======================
   Parameter Type   Description
   ========= ====== =======================
   self      String Resource link.
   previous  String Previous resource link.
   next      String Next resource link.
   ========= ====== =======================

.. _iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritem:

.. table:: **Table 5** roles

   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                            | Type                  | Description                                                                                                                            |
   +======================================================================================+=======================+========================================================================================================================================+
   | domain_id                                                                            | String                | ID of the domain which the custom policy belongs to.                                                                                   |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | references                                                                           | Integer               | Number of references.                                                                                                                  |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | updated_time                                                                         | String                | Time when the custom policy was last updated.                                                                                          |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | created_time                                                                         | String                | Time when the custom policy was created.                                                                                               |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | description_cn                                                                       | String                | Description of the custom policy.                                                                                                      |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | catalog                                                                              | String                | Service catalog.                                                                                                                       |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                                                 | String                | Name of the custom policy.                                                                                                             |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | description                                                                          | String                | Description of the custom policy.                                                                                                      |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`links <iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritemlinks>`   | Object                | Resource link of the custom policy.                                                                                                    |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | id                                                                                   | String                | Policy ID.                                                                                                                             |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | display_name                                                                         | String                | Display name of the custom policy.                                                                                                     |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | type                                                                                 | String                | Display mode.                                                                                                                          |
   |                                                                                      |                       |                                                                                                                                        |
   |                                                                                      |                       | .. note::                                                                                                                              |
   |                                                                                      |                       |                                                                                                                                        |
   |                                                                                      |                       |    -  **AX**: Account level.                                                                                                           |
   |                                                                                      |                       |    -  **XA**: Project level.                                                                                                           |
   |                                                                                      |                       |    -  The display mode of a custom policy can only be **AX** or **XA**. A custom policy must be displayed at either of the two levels. |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`policy <iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicy>` | Object                | Content of custom policy.                                                                                                              |
   +--------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritemlinks:

.. table:: **Table 6** roles.links

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   self      String Resource link.
   ========= ====== ==============

.. _iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicy:

.. table:: **Table 7** roles.policy

   +---------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                               | Type                  | Description                                                                                                                                   |
   +=========================================================================================================+=======================+===============================================================================================================================================+
   | Version                                                                                                 | String                | Policy version.                                                                                                                               |
   |                                                                                                         |                       |                                                                                                                                               |
   |                                                                                                         |                       | .. note::                                                                                                                                     |
   |                                                                                                         |                       |                                                                                                                                               |
   |                                                                                                         |                       |    -  **1.0**: System-defined role. Only a limited number of service-level roles are provided for authorization.                              |
   |                                                                                                         |                       |    -  **1.1**: Policy. A policy defines the permissions required to perform operations on a specific cloud resource under certain conditions. |
   +---------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Statement <iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicystatementarritem>` | Array of objects      | Statement of the policy. A policy can contain a maximum of eight statements.                                                                  |
   +---------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicystatementarritem:

.. table:: **Table 8** roles.policy.Statement

   +------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                        | Type                  | Description                                                                                                                                                                                                                                |
   +==================================================================================================================+=======================+============================================================================================================================================================================================================================================+
   | Action                                                                                                           | Array of strings      | Specific operation permission on a resource. A maximum of 100 actions are allowed.                                                                                                                                                         |
   |                                                                                                                  |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                  |                       | .. note::                                                                                                                                                                                                                                  |
   |                                                                                                                  |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                  |                       |    -  The value format is *Service name*:*Resource type*:*Operation*, for example, **vpc:ports:create**.                                                                                                                                   |
   |                                                                                                                  |                       |    -  *Service name*: indicates the product name, such as **ecs**, **evs**, or **vpc**. Only lowercase letters are allowed. Resource types and operations are not case-sensitive. You can use an asterisk (*) to represent all operations. |
   |                                                                                                                  |                       |    -  For a custom policy for agencies, this parameter should be set to *"Action": ["iam:agencies:assume"]*.                                                                                                                               |
   +------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Effect                                                                                                           | String                | Effect of the permission. The value can be **Allow** or **Deny**. If both Allow and Deny statements are found in a policy, the authentication starts from the Deny statements.                                                             |
   +------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Condition <iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicystatementarritemcondition>` | Object                | Conditions for the permission to take effect. A maximum of 10 conditions are allowed.                                                                                                                                                      |
   +------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource                                                                                                         | Array of strings      | Cloud resource. The array can contain a maximum of 10 resource strings, and each string cannot exceed 128 characters.                                                                                                                      |
   |                                                                                                                  |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                  |                       | .. note::                                                                                                                                                                                                                                  |
   |                                                                                                                  |                       |                                                                                                                                                                                                                                            |
   |                                                                                                                  |                       |    -  Format: *::::*. For example, **obs:::bucket:\***. Asterisks are allowed.                                                                                                                                                             |
   |                                                                                                                  |                       |    -  The region segment can be **\*** or a region accessible to the user. The specified resource must belong to the corresponding service that actually exists.                                                                           |
   |                                                                                                                  |                       |    -  In the case of a custom policy for agencies, the type of this parameter is Object, and the value should be set to *"Resource": {"uri": ["/iam/agencies/07805acaba800fdd4fbdc00b8f888c7c"]}*.                                         |
   +------------------------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicystatementarritemcondition:

.. table:: **Table 9** roles.policy.Statement.Condition

   +-------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------+
   | Parameter                                                                                                               | Type                  | Description                                   |
   +=========================================================================================================================+=======================+===============================================+
   | :ref:`operator <iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicystatementarritemconditionoperator>` | Object                | Operator, for example, Bool and StringEquals. |
   |                                                                                                                         |                       |                                               |
   |                                                                                                                         |                       | The parameter type is custom object.          |
   +-------------------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------+

.. _iam_02_0011__en-us_topic_0222037472_response_rs111rolesarritempolicystatementarritemconditionoperator:

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

   GET https://sample.domain.com/v3.0/OS-ROLE/roles

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "roles" : [ {
       "domain_id" : "d78cbac186b744899480f25bd022f...",
       "updated_time" : "1579229246886",
       "created_time" : "1579229246886",
       "description_cn" : "Description in Chinese",
       "catalog" : "CUSTOMED",
       "name" : "custom_d78cbac186b744899480f25bd022f468_1",
       "description" : "IAMDescription",
       "links" : {
         "self" : "https://sample.domain.com/v3/roles/93879fd90f1046f69e6e0b31c94d2..."
       },
       "id" : "93879fd90f1046f69e6e0b31c94d2...",
       "display_name" : "IAMCloudServicePolicy",
       "type" : "AX",
       "policy" : {
         "Version" : "1.1",
         "Statement" : [ {
           "Condition" : {
             "StringStartWith" : {
               "g:ProjectName" : [ "AZ-1" ]
             }
           },
           "Action" : [ "obs:bucket:GetBucketAcl" ],
           "Resource" : [ "obs:*:*:bucket:*" ],
           "Effect" : "Allow"
         } ]
       }
     }, {
       "domain_id" : "d78cbac186b744899480f25bd022f...",
       "updated_time" : "1579229242358",
       "created_time" : "1579229242358",
       "description_cn" : "Description in Chinese",
       "catalog" : "CUSTOMED",
       "name" : "custom_d78cbac186b744899480f25bd022f468_0",
       "description" : "IAMDescription",
       "links" : {
         "self" : "https://sample.domain.com/v3/roles/f67224e84dc849ab954ce29fb4f47..."
       },
       "id" : "f67224e84dc849ab954ce29fb4f473...",
       "display_name" : "IAMAgencyPolicy",
       "type" : "AX",
       "policy" : {
         "Version" : "1.1",
         "Statement" : [ {
           "Action" : [ "iam:agencies:assume" ],
           "Resource" : {
             "uri" : [ "/iam/agencies/07805acaba800fdd4fbdc00b8f888..." ]
           },
           "Effect" : "Allow"
         } ]
       }
     } ],
     "links" : {
       "next" : null,
       "previous" : null,
       "self" : "https://sample.domain.com/v3/roles?domain_id=d78cbac186b744899480f25bd022f..."
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
500         Internal server error.
=========== =========================================

Error Codes
-----------

None
