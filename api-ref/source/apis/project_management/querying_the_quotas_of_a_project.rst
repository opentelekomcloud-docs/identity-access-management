:original_name: iam_02_0037.html

.. _iam_02_0037:

Querying the Quotas of a Project
================================

Function
--------

This API is used to query the quotas of a specified project.

URI
---

-  URI format

   GET /v3.0/OS-QUOTA/projects/{project_id}

-  URI parameters

========== ========= ====== ==================================
Parameter  Mandatory Type   Description
========== ========= ====== ==================================
project_id Yes       String ID of the project to query quotas.
========== ========= ====== ==================================

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                     |
   +=================+=================+=================+=================================================================================+
   | X-Auth-Token    | Yes             | String          | Provide either of the following tokens:                                         |
   |                 |                 |                 |                                                                                 |
   |                 |                 |                 | -  Token with **Security Administrator** permissions                            |
   |                 |                 |                 | -  IAM user token with the **scope** specified as the project you want to query |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 2** Parameters in the response body

   +---------------------------------------------------+--------+----------------------------------+
   | Parameter                                         | Type   | Description                      |
   +===================================================+========+==================================+
   | :ref:`quotas <iam_02_0037__response_quotaresult>` | object | Quota information of the domain. |
   +---------------------------------------------------+--------+----------------------------------+

.. _iam_02_0037__response_quotaresult:

.. table:: **Table 3** quotas

   +----------------------------------------------------+------------------+-----------------------+
   | Parameter                                          | Type             | Description           |
   +====================================================+==================+=======================+
   | :ref:`resources <iam_02_0037__response_resources>` | Array of objects | Resource information. |
   +----------------------------------------------------+------------------+-----------------------+

.. _iam_02_0037__response_resources:

.. table:: **Table 4** resources

   ========= ======= ==============
   Parameter Type    Description
   ========= ======= ==============
   max       Integer Maximum quota.
   min       Integer Minimum quota.
   quota     Integer Current quota.
   type      String  Quota type.
   used      Integer Used quota.
   ========= ======= ==============

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-QUOTA/projects/{project_id}

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "quotas" : {
                   "resources" : [
                         {
                              "max" : 50,
                              "min" : 0,
                              "quota" : 10,
                              "type" : "project",
                              "used" : 4
                            }
                        ]
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
