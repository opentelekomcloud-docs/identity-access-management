:original_name: en-us_topic_0046611276.html

.. _en-us_topic_0046611276:

IAM Features
============

IAM provides the following basic functions:

-  Refined permissions management

   You can control user access to different projects and grant different permissions to users for the same project. For example, you can grant some users permissions to manage Object Storage Service (OBS), and grant other users only the permissions to read data from OBS.


   .. figure:: /_static/images/en-us_image_0274187240.png
      :alt: **Figure 1** Permissions management model

      **Figure 1** Permissions management model

-  Simplified authorization

   You can authorize users in just two steps:

   #. Plan user groups according to users' responsibilities and grant permissions to each user group.
   #. Add a user to the user group that matches the user's responsibilities.

-  Federated identity authentication

   Federated identity authentication enables users in your identity authentication system to access your resources through single sign-on (SSO).

-  Delegation of resource access to another account or a specific cloud service

   You can delegate your operation permissions to a cloud service or another account so that the cloud service or account can access your resources.

-  User authentication and authorization for other cloud services

   Users can be authenticated by IAM to access other services, for example, Relational Database Service (RDS), Cloud Trace Service (CTS), and OBS, based on assigned permissions.

-  Security policy management

   You can set multi-factor authentication (MFA), login authentication and password policies, and an access control list (ACL) to keep user information and system data secure.
