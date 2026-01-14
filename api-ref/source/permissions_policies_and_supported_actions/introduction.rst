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

.. note::

   -  The check mark (Y) and cross symbol (x) indicate that an action takes effect or does not take effect for the corresponding type of projects. A hyphen (-) indicates that an action is irrelevant to the corresponding type of projects.
   -  IAM is a global service which does not involve project-based authorization.
   -  Some permissions only support actions and do not support APIssuch as permissions for :ref:`virtual MFA device management <iam_02_0046__section901342135518>`.
