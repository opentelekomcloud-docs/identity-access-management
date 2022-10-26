:original_name: iam_02_0015.html

.. _iam_02_0015:

Deleting a Custom Policy
========================

Function
--------

This API is provided for the administrator to delete a custom policy.

The API can be called using both the global endpoint and region-specific endpoints.

URI
---

DELETE /v3.0/OS-ROLE/roles/{role_id}

.. table:: **Table 1** URI parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                      |
   +===========+===========+========+==================================================================================================================+
   | role_id   | Yes       | String | Custom policy ID. For details about how to obtain a custom policy ID, see :ref:`Custom Policy ID <iam_02_0011>`. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

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

None

Example Request
---------------

.. code-block:: text

   DELETE https://iam.eu-de.otc.t-systems.com/v3.0/OS-ROLE/roles/{role_id}

Example Response
----------------

None

Status Codes
------------

=========== ==========================================
Status Code Description
=========== ==========================================
200         The custom policy is deleted successfully.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
500         Internal server error.
=========== ==========================================

Error Codes
-----------

None
