:original_name: en-us_topic_0066154566.html

.. _en-us_topic_0066154566:

Modifying Project Data
======================

Function
--------

This API is used to modify project information.

URI
---

-  URI format

   PATCH /v3/projects/{project_id}

-  URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

-  Parameters in the request header

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | Content-Type    | Yes             | String          | Text type and encoding mode.                                        |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | Fill **application/json;charset=utf8** in this field.               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Authenticated token with the **Security Administrator** permission. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

-  Parameters in the request body

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | name            | No              | String          | Project name, which must start with the ID of an existing region and be less than or equal to 64 characters. |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Example: *{region}*\ **\_test2**                                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Project description, which can contain a maximum of 255 characters.                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

-  Example Request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X PATCH -d '{"project":{"name":"region_test2","description":"test_project_desc"}}' https://sample.domain.com/v3/projects/23da5961c8214f5caf701c27d9703959

Response Parameters
-------------------

Example Response

.. code-block::

   {
       "project": {
           "is_domain": false,
           "description": "test_project_desc",
           "links": {
               "self": "https://sample.domain.com/v3/projects/23da5961c8214f5caf701c27d9703959"
           },
           "enabled": true,
           "id": "23da5961c8214f5caf701c27d9703959",
           "parent_id": "d1294857fdf64251994892b344f53e88",
           "domain_id": "d1294857fdf64251994892b344f53e88",
           "name": "region_test2"
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
409         Duplicate project name.
=========== =========================================
