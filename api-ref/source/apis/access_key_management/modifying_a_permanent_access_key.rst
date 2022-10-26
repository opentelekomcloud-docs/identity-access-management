:original_name: iam_03_0004.html

.. _iam_03_0004:

Modifying a Permanent Access Key
================================

Function
--------

This API can be used by the administrator to modify the specified permanent access key of an IAM user or used by an IAM user to modify one of their permanent access keys.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

PUT /v3.0/OS-CREDENTIAL/credentials/{access_key}

.. table:: **Table 1** URI parameters

   ========== ========= ====== ====================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ====================================
   access_key Yes       String AK of the access key to be modified.
   ========== ========= ====== ====================================

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================+
   | Content-Type    | Yes             | String          | Fill **application/json;charset=utf8** in this field.                                                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator** permissions is required if the administrator is requesting to modify a specified permanent access key of an IAM user. |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | The user token (no special permission requirements) of an IAM user is required if the user is requesting to modify one of their permanent access keys.        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Parameters in the request body

   +-------------------------------------------------------------------------------------------------------+-----------+--------+-----------------------------+
   | Parameter                                                                                             | Mandatory | Type   | Description                 |
   +=======================================================================================================+===========+========+=============================+
   | :ref:`credential <iam_03_0004__en-us_topic_0221566839_en-us_topic_0221482390_request_rq45credential>` | Yes       | Object | Authentication information. |
   +-------------------------------------------------------------------------------------------------------+-----------+--------+-----------------------------+

.. _iam_03_0004__en-us_topic_0221566839_en-us_topic_0221482390_request_rq45credential:

.. table:: **Table 4** credential

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | status          | No              | String          | Status of the access key to be changed to The value can be **active** or **inactive**. |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Options:                                                                               |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | -  active                                                                              |
   |                 |                 |                 | -  inactive                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | description     | No              | String          | Description of the access key                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 5** Parameters in the response body

   +--------------------------------------------------------------------------------------------------------+--------+-----------------------------+
   | Parameter                                                                                              | Type   | Description                 |
   +========================================================================================================+========+=============================+
   | :ref:`credential <iam_03_0004__en-us_topic_0221566839_en-us_topic_0221482390_response_rs45credential>` | Object | Authentication information. |
   +--------------------------------------------------------------------------------------------------------+--------+-----------------------------+

.. _iam_03_0004__en-us_topic_0221566839_en-us_topic_0221482390_response_rs45credential:

.. table:: **Table 6** credential

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

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-CREDENTIAL/credentials/{access_key}

.. code-block::

   {
       "credential": {
           "status": "inactive",
           "description": "IAMDescription"
       }
   }

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
       "credential": {
           "status": "inactive",
           "access": "LOSZM4YRVLKOY9...",
           "create_time": "2020-01-08T06:26:08.123059Z",
           "user_id": "07609fb9358010e21f7bc00375..."
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
