:original_name: iam_01_0600.html

.. _iam_01_0600:

Custom Policy Use Cases
=======================

Using a Custom Policy Along with Full-Permission System-Defined Policies
------------------------------------------------------------------------

Use the following method to assign permissions of the **FullAccess** policy to a user but also forbid the user from accessing CTS. Create a custom policy for denying access to the service, and attach the two policies to the group to which the user belongs. Then, the user will be able to perform all operations on all services except CTS.

Example policy denying access to CTS:

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
           {
               "Effect": "Deny",
               "Action": [
                       "cts:*:*"
               ]
           }
       ]
   }

.. note::

   -  **Action**: Operations to be performed. Each action must be defined in the format "*Service name*:*Resource type*:*Operation*".

      For example, **cts:*:\*** refers to permissions for performing all operations on all resource types of CTS.

   -  **Effect**: Determines whether to deny or allow the operation.

Using a Custom Policy Along with a System-Defined Policy
--------------------------------------------------------

-  Use the following method to assign permissions of the **ECS FullAccess** policy to a user but also forbid the user from deleting ECSs. Create a custom policy denying the **ecs:cloudServers:delete** action, and attach this custom policy together with the system-defined **ECS FullAccess** policy to the group to which the user belongs. Then, the user will be able to perform all operations on ECS except deleting ECSs.

   Example policy denying ECS deletion:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Deny",
                  "Action": [
                          "ecs:cloudServers:delete"
                  ]
              }
          ]
      }

-  Use the following method to assign permissions of the **OBS Buckets Viewer** role to all IAM users but also forbid certain users from viewing specific resources, for example, forbidding users whose names start with **TestUser** from viewing buckets whose names start with **TestBucket**. Create a custom policy for denying the operation, and attach both the **OBS Buckets Viewer** role and the custom policy to the groups to which the users belong. Then, the users will be able to view only buckets whose names do not start with **TestBucket**.

   Example policy forbidding users whose names start with **TestUser** from viewing buckets whose names start with **TestBucket**:

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Deny",
                              "Action": [
                                      "obs:bucket:ListAllMybuckets",
                                      "obs:bucket:HeadBucket",
                                      "obs:bucket:ListBucket",
                                      "obs:bucket:GetBucketLocation"
                              ],
                              "Resource": [
                                  "obs:*:*:bucket:TestBucket*"
                              ],
                              "Condition": {
                                  "StringStartWith": {
                                      "g:UserName": [
                                          "TestUser"
                          ]
                      }
                  }
                      }
              ]
      }

.. note::

   Currently, only certain cloud services (such as OBS) support resource-based authorization. For services that do not support this function, you cannot create custom policies containing resource types.

Using Only a Custom Policy
--------------------------

To grant a user permissions for accessing specific services, you can create a custom policy and attach only the custom policy to the group to which the user belongs.

-  The following is an example policy that allows access only to ECS, EVS, VPC, Application Operations Management (AOM), and ELB.

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Allow"
                              "Action": [
                                      "ecs:*:*",
                                      "evs:*:*",
                                      "vpc:*:*",
                                      "aom:*:*",
                                      "elb:*:*"
                              ],
                      }
              ]
      }

-  The following is an example policy that allows only IAM users whose names start with **TestUser** to delete all objects in the **my-object** directory of the bucket **my-bucket**.

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Allow",
                              "Action": [
                                  "obs:object:DeleteObject"
                              ],
                              "Resource": [
                                  "obs:*:*:object:my-bucket/my-object/*"
                              ],
                              "Condition": {
                                  "StringStartWith": {
                                      "g:UserName": [
                                          "TestUser"
                          ]
                      }
              ]
      }

-  The following is an example policy that allows access to all services except ECS, EVS, VPC, AOM, and ELB.

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Allow"
                              "Action": [
                                      "*:*:*"
                              ],
                      },
                      {
                              "Action": [
                                      "ecs:*:*",
                      "evs:*:*",
                      "vpc:*:*",
                      "aom:*:*",
                      "elb:*:*"
                              ],
                              "Effect": "Deny"
                      }
              ]
      }
