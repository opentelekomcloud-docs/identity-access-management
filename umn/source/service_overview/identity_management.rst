:original_name: iam_01_0023.html

.. _iam_01_0023:

Identity Management
===================

You can manage users in your account and their security credentials. In addition, you can configure federated identity authentication so that users in other systems can access the cloud system through SSO.

Domain
------

A domain, also called an "account", is created upon successful registration with the cloud system. The domain has full access permissions for its cloud services and resources.

For security purposes, create a security administrator and grant them **Security Administrator** permissions to manage users and their permissions in your account.


.. figure:: /_static/images/en-us_image_0274187193.png
   :alt: **Figure 1** Account management module

   **Figure 1** Account management module

User
----

You or other administrators can create users for employees, systems, or applications in IAM. The users can log in to the console or access APIs using their own identity credentials (passwords and access keys).


.. figure:: /_static/images/en-us_image_0274186863.png
   :alt: **Figure 2** Relationship between the account and users

   **Figure 2** Relationship between the account and users

Federated User
--------------

Federated users access the cloud system through federated identity authentication.

After being authenticated by an identity provider (IdP), users can access resources in a service provider (SP) without needing re-authentication.

-  Identity provider: a system that authenticates user identities. In federated identity authentication, the identity authentication system of an enterprise, for example, the enterprise management system, is the identity provider.
-  Service provider: a system that provides services.

Federated identity authentication allows users in an identity provider to access the cloud system by using the users' security credentials in the identity provider. IAM does not need to generate new security credentials for the users. In this way, SSO is implemented.
