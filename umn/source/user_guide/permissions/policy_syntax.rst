:original_name: iam_01_0017.html

.. _iam_01_0017:

Policy Syntax
=============

Policy Content
--------------

A fine-grained policy consists of the policy version (the **Version** field) and statement (the **Statement** field).

|image1|

-  **Version**: Distinguishes between role-based access control (RBAC) and fine-grained policies.

   -  **1.0**: RBAC policies, which are preset in the system and used to grant permissions for each service as a whole. After such a policy is granted to a user, the user has all permissions of the corresponding service.
   -  **1.1**: Fine-grained policies, which enable more refined authorization based on service APIs. Users granted permissions of such a policy can only perform specific operations on the corresponding service. Fine-grained policies include system-defined and custom policies.

      -  System-defined policies: read-only and administrator permissions for different services.
      -  Custom policies: created and managed by users to supplement system-defined policies. For example, you can create a custom policy to allow users only to modify ECS specifications.

-  **Statement**: Detailed information about a policy, containing the **Effect** and **Action** elements.

   -  Effect

      The valid values for **Effect** include **Allow** and **Deny**. In a custom policy that contains both Allow and Deny statements, the Deny statements take precedence.

   -  Action

      The value can be one or more resource operations.

      The value format is *Service name*:*Resource type*:*Action*, for example, **vpc:ports:create**.

   -  Resource

      Resources on which the policy takes effect.

      Format: *Service name*:*Region*:*Account ID*:*Resource type*:*Resource path*. An asterisk (``*``) means all based on its position in the resource path.

   -  Condition

      Conditions determine when a policy takes effect. A condition consists of a condition key and operator. Condition keys (see the documentation of the relevant cloud service) are either :ref:`global <iam_01_0017__table5817133903114>` or service-level and are used in the **Condition** element of a policy statement. Global condition keys (starting with **g:**) are available for operations of all services, while service-level condition keys (starting with a service abbreviation name such as **obs:**) are available only for operations of the corresponding service. An operator is used together with a condition key to form a complete condition statement.

      Format: *Condition operator*:*{Condition key:[Value 1, Value 2]}*

      Example:

      -  **StringEndWithIfExists":{"g:UserName":["specialCharactor"]}**: The statement is valid for users whose names end with **specialCharactor**.

      .. _iam_01_0017__table5817133903114:

      .. table:: **Table 1** Global condition keys

         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | Global Condition Key | Type             | Description                                                                                                                                      |
         +======================+==================+==================================================================================================================================================+
         | g:CurrentTime        | Time             | Time when an authentication request is received. The time is expressed in the format defined by ISO 8601, for example, **2012-11-11T23:59:59Z**. |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:DomainName         | Character string | Domain name                                                                                                                                      |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:MFAPresent         | Boolean          | Indicates whether to obtain a token through MFA authentication.                                                                                  |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:MFAAge             | Number           | Validity period of a token obtained through MFA authentication. This condition must be used together with **g:MFAPresent**.                      |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:ProjectName        | Character string | Project name                                                                                                                                     |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:ServiceName        | Character string | Service name                                                                                                                                     |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:UserId             | Character string | User ID                                                                                                                                          |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | g:UserName           | Character string | Username                                                                                                                                         |
         +----------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  *Service name*: indicates a product name, such as **ecs**, **evs**, or **vpc**. Only lowercase letters are allowed.
      -  *Resource type* and *Action*: The values are case-insensitive, and wildcards (*) are allowed. A wildcard (*) can represent all or part of information about resource types and actions for the specific service.

Example Policies
----------------

-  A policy can define a single permission, such as the permission required to query ECS details.

   .. code-block::

      {
            "Version": "1.1",
            "Statement": [
                  {
                        "Effect": "Allow",
                        "Action": [
                              "ecs:servers:list",
                              "ecs:servers:get",
                              "ecs:serverVolumes:use",
                              "ecs:diskConfigs:use",
                              "ecs:securityGroups:use",
                              "ecs:serverKeypairs:get",
                              "vpc:securityGroups:list",
                              "vpc:securityGroups:get",
                              "vpc:securityGroupRules:get",
                              "vpc:networks:get",
                              "vpc:subnets:get",
                              "vpc:ports:get",
                              "vpc:routers:get"
                        ]
                  }
            ]
      }

-  A policy can define multiple permissions, such as the permissions required to lock ECSs and create Elastic Volume Service (EVS) disks.

   .. code-block::

      {
          "Version": "1.1",
            "Statement": [
                  {
                        "Effect": "Allow",
                        "Action": [
                              "ecs:servers:lock",
                              "evs:volumes:create"
                        ]
                  }
            ]
      }

-  The following example shows how to use wildcards (*) to define full permissions for Image Management Service (IMS) resources.

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Action": [
                                      "ims:*:*",
                                      "ecs:*:list",
                                      "ecs:*:get",
                                      "evs:*:get"
                              ],
                              "Effect": "Allow"
                      }
              ]
      }

Authentication Process
----------------------

IAM authenticates users according to the permissions granted to the users. The following diagram shows the authentication process.


.. figure:: /_static/images/en-us_image_0274187277.png
   :alt: **Figure 1** Authentication process

   **Figure 1** Authentication process

.. note::

   The actions in each policy bear the OR relationship.

#. A user accesses the system and initiates an operation request.
#. The system evaluates all the permissions policies assigned to the user.
#. The system looks for explicit Deny permissions in these policies. If the system finds an explicit Deny that applies, it returns a decision of Deny, and the authentication ends.
#. If no explicit Deny is found, the system looks for Allow permissions that would apply to the request. If the system finds an explicit Allow permission that applies, it returns a decision of Allow, and the authentication ends.
#. If no explicit Allow permission is found, the system returns a decision of Deny, and the authentication ends.

.. |image1| image:: /_static/images/en-us_image_0000001180570109.png
