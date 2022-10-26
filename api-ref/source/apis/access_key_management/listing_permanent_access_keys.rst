:original_name: iam_03_0003.html

.. _iam_03_0003:

Listing Permanent Access Keys
=============================

Function
--------

This API can be used by the administrator to list all permanent access key of an IAM user or used by an IAM user to list all of their permanent access keys.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

GET /v3.0/OS-CREDENTIAL/credentials

.. table:: **Table 1** Query parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   No        String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================+
   | Content-Type    | Yes             | String          | Fill **application/json;charset=utf8** in this field.                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator** permissions is required if the administrator is requesting to query all permanent access keys of an IAM user. |
   |                 |                 |                 |                                                                                                                                                       |
   |                 |                 |                 | The user token (no special permission requirements) of an IAM user is required if the user is requesting to query their permanent access keys.        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Parameters in the response body

   +-----------------------------------------------------------------------------------------------------------------+------------------+------------------------+
   | Parameter                                                                                                       | Type             | Description            |
   +=================================================================================================================+==================+========================+
   | :ref:`credentials <iam_03_0003__en-us_topic_0221566837_en-us_topic_0221482413_response_rs43credentialsarritem>` | Array of objects | Authentication result. |
   +-----------------------------------------------------------------------------------------------------------------+------------------+------------------------+

.. _iam_03_0003__en-us_topic_0221566837_en-us_topic_0221482413_response_rs43credentialsarritem:

.. table:: **Table 4** credentials

   =========== ====== =====================================
   Parameter   Type   Description
   =========== ====== =====================================
   user_id     String IAM user ID.
   access      String AK.
   status      String Status of the access key.
   create_time String Time when the access key was created.
   description String Description of the access key.
   =========== ====== =====================================

Example Request
---------------

-  Request for an IAM user to query their permanent access keys

   .. code-block:: text

      GET https://sample.domain.com/v3.0/OS-CREDENTIAL/credentials

-  Request for an administrator to query all permanent access keys of an IAM user (user ID: **07609fb9358010e21f7bc003751c...**)

   .. code-block:: text

      GET https://sample.domain.com/v3.0/OS-CREDENTIAL/credentials?user_id=07609fb9358010e21f7bc0037....

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
       "credentials": [
           {
               "access": "LOSZM4YRVLKOY9E8X...",
               "create_time": "2020-01-08T06:26:08.123059Z",
               "user_id": "07609fb9358010e21f7bc0037...",
               "description": "",
               "status": "active"
           },
           {
               "access": "P83EVBZJMXCYTMU...",
               "create_time": "2020-01-08T06:25:19.014028Z",
               "user_id": "07609fb9358010e21f7bc003751...",
               "description": "",
               "status": "active"
           }
       ]
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
404         The requested resource cannot be found.
500         Internal server error.
=========== =========================================

Error Codes
-----------

None
