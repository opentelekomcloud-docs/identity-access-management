:original_name: iam_01_019.html

.. _iam_01_019:

Fine-Grained Policies
=====================

A fine-grained policy is a set of permissions that define operations allowed to be performed on specific cloud services. A policy can contain multiple permission sets. After a policy is attached to a user group, users in the user group inherit the permissions of the policy. IAM implements fine-grained access control based on the permissions defined by policies.

IAM supports two types of policies:

-  System-defined policies: define the common permissions preset in the cloud system, which are typically read-only or administrator permission for different cloud services such as ECS. System-defined policies can only be used for authorization and cannot be modified.
-  Custom policies: created and managed by users to supplement system-defined policies.
