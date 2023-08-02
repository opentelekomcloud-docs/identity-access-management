:original_name: iam_02_0021.html

.. _iam_02_0021:

Modifying the Operation Protection Policy
=========================================

Function
--------

This API is provided for the administrator to modify the operation protection policy.

URI
---

PUT /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/protect-policy

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

.. table:: **Table 3** Parameters in the request body

   +-------------------------------------------------------+-----------+--------+------------------------------+
   | Parameter                                             | Mandatory | Type   | Description                  |
   +=======================================================+===========+========+==============================+
   | :ref:`protect_policy <iam_02_0021__table54451161197>` | Yes       | object | Operation protection policy. |
   +-------------------------------------------------------+-----------+--------+------------------------------+

.. _iam_02_0021__table54451161197:

.. table:: **Table 4** protect_policy

   +----------------------+-----------+---------+--------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory | Type    | Description                                                                                      |
   +======================+===========+=========+==================================================================================================+
   | operation_protection | Yes       | Boolean | Indicates whether operation protection has been enabled. The value can be **true** or **false**. |
   +----------------------+-----------+---------+--------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 5** Parameters in the response body

   +--------------------------------------------------------+--------+------------------------------+
   | Parameter                                              | Type   | Description                  |
   +========================================================+========+==============================+
   | :ref:`protect_policy <iam_02_0021__table345114671913>` | object | Operation protection policy. |
   +--------------------------------------------------------+--------+------------------------------+

.. _iam_02_0021__table345114671913:

.. table:: **Table 6** protect_policy

   +----------------------+---------+--------------------------------------------------------------------------------------------------+
   | Parameter            | Type    | Description                                                                                      |
   +======================+=========+==================================================================================================+
   | operation_protection | Boolean | Indicates whether operation protection has been enabled. The value can be **true** or **false**. |
   +----------------------+---------+--------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/protect-policy

   {
     "protect_policy" : {
       "operation_protection" : true
     }
   }

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

**Status code: 400**

The request body is abnormal.

-  Example 1

.. code-block::

   {
      "error_msg" : "'%(key)s' is a required property.",
      "error_code" : "IAM.0072"
    }

-  Example 2

.. code-block::

   {
      "error_msg" : "Invalid input for field '%(key)s'. The value is '%(value)s'.",
      "error_code" : "IAM.0073"
    }

**Status code: 403**

Access denied.

-  Example 1

.. code-block::

   {
      "error_msg" : "Policy doesn't allow %(actions)s to be performed.",
      "error_code" : "IAM.0003"
    }

-  Example 2

.. code-block::

   {
      "error_msg" : "You are not authorized to perform the requested action.",
      "error_code" : "IAM.0002"
    }

**Status code: 500**

The system is abnormal.

.. code-block::

   {
     "error_msg" : "An unexpected error prevented the server from fulfilling your request.",
     "error_code" : "IAM.0006"
   }

Status Codes
------------

=========== =============================
Status Code Description
=========== =============================
200         The request is successful.
400         The request body is abnormal.
401         Authentication failed.
403         Access denied.
500         The system is abnormal.
=========== =============================
