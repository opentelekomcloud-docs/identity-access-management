:original_name: iam_01_0023.html

.. _iam_01_0023:

Identity Management
===================

You can manage users in your account and their security credentials. In addition, you can configure identity federation so that users in other systems can access the cloud platform through SSO.

.. _iam_01_0023__section1475194083513:

Domain
------

A domain, also called an "account", is created upon successful registration with the cloud platform. The domain has full access permissions for its cloud services and resources.

For security purposes, create a security administrator and grant them **Security Administrator** permissions to manage users and their permissions in your account.


.. figure:: /_static/images/en-us_image_0274187193.png
   :alt: **Figure 1** Account management model

   **Figure 1** Account management model

User
----

You or other administrators can create users for employees, systems, or applications in IAM. The users can log in to the console or access APIs using their own identity credentials (passwords and access keys).


.. figure:: /_static/images/en-us_image_0274186863.png
   :alt: **Figure 2** Relationship between an account and users

   **Figure 2** Relationship between an account and users

Federated User
--------------

Federated users access the cloud platform through identity federation.

After being authenticated by an identity provider (IdP), users can access resources in a service provider (SP) without needing re-authentication.

-  IdP: a system that authenticates user identities. In identity federation, the identity authentication system of an enterprise, for example, the enterprise management system, is the IdP.
-  Service provider: a system that provides services.

Identity federation allows users in an IdP to access the cloud platform by using the users' security credentials in the IdP. IAM does not need to generate new security credentials for the users. In this way, SSO is implemented.
