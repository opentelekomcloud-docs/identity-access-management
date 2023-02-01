:original_name: en-us_topic_0079620341.html

.. _en-us_topic_0079620341:

Introduction
============

If you have an identity authentication system, you do not need to create new users in the service provider system. Instead, you can configure federated identity authentication to allow users in your identity authentication system to access cloud resources through SSO.

The cloud system supports two types of federated identity authentication:

-  Web SSO: Browsers are used as the communication media. This authentication type enables common users to access the system using browsers.

-  API calling: Development tools (such as OpenStack Client) are used as the communication media. This authentication type enables enterprise users and common users to access the system by calling APIs.

   Users in your enterprise can choose SP-initiated or IdP-initiated federated identity authentication for API calling depending on your identity provider system.

Without Federated Identity Authentication
-----------------------------------------

-  SSO not supported

   Users authenticated by the identity provider of an enterprise management system cannot access the cloud system.


   .. figure:: /_static/images/en-us_image_0274187218.png
      :alt: **Figure 1** User authentication model (1)

      **Figure 1** User authentication model (1)

-  Complex user management

   The enterprise administrator has to create users in both the enterprise management system and the cloud system.

-  Complex user operations

   Users have to use different accounts to log in to the enterprise management system and cloud system.


   .. figure:: /_static/images/en-us_image_0274187275.png
      :alt: **Figure 2** User login model (1)

      **Figure 2** User login model (1)

With Federated Identity Authentication
--------------------------------------

-  SSO supported

   Users authenticated by the identity provider can access the cloud system through SSO.


   .. figure:: /_static/images/en-us_image_0274186850.png
      :alt: **Figure 3** User authentication model (2)

      **Figure 3** User authentication model (2)

-  Simplified user management

   The enterprise administrator does not need to create users in the cloud system.

-  Easy user operations

   Users can access the cloud system through the enterprise management system.


   .. figure:: /_static/images/en-us_image_0274187239.png
      :alt: **Figure 4** User login model (2)

      **Figure 4** User login model (2)
