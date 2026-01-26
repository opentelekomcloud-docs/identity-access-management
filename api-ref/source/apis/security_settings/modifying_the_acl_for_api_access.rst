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
   | :ref:`api_acl_policy <iam_02_0029__table165615447201>` | Yes       | Object | ACL for API access. |
   +--------------------------------------------------------+-----------+--------+---------------------+

.. _iam_02_0029__table165615447201:

.. table:: **Table 4** api_acl_policy

   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                       | Mandatory | Type             | Description                                                                                                           |
   +=================================================================+===========+==================+=======================================================================================================================+
   | :ref:`allow_address_netmasks <iam_02_0029__table6660124414208>` | No        | Array of objects | IPv4 CIDR blocks from which API access is allowed. Specify either **allow_address_netmasks** or **allow_ip_ranges**.  |
   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------------------+
   | :ref:`allow_ip_ranges <iam_02_0029__table1663444182011>`        | No        | Array of objects | IP address ranges from which API access is allowed. Specify either **allow_address_netmasks** or **allow_ip_ranges**. |
   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------------------+
   | :ref:`allow_vpc_endpoints <iam_02_0029__table1867934162615>`    | No        | Array of objects | VPC address from which API access is allowed.                                                                         |
   +-----------------------------------------------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------------------+

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

.. _iam_02_0029__table1867934162615:

.. table:: **Table 7** allow_vpc_endpoints

   +-----------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                         |
   +=================+===========+========+=====================================================================+
   | description     | No        | String | Description about the VPC address.                                  |
   +-----------------+-----------+--------+---------------------------------------------------------------------+
   | vpc_endpoint_id | Yes       | String | VPC address, for example, **8di3jdu-38d7-jhfa-7df6-8adyfiadfia6d**. |
   +-----------------+-----------+--------+---------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 8** Parameters in the response body

   +---------------------------------------------------------+--------+---------------------+
   | Parameter                                               | Type   | Description         |
   +=========================================================+========+=====================+
   | :ref:`api_acl_policy <iam_02_0029__table9669844112020>` | Object | ACL for API access. |
   +---------------------------------------------------------+--------+---------------------+

.. _iam_02_0029__table9669844112020:

.. table:: **Table 9** api_acl_policy

   +------------------------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                        | Type             | Description                                                                                                                                 |
   +==================================================================+==================+=============================================================================================================================================+
   | :ref:`allow_address_netmasks <iam_02_0029__table06721944162013>` | Array of objects | IPv4 CIDR blocks from which API access is allowed.                                                                                          |
   +------------------------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`allow_ip_ranges <iam_02_0029__table1567554416203>`         | Array of objects | IP address ranges from which API access is allowed.                                                                                         |
   +------------------------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`allow_vpc_endpoints <iam_02_0029__table195195282813>`      | Array of objects | VPC address from which access is allowed. This parameter is only returned when a VPC address from which API access is allowed is specified. |
   +------------------------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_02_0029__table06721944162013:

.. table:: **Table 10** api_acl_policy.allow_address_netmasks

   =============== ====== =================================================
   Parameter       Type   Description
   =============== ====== =================================================
   address_netmask String IPv4 CIDR block, for example, **192.168.0.1/24**.
   description     String Description about the IPv4 CIDR block.
   =============== ====== =================================================

.. _iam_02_0029__table1567554416203:

.. table:: **Table 11** api_acl_policy.allow_ip_ranges

   +-------------+--------+-------------------------------------------------------------+
   | Parameter   | Type   | Description                                                 |
   +=============+========+=============================================================+
   | description | String | Description about an IP address range.                      |
   +-------------+--------+-------------------------------------------------------------+
   | ip_range    | String | IP address range, for example, **0.0.0.0-255.255.255.255**. |
   +-------------+--------+-------------------------------------------------------------+

.. _iam_02_0029__table195195282813:

.. table:: **Table 12** api_acl_policy.allow_vpc_endpoints

   +-----------------+--------+---------------------------------------------------------------------+
   | Parameter       | Type   | Description                                                         |
   +=================+========+=====================================================================+
   | description     | String | Description about the VPC address.                                  |
   +-----------------+--------+---------------------------------------------------------------------+
   | vpc_endpoint_id | String | VPC address, for example, **8di3jdu-38d7-jhfa-7df6-8adyfiadfia6d**. |
   +-----------------+--------+---------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   PUT https://sample.domain.com/v3.0/OS-SECURITYPOLICY/domains/{domain_id}/api-acl-policy

   {
     "api_acl_policy" : {
       "allow_ip_ranges" : [ {
         "ip_range" : "0.0.0.0-255.255.255.255",
         "description" : "1"
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
         "description" : "1"
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
