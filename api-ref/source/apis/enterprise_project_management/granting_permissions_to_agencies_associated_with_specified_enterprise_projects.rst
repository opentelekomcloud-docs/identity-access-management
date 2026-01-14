:original_name: iam_02_0633.html

.. _iam_02_0633:

Granting Permissions to Agencies Associated with Specified Enterprise Projects
==============================================================================

Function
--------

This API is used to grant permissions to agencies associated with specified enterprise projects.

URI
---

PUT /v3.0/OS-PERMISSION/subjects/agency/scopes/enterprise-project/role-assignments

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                  |
   +==============+===========+========+==============================================================================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.                                                                        |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with **iam:permissions:grantRoleToAgencyOnEnterpriseProject** or **Security Administrator** permissions. |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters in the request body

   +----------------------------------------------------------------------------------------------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                      | Mandatory | Type             | Description                                                                                               |
   +================================================================================================================+===========+==================+===========================================================================================================+
   | :ref:`role_assignments <iam_02_0633__en-us_topic_0000001491323110_en-us_topic_0222594411_request_rq123agency>` | Yes       | Array of objects | Association between agencies and enterprise projects. A maximum of 250 association records are supported. |
   +----------------------------------------------------------------------------------------------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------+

.. _iam_02_0633__en-us_topic_0000001491323110_en-us_topic_0222594411_request_rq123agency:

.. table:: **Table 3** role_assignments

   ===================== ========= ====== ======================
   Parameter             Mandatory Type   Description
   ===================== ========= ====== ======================
   agency_id             Yes       String Agency ID.
   enterprise_project_id Yes       String Enterprise project ID.
   role_id               Yes       String Policy ID.
   ===================== ========= ====== ======================

Response Parameters
-------------------

None

Example Request
---------------

Request for granting permissions to agencies associated with a specified enterprise project

.. code-block:: text

   PUT /v3.0/OS-PERMISSION/subjects/agency/scopes/enterprise-project/role-assignments
   {
     "role_assignments": [
       {
         "agency_id": "as0d9f8asdfasdfa09sd8f9aaa",
         "enterprise_project_id": "3asdfs0d9f8asdfasdfa09sd8f9aaa",
         "role_id": "5s0d9f8dafsdfasdfa09sd8f9aaa"
       }
     ]
   }

Example Response
----------------

**Status code: 200**

The request is successful.

**Status code: 400**

Parameter error.

.. code-block::

   {
     "error" : {
       "message" : "Illegal request",
       "code" : 400,
       "title" : "Bad Request"
     }
   }

**Status code: 401**

Authentication failed.

.. code-block::

   {
     "error" : {
       "message" : "Authentication failed",
       "code" : 401,
       "title" : "Unauthorized"
     }
   }

**Status code: 403**

Operation denied.

.. code-block::

   {
     "error" : {
       "message" : "Forbidden operation",
       "code" : 403,
       "title" : "Forbidden"
     }
   }

Status Codes
------------

=========== ==========================
Status Code Description
=========== ==========================
200         The request is successful.
400         Parameter error.
401         Authentication failed.
403         Unauthorized operation.
500         Internal server error.
=========== ==========================
