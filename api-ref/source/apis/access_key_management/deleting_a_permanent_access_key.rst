:original_name: iam_03_0005.html

.. _iam_03_0005:

Deleting a Permanent Access Key
===============================

Function
--------

This API can be used by the administrator to delete the specified permanent access key of an IAM user or used by an IAM user to delete one of their permanent access keys.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

DELETE /v3.0/OS-CREDENTIAL/credentials/{access_key}

.. table:: **Table 1** URI parameters

   ========== ========= ====== =================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =================
   access_key Yes       String AK to be deleted.
   ========== ========= ====== =================

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================+
   | Content-Type    | Yes             | String          | Fill **application/json;charset=utf8** in this field.                                                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | A token with **Security Administrator** permissions is required if the administrator is requesting to delete a specified permanent access key of an IAM user. |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | The user token (no special permission requirements) of an IAM user is required if the user is requesting to delete one of their permanent access keys.        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://sample.domain.com/v3.0/OS-CREDENTIAL/credentials/{access_key}

Example Response
----------------

None

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
204         The access key is deleted successfully.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =========================================

Error Codes
-----------

None
