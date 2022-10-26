:original_name: iam_19_0003.html

.. _iam_19_0003:

Introduction
============

By default, new users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

An account has all the permissions required to call all APIs, but users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if a user queries ECSs using an API, the user must have been granted permissions that allow the **ecs:servers:list** action.

Supported Actions
-----------------

IAM provides system-defined policies that can be directly used. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permission: Defined by actions in a custom policy.
-  APIs: REST APIs that can be called in a custom policy.
-  Actions: Added to a custom policy to control permissions for specific operations.
-  IAM or enterprise projects: A custom policy can be applied to IAM projects or enterprise projects or both. Policies that contain actions supporting both IAM and enterprise projects can be assigned to user groups and take effect in both IAM and Enterprise Management. Policies that only contain actions supporting IAM projects can be assigned to user groups and only take effect for IAM. Such policies will not take effect if they are assigned to user groups in Enterprise Management. For details about the differences between IAM and enterprise projects, see "Differences Between IAM Projects and Enterprise Projects".

.. note::

   -  The check mark (Y) and cross symbol (x) indicate that an action takes effect or does not take effect for the corresponding type of projects. A hyphen (-) indicates that an action is irrelevant to the corresponding type of projects.
   -  IAM is a global service which does not involve project-based authorization.
   -  Some permissions support only actions and do not support APIs\ :ref:`, such as permissions for virtual MFA device management <iam_02_0046__section901342135518>`.
