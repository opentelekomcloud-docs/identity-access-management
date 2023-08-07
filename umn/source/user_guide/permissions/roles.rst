:original_name: iam_01_0601.html

.. _iam_01_0601:

Roles
=====

Roles are a type of coarse-grained authorization mechanism that defines service-level permissions based on user responsibilities. IAM provides a limited number of roles for permissions management.

Services on the cloud platform interwork with each other. Roles of some services take effect only if they are assigned along with roles of other services. For more information, see :ref:`Assigning Dependency Roles <iam_01_0657>`.

Role Content
------------

When using roles to assign permissions, you can select a role and click |image1| to view the details of the role. This section uses the **DNS Administrator** role as an example to describe the role content.

.. code-block::

   {
       "Version": "1.0",
       "Statement": [
           {
               "Action": [
                   "DNS:Zone:*",
                   "DNS:RecordSet:*",
                   "DNS:PTRRecord:*"
               ],
               "Effect": "Allow"
           }
       ],
       "Depends": [
           {
               "catalog": "BASE",
               "display_name": "Tenant Guest"
           },
           {
               "catalog": "VPC",
               "display_name": "VPC Administrator"
           }
       ]
   }

Parameter Description
---------------------

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       |                 | Description                                                               | Value                                                                                                                                                                              |
   +=================+=================+===========================================================================+====================================================================================================================================================================================+
   | Version         |                 | Role version.                                                             | **1.0**: indicates role-based access control.                                                                                                                                      |
   +-----------------+-----------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Statement       | Action          | Operations to be performed on the service.                                | Format: "*Service name*:*Resource type*:*Operation*".                                                                                                                              |
   |                 |                 |                                                                           |                                                                                                                                                                                    |
   |                 |                 |                                                                           | **DNS:Zone:\***: Permissions for performing all operations on Domain Name Service (DNS) zones.                                                                                     |
   +-----------------+-----------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                 | Effect          | Determines whether to allow or deny the operations defined in the action. | -  Allow                                                                                                                                                                           |
   |                 |                 |                                                                           | -  Deny                                                                                                                                                                            |
   |                 |                 |                                                                           |                                                                                                                                                                                    |
   |                 |                 |                                                                           | .. note::                                                                                                                                                                          |
   |                 |                 |                                                                           |                                                                                                                                                                                    |
   |                 |                 |                                                                           |    If a role grants both Allow and Deny effects for the same action, the Deny takes precedence.                                                                                    |
   +-----------------+-----------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Depends         | catalog         | Name of the service to which a dependency role belongs.                   | Service name. Example: **BASE** and **VPC**.                                                                                                                                       |
   +-----------------+-----------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                 | display_name    | Name of the dependency role.                                              | Role name.                                                                                                                                                                         |
   |                 |                 |                                                                           |                                                                                                                                                                                    |
   |                 |                 |                                                                           | .. note::                                                                                                                                                                          |
   |                 |                 |                                                                           |                                                                                                                                                                                    |
   |                 |                 |                                                                           |    When you assign the **DNS Administrator** role to a user group, you also need to assign the **Tenant Guest** and **VPC Administrator** roles to the group for the same project. |
   |                 |                 |                                                                           |                                                                                                                                                                                    |
   |                 |                 |                                                                           |    For more information about dependencies, see "Permissions".                                                                                                                     |
   +-----------------+-----------------+---------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001162246460.png
