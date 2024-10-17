:original_name: iam_02_0040.html

.. _iam_02_0040:

Querying All Permissions of an Agency
=====================================

Function
--------

This API is provided for the administrator to query all permissions that have been assigned to an agency.

URI
---

GET /v3.0/OS-INHERIT/domains/{domain_id}/agencies/{agency_id}/roles/inherited_to_projects

.. table:: **Table 1** URI parameters

   ========= ========= ====== =============================
   Parameter Mandatory Type   Description
   ========= ========= ====== =============================
   agency_id Yes       String Agency ID.
   domain_id Yes       String ID of the delegating account.
   ========= ========= ====== =============================

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

   +-----------------------------------------------+------------------+----------------------------+
   | Parameter                                     | Type             | Description                |
   +===============================================+==================+============================+
   | :ref:`roles <iam_02_0040__table095611121610>` | Array of objects | Permission information.    |
   +-----------------------------------------------+------------------+----------------------------+
   | :ref:`links <iam_02_0040__table496413127611>` | object           | Resource link information. |
   +-----------------------------------------------+------------------+----------------------------+

.. _iam_02_0040__table095611121610:

.. table:: **Table 4** roles

   +-----------------------------------------------+--------+---------------------------+
   | Parameter                                     | Type   | Description               |
   +===============================================+========+===========================+
   | id                                            | String | Permission ID.            |
   +-----------------------------------------------+--------+---------------------------+
   | :ref:`links <iam_02_0040__table496413127611>` | object | Permission resource link. |
   +-----------------------------------------------+--------+---------------------------+
   | name                                          | String | Permission name.          |
   +-----------------------------------------------+--------+---------------------------+

.. _iam_02_0040__table496413127611:

.. table:: **Table 5** links

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   self      String Resource link.
   ========= ====== ==============

Example Request
---------------

.. code-block:: text

   GET https://sample.domain.com/v3.0/OS-INHERIT/domains/{domain_id}/agencies/{agency_id}/roles/inherited_to_projects

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "roles" : [
         {
             "name" : "system_all_154",
             "links" : {
                          "self" : "https://sample.domain.com/v3/roles/04570dfe267c45a3940e1ae9de868..."
                         },
             "id" : "04570dfe267c45a3940e1ae9de868..."
           },
         {
             "name" : "test1_admin",
             "links" : {
                           "self" : "https://sample.domain.com/v3/roles/1bf20f1adba94747a6e02e1be3810..."
                          },
             "id" : "1bf20f1adba94747a6e02e1be3810..."
           }
         ],
     "links" : {
             "self" : "https://sample.domain.com/v3.0/OS-INHERIT/domains/05b09b4723001dc90f27c0008f8b1.../agencies/08c6652e86801d234f01c00078308.../roles/inherited_to_projects"
                 }
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
