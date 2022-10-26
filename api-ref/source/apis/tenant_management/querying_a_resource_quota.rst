:original_name: iam_02_0114.html

.. _iam_02_0114:

Querying a Resource Quota
=========================

Function
--------

This API is used to query a resource quota. You can query the quota of users, user groups, identity providers, agencies, and policies.

URI
---

-  URI format

   GET /v3.0/OS-QUOTA/domains/{domain_id}

-  URI parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                             |
   +===========+===========+========+=========================================================================================+
   | domain_id | Yes       | String | ID of the domain whose quota is to be queried.                                          |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------+
   | type      | No        | String | Type of the quota to be queried. The value can be user, group, idp, agency, and policy. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------+

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | User token (no special permission requirements).      |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block:: text

      GET https://sample.domain.com/v3.0/OS-QUOTA/domains/{domain_id}?type=group

Response Parameters
-------------------

.. table:: **Table 1** Parameters in the response body

   +---------------------------------------------------+--------+----------------------------------+
   | Parameter                                         | Type   | Description                      |
   +===================================================+========+==================================+
   | :ref:`quotas <iam_02_0114__response_quotaresult>` | Object | Quota information of the domain. |
   +---------------------------------------------------+--------+----------------------------------+

.. _iam_02_0114__response_quotaresult:

.. table:: **Table 2** quotas

   +---------------------------------------------------+------------------+-----------------------+
   | Parameter                                         | Type             | Description           |
   +===================================================+==================+=======================+
   | :ref:`resources <iam_02_0114__table017984019288>` | Array of objects | Resource information. |
   +---------------------------------------------------+------------------+-----------------------+

.. _iam_02_0114__table017984019288:

.. table:: **Table 3** resources

   ========= ======= ==============
   Parameter Type    Description
   ========= ======= ==============
   max       Integer Maximum quota.
   min       Integer Minimum quota.
   quota     Integer Current quota.
   type      String  Quota type.
   used      Integer Used quota.
   ========= ======= ==============

-  Example response

   .. code-block::

      Group quota:
      {
          "quotas": {
              "resources": [
                  {
                      "max": 200,
                      "min": 10,
                      "quota": 20,
                      "type": "group",
                      "used": 6
                  }
              ]
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
500         Internal server error.
503         Service unavailable.
=========== =========================================
