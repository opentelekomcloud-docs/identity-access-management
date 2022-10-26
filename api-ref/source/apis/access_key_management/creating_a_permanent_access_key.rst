:original_name: iam_03_0001.html

.. _iam_03_0001:

Creating a Permanent Access Key
===============================

Function
--------

This API can be used by the administrator to create a permanent access key for an IAM user or used by an IAM user to create a permanent access key for itself.

Access keys are identity credentials for using development tools (APIs, CLI, and SDKs) to access the cloud system. Access keys cannot be used to log in to the console. AK is used in conjunction with an SK to sign requests cryptographically, ensuring that the requests are secret, complete, and correct.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

POST /v3.0/OS-CREDENTIAL/credentials

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================+
   | Content-Type    | Yes             | String          | Fill **application/json;charset=utf8** in this field.                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator permissions** is required if the administrator is requesting to create a permanent access key for an IAM user.  |
   |                 |                 |                 |                                                                                                                                                       |
   |                 |                 |                 | The user token (no special permission requirements) of an IAM user is required if the user is requesting to create a permanent access key for itself. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters in the request body

   +-------------------------------------------------------------------------------------------------------+-----------+--------+-----------------------------+
   | Parameter                                                                                             | Mandatory | Type   | Description                 |
   +=======================================================================================================+===========+========+=============================+
   | :ref:`credential <iam_03_0001__en-us_topic_0221566836_en-us_topic_0221482442_request_rq42credential>` | Yes       | Object | Authentication information. |
   +-------------------------------------------------------------------------------------------------------+-----------+--------+-----------------------------+

.. _iam_03_0001__en-us_topic_0221566836_en-us_topic_0221482442_request_rq42credential:

.. table:: **Table 3** credential

   =========== ========= ====== ==============================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ==============================
   user_id     Yes       String IAM user ID.
   description No        String Description of the access key.
   =========== ========= ====== ==============================

Response Parameters
-------------------

.. table:: **Table 4** Parameters in the response body

   +--------------------------------------------------------------------------------------------------------+--------+------------------------+
   | Parameter                                                                                              | Type   | Description            |
   +========================================================================================================+========+========================+
   | :ref:`credential <iam_03_0001__en-us_topic_0221566836_en-us_topic_0221482442_response_rs42credential>` | Object | Authentication result. |
   +--------------------------------------------------------------------------------------------------------+--------+------------------------+

.. _iam_03_0001__en-us_topic_0221566836_en-us_topic_0221482442_response_rs42credential:

.. table:: **Table 5** credential

   =========== ====== =====================================
   Parameter   Type   Description
   =========== ====== =====================================
   create_time String Time when the access key was created.
   access      String AK.
   secret      String SK.
   status      String Status of the access key.
   user_id     String IAM user ID.
   description String Description of the access key.
   =========== ====== =====================================

Example Request
---------------

.. code-block:: text

   POST https://sample.domain.com/v3.0/OS-CREDENTIAL/credentials

.. code-block::

   {
       "credential": {
           "description": "IAMDescription",
           "user_id": "07609fb9358010e21f7bc003751c7c32"
       }
   }

Example Response
----------------

**Status code: 201**

The request is successful.

.. code-block::

   {
       "credential": {
           "access": "P83EVBZJMXCYTMUII...",
           "create_time": "2020-01-08T06:25:19.014028Z",
           "user_id": "07609fb9358010e21f7bc003751...",
           "description": "IAMDescription",
           "secret": "TTqAHPbhWorg9ozx8Dv9MUyzYnOKDppxzHt...",
           "status": "active"
       }
   }

**Status code: 400**

The server failed to process the request. (The number of access keys has reached the maximum allowed limit.)

.. code-block::

   {
       "error": {
           "message": "akSkNumExceed",
           "code": 400,
           "title": "Bad Request"
       }
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                  |
+=============+==============================================================================================================+
| 201         | The request is successful.                                                                                   |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request. (The number of access keys has reached the maximum allowed limit.) |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                                                       |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 403         | Access denied.                                                                                               |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 500         | Internal server error.                                                                                       |
+-------------+--------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

None
