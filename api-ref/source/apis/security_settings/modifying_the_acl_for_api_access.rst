:original_name: iam_02_0029.html

.. _iam_02_0029:

Modifying the ACL for API Access
================================

Function
--------

This API is provided for the administrator to modify the ACL for API access.

URI
---

PUT /v3.0/OS-SECURITYPOLICY/domains/{domain_id}/api-acl-policy

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

   +--------------------------------------------------------+-----------+--------+---------------------+
   | Parameter                                              | Mandatory | Type   | Description         |
   +========================================================+===========+========+=====================+
   | :ref:`api_acl_policy <iam_02_0029__table165615447201>` | Yes       | object | ACL for API access. |
   +--------------------------------------------------------+-----------+--------+---------------------+

.. _iam_02_0029__table165615447201:

.. table:: **Table 4** api_acl_policy

   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------+
   | Parameter                                                       | Mandatory | Type             | Description                                         |
   +=================================================================+===========+==================+=====================================================+
   | :ref:`allow_address_netmasks <iam_02_0029__table6660124414208>` | Yes       | Array of objects | IPv4 CIDR blocks from which API access is allowed.  |
   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------+
   | :ref:`allow_ip_ranges <iam_02_0029__table1663444182011>`        | Yes       | Array of objects | IP address ranges from which API access is allowed. |
   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------+

.. _iam_02_0029__table6660124414208:

.. table:: **Table 5** allow_address_netmasks

   +-----------------+-----------+--------+---------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                       |
   +=================+===========+========+===================================================+
   | address_netmask | Yes       | String | IPv4 CIDR block, for example, **192.168.0.1/24**. |
   +-----------------+-----------+--------+---------------------------------------------------+
   | description     | No        | String | Description about the IPv4 CIDR block.            |
   +-----------------+-----------+--------+---------------------------------------------------+

.. _iam_02_0029__table1663444182011:

.. table:: **Table 6** allow_ip_ranges

   +-------------+-----------+--------+-------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                 |
   +=============+===========+========+=============================================================+
   | description | No        | String | Description about an IP address range.                      |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | ip_range    | Yes       | String | IP address range, for example, **0.0.0.0-255.255.255.255**. |
   +-------------+-----------+--------+-------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 7** Parameters in the response body

   +---------------------------------------------------------+--------+---------------------+
   | Parameter                                               | Type   | Description         |
   +=========================================================+========+=====================+
   | :ref:`api_acl_policy <iam_02_0029__table9669844112020>` | object | ACL for API access. |
   +---------------------------------------------------------+--------+---------------------+

.. _iam_02_0029__table9669844112020:

.. table:: **Table 8** api_acl_policy

   +------------------------------------------------------------------+---------+-----------------------------------------------------+
   | Parameter                                                        | Type    | Description                                         |
   +==================================================================+=========+=====================================================+
   | :ref:`allow_address_netmasks <iam_02_0029__table06721944162013>` | objects | IPv4 CIDR blocks from which API access is allowed.  |
   +------------------------------------------------------------------+---------+-----------------------------------------------------+
   | :ref:`allow_ip_ranges <iam_02_0029__table1663444182011>`         | objects | IP address ranges from which API access is allowed. |
   +------------------------------------------------------------------+---------+-----------------------------------------------------+

.. _iam_02_0029__table06721944162013:

.. table:: **Table 9** allow_address_netmasks

   =============== ====== =================================================
   Parameter       Type   Description
   =============== ====== =================================================
   address_netmask String IPv4 CIDR block, for example, **192.168.0.1/24**.
   description     String Description about the IPv4 CIDR block.
   =============== ====== =================================================

.. table:: **Table 10** allow_ip_ranges

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

   PUT https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/api-acl-policy

   {
     "api_acl_policy" : {
       "allow_ip_ranges" : [ {
         "ip_range" : "0.0.0.0-255.255.255.255",
         "description" : "1"
       }, {
         "ip_range" : "0.0.0.0-255.255.255.253",
         "description" : "12"
       } ],
       "allow_address_netmasks" : [ {
         "address_netmask" : "192.168.0.1/24",
         "description" : "3"
       }, {
         "address_netmask" : "192.168.0.2/23",
         "description" : "4"
       } ]
     }
   }

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "api_acl_policy" : {
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
