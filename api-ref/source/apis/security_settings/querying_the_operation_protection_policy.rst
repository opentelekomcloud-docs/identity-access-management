:original_name: iam_02_0022.html

.. _iam_02_0022:

Querying the Operation Protection Policy
========================================

Function
--------

This API is used to query the operation protection policy.

URI
---

GET /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/protect-policy

.. table:: **Table 1** URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   domain_id Yes       String Domain ID.
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Parameters in the response body

   +---------------------------------------------------------+--------+------------------------------+
   | Parameter                                               | Type   | Description                  |
   +=========================================================+========+==============================+
   | :ref:`protect_policy <iam_02_0022__table1543815262192>` | object | Operation protection policy. |
   +---------------------------------------------------------+--------+------------------------------+

.. _iam_02_0022__table1543815262192:

.. table:: **Table 4** protect_policy

   +----------------------+---------+--------------------------------------------------------------------------------------------------+
   | Parameter            | Type    | Description                                                                                      |
   +======================+=========+==================================================================================================+
   | operation_protection | Boolean | Indicates whether operation protection has been enabled. The value can be **true** or **false**. |
   +----------------------+---------+--------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/protect-policy

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "protect_policy" : {
       "operation_protection" : false
     }
   }

**Status code: 403**

Access denied.

-  Example 1

.. code-block::

   {
      "error_msg" : "You are not authorized to perform the requested action.",
      "error_code" : "IAM.0002"
    }

-  Example 2

.. code-block::

   {
      "error_msg" : "Policy doesn't allow %(actions)s to be performed.",
      "error_code" : "IAM.0003"
    }

**Status code: 404**

The requested resource cannot be found.

.. code-block::

   {
     "error_msg" : "Could not find %(target)s: %(target_id)s.",
     "error_code" : "IAM.0004"
   }

**Status code: 500**

Internal server error.

.. code-block::

   {
     "error_msg" : "An unexpected error prevented the server from fulfilling your request.",
     "error_code" : "IAM.0006"
   }

Status Codes
------------

=========== =======================================
Status Code Description
=========== =======================================
200         The request is successful.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =======================================
