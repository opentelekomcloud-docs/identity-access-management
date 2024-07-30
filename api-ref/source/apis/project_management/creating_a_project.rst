:original_name: en-us_topic_0066154565.html

.. _en-us_topic_0066154565:

Creating a Project
==================

Function
--------

This API is used to create a project.

URI
---

POST /v3/projects

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

-  Parameters in the request body

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                      |
   +=================+=================+=================+==================================================================================================================+
   | name            | Yes             | String          | Project name, which must start with "*ID of an existing region*\ \_" and be less than or equal to 64 characters. |
   |                 |                 |                 |                                                                                                                  |
   |                 |                 |                 | Example: *{region_id}*\ \_test1                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | parent_id       | Yes             | String          | Parent project ID to which a project belongs.                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | domain_id       | No              | String          | ID of the domain that a project belongs to.                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Project description, which can contain a maximum of 255 characters.                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X POST -d '{"project":{"domain_id":"acf2ffabba974fae8f30378ffde2c...","name":"region_test1"}}' https://sample.domain.com/v3/projects

Response Parameters
-------------------

Example response

.. code-block::

   {
       "project": {
           "is_domain": false,
           "description": "",
           "links": {
               "self": "https://sample.domain.com/v3/projects/3de1461665f045ef91ba1efe8121b979"
           },
           "enabled": true,
           "id": "3de1461665f045ef91ba1efe8121b979",
           "parent_id": "d1294857fdf64251994892b344f53e88",
           "domain_id": "d1294857fdf64251994892b344f53e88",
           "name": "region_test1"
       }
   }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
201         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
409         Duplicate project name.
=========== =========================================
