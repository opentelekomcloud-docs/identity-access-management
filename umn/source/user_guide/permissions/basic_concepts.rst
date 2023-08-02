:original_name: iam_01_019.html

.. _iam_01_019:

Basic Concepts
==============

Permissions
-----------

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

Permission Type
---------------

You can grant permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. There are only a limited number of roles for granting permissions to users. When using roles to grant permissions, you also need to assign dependency roles. Roles are not ideal for fine-grained authorization and least privilege access.

-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization and secure access control. For example, you can grant ECS users only the permissions required for managing a certain type of ECS resources.

   IAM supports both :ref:`system-defined policies <iam_01_019__section12813010175110>` and :ref:`custom policies <iam_01_019__en-us_topic_0171210163_section1798011555117>`.

.. _iam_01_019__section12813010175110:

System-Defined Policy
---------------------

A system-defined policy defines the common actions of a cloud service. System-defined policies can be used to assign permissions to user groups, and they cannot be modified. For details about the system-defined policies of all cloud services, see "Permissions".

If there are no system-defined policies for a specific service, it indicates that IAM does not support this service.

.. _iam_01_019__en-us_topic_0171210163_section1798011555117:

Custom Policy
-------------

You can create custom policies using the actions supported by cloud services to supplement system-defined policies for more refined access control. You can create custom policies in the visual editor or in JSON view.
