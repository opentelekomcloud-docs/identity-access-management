:original_name: iam_11_0003.html

.. _iam_11_0003:

Querying Role Assignments
=========================

Function
--------

This API is used to query the user groups to which a specified role has been assigned.

URI
---

-  URI format

   GET /v3/role_assignments{?role.id,user.id,group.id,scope.project.id,scope.domain.id, scope.OS-INHERIT:inherited_to,include_subtree}

-  URI parameters: Specify any of the **role.id**, **user.id**, **group.id**, **scope.project.id**, and **scope.domain.id** parameters.

   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                     | Mandatory       | Type            | Description                                                                                                                                                                      |
   +===============================+=================+=================+==================================================================================================================================================================================+
   | role.id                       | No              | String          | Role ID.                                                                                                                                                                         |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | This parameter must be specified in conjunction with any of **user.id**, **group.id**, **scope.project.id**, and **scope.domain.id**.                                            |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user.id                       | No              | String          | User ID.                                                                                                                                                                         |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | This parameter cannot be specified in conjunction with **group.id**.                                                                                                             |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group.id                      | No              | String          | User group ID.                                                                                                                                                                   |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | This parameter cannot be specified in conjunction with **user.id**.                                                                                                              |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scope.project.id              | No              | String          | Project ID.                                                                                                                                                                      |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | This parameter cannot be specified in conjunction with **scope.domain.id**.                                                                                                      |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scope.domain.id               | No              | String          | Domain ID.                                                                                                                                                                       |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | This parameter cannot be specified in conjunction with **scope.project.id**.                                                                                                     |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scope.OS-INHERIT:inherited_to | No              | String          | Used to filter based on role assignments that are inherited.                                                                                                                     |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | The only value of this parameter that is currently supported is **projects**.                                                                                                    |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | include_subtree               | No              | Boolean         | The value **true** means listing all role assignments involving the specified project and all subprojects. Any non-zero value of this parameter will be interpreted as **true**. |
   |                               |                 |                 |                                                                                                                                                                                  |
   |                               |                 |                 | This parameter must be specified in conjunction with **scope.project.id**.                                                                                                       |
   +-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/role_assignments?group.id=06c904fddd807cd93f0ec018b5d30a34&role.id=bc61db25975247758de0d5e254a85915&scope.domain.id=06c904fdca807cd90f0ac018001...

Response Parameters
-------------------

-  Parameters in the response body

   ================ ========= ==== ===================
   Parameter        Mandatory Type Description
   ================ ========= ==== ===================
   role_assignments Yes       List Role assignments.
   links            Yes       Dict Role resource link.
   ================ ========= ==== ===================

-  role_assignments

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | scope           | Yes             | Dict            | Application scope of the role. The value can be **domain** or **project**.                         |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Domain:                                                                                            |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | .. code-block::                                                                                    |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 |    "scope": {                                                                                      |
   |                 |                 |                 |           "domain": {                                                                              |
   |                 |                 |                 |                "id": "06c9..."                                                                     |
   |                 |                 |                 |                         }                                                                          |
   |                 |                 |                 |                 }                                                                                  |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Project:                                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | .. code-block::                                                                                    |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 |    "scope": {                                                                                      |
   |                 |                 |                 |           "project": {                                                                             |
   |                 |                 |                 |                "id": "06c9..."                                                                     |
   |                 |                 |                 |                         }                                                                          |
   |                 |                 |                 |                 }                                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | role            | Yes             | Dict            | Role information, including the role ID.                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Example:                                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | .. code-block::                                                                                    |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 |    "role": {                                                                                       |
   |                 |                 |                 |           " id ": " bc61..."                                                                       |
   |                 |                 |                 |                }                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | group           | No              | Dict            | Group information, which is returned if the role has been assigned to a user group.                |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Example:                                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | .. code-block::                                                                                    |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 |    "group": {                                                                                      |
   |                 |                 |                 |           " id ": " 06c9..."                                                                       |
   |                 |                 |                 |                }                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | agency          | No              | Dict            | Group information, which is returned if the role has been assigned to an agency.                   |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Example:                                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | .. code-block::                                                                                    |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 |    "agency": {                                                                                     |
   |                 |                 |                 |           " id ": " 06c9..."                                                                       |
   |                 |                 |                 |                }                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | links           | Yes             | Dict            | Assignment resource link information.                                                              |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Example:                                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | .. code-block::                                                                                    |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 |    "links": {                                                                                      |
   |                 |                 |                 |           "assignment": "https://sample.domain.com/v3/projects/06c9../groups/06c9../roles/bc61.. " |
   |                 |                 |                 |                }                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+

-  links

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                              |
   +=================+=================+=================+==========================================================================+
   | self            | Yes             | String          | Resource link.                                                           |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Example:                                                                 |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | "self": "https://sample.domain.com/v3/role_assignments? group.id=06c..." |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | previous        | Yes             | String          | Previous resource link.                                                  |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Example:                                                                 |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | "previous": null                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | next            | No              | String          | Next resource link.                                                      |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Example:                                                                 |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | "next": null                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "role_assignments": [
              {
                  "scope": {
                      "domain": {
                          "id": "06c904fdca807cd90f0ac01800167760"
                      }
                  },
                  "role": {
                      "id": "bc61db25975247758de0d5e254a85915"
                  },
                  "group": {
                      "id": "06c904fddd807cd93f0ec018b5d30a34"
                  },
                  "links": {
                      "assignment": "https://sample.domain.com/v3/domains/06c904fdca807cd90f0ac01800167760/groups/06c904fddd807cd93f0ec018b5d30a34/roles/bc61db25975247758de0d5e254a85915"
                  }
              }
          ],
          "links": {
              "self": "https://sample.domain.com/v3/role_assignments?group.id=06c904fddd807cd93f0ec018b5d30a34&role.id=bc61db25975247758de0d5e254a85915&scope.domain.id=06c904fdca807cd90f0ac01800167760",
              "previous": null,
              "next": null
          }
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 200         | The request is successful.                                                     |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                        |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
