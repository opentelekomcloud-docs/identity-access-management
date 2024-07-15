:original_name: iam_02_0028.html

.. _iam_02_0028:

Querying the ACL for Console Access
===================================

Function
--------

This API is used to query the ACL for console access.

URI
---

GET /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/console-acl-policy

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

   +-------------------------------------------------------------+--------+-------------------------+
   | Parameter                                                   | Type   | Description             |
   +=============================================================+========+=========================+
   | :ref:`console_acl_policy <iam_02_0028__table1910743413202>` | object | ACL for console access. |
   +-------------------------------------------------------------+--------+-------------------------+

.. _iam_02_0028__table1910743413202:

.. table:: **Table 4** console_acl_policy

   +-------------------------------------------------------------------+------------------+---------------------------------------------------------+
   | Parameter                                                         | Type             | Description                                             |
   +===================================================================+==================+=========================================================+
   | :ref:`allow_address_netmasks <iam_02_0028__table201101534172012>` | Array of objects | IPv4 CIDR blocks from which console access is allowed.  |
   +-------------------------------------------------------------------+------------------+---------------------------------------------------------+
   | :ref:`allow_ip_ranges <iam_02_0028__table10112234152017>`         | Array of objects | IP address ranges from which console access is allowed. |
   +-------------------------------------------------------------------+------------------+---------------------------------------------------------+

.. _iam_02_0028__table201101534172012:

.. table:: **Table 5** allow_address_netmasks

   =============== ====== =================================================
   Parameter       Type   Description
   =============== ====== =================================================
   address_netmask String IPv4 CIDR block, for example, **192.168.0.1/24**.
   description     String Description about the IPv4 CIDR block.
   =============== ====== =================================================

.. _iam_02_0028__table10112234152017:

.. table:: **Table 6** allow_ip_ranges

   +-------------+--------+-------------------------------------------------------------+
   | Parameter   | Type   | Description                                                 |
   +=============+========+=============================================================+
   | description | String | Description about an IP address range.                      |
   +-------------+--------+-------------------------------------------------------------+
   | ip_range    | String | IP address range, for example, **0.0.0.0-255.255.255.255**. |
   +-------------+--------+-------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/console-acl-policy

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "console_acl_policy" : {
       "allow_ip_ranges" : [ {
         "ip_range" : "0.0.0.0-255.255.255.255",
         "description" : ""
       }, {
         "ip_range" : "0.0.0.0-255.255.255.255",
         "description" : ""
       } ],
       "allow_address_netmasks" : [ {
         "address_netmask" : "192.168.0.1/24",
         "description" : ""
       }, {
         "address_netmask" : "192.168.0.1/24",
         "description" : ""
       } ]
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
