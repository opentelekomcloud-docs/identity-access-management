:original_name: iam_03_0002.html

.. _iam_03_0002:

Querying a Permanent Access Key
===============================

Function
--------

This API can be used by the administrator to query the specified permanent access key of an IAM user or used by an IAM user to query one of their permanent access keys.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

GET /v3.0/OS-CREDENTIAL/credentials/{access_key}

.. table:: **Table 1** URI parameters

   ========== ========= ====== ===================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================================
   access_key Yes       String AK of the access key to be queried.
   ========== ========= ====== ===================================

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================+
   | Content-Type    | Yes             | String          | Fill **application/json;charset=utf8** in this field.                                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator** permissions is required if the administrator is requesting to query a specified permanent access key of an IAM user. |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | The user token (no special permission requirements) of an IAM user is required if the user is requesting to query one of their permanent access keys.        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Parameters in the response body

   +--------------------------------------------------------------------------------------------------------+--------+------------------------+
   | Parameter                                                                                              | Type   | Description            |
   +========================================================================================================+========+========================+
   | :ref:`credential <iam_03_0002__en-us_topic_0221566838_en-us_topic_0221482383_response_rs44credential>` | Object | Authentication result. |
   +--------------------------------------------------------------------------------------------------------+--------+------------------------+

.. _iam_03_0002__en-us_topic_0221566838_en-us_topic_0221482383_response_rs44credential:

.. table:: **Table 4** credential

   ============= ====== =======================================
   Parameter     Type   Description
   ============= ====== =======================================
   user_id       String IAM user ID.
   access        String AK.
   status        String Status of the access key.
   create_time   String Time when the access key was created.
   last_use_time String Time when the access key was last used.
   description   String Description of the access key.
   ============= ====== =======================================

Example Request
---------------

.. code-block::

    GET https://sample.domain.com/v3.0/OS-CREDENTIAL/credentials/{access_key}

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
       "credential": {
           "last_use_time": "2020-01-08T06:26:08.123059Z",
           "access": "LOSZM4YRVLKOY9E8...",
           "create_time": "2020-01-08T06:26:08.123059Z",
           "user_id": "07609fb9358010e21f7bc003751...",
           "description": "",
           "status": "active"
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
404         The requested resource cannot be found.
500         Internal server error.
=========== =========================================

Error Codes
-----------

None
