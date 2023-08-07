:original_name: iam_08_0258.html

.. _iam_08_0258:

Step 4: Verify the Federated Login
==================================

Verifying the Federated Login
-----------------------------

Federated users can initiate a login from the IdP or SP.

-  Initiating a login from an IdP, for example, Microsoft Active Directory Federation Services (AD FS) or Shibboleth.
-  Initiating a login from the SP (the cloud platform). You can obtain the login link from the IdP details page on the IAM console.

The IdP-initiated login method depends on the IdP. For details, see the IdP help documentation. This section describes how to initiate a login from the SP.

#. Log in as a federated user.

   On the **Identity Providers** page of the console, click **View** in the row containing the IdP. Click |image1| to copy the login link displayed in the **Basic Information** area, open the link using a browser, and then enter the username and password used in the enterprise management system.


   .. figure:: /_static/images/en-us_image_0000001656582221.png
      :alt: **Figure 1** Login link

      **Figure 1** Login link

#. Check whether the federated user is logging in as an IAM user.

Redirecting to a Specified Region or Service
--------------------------------------------

You can specify the target page which the federated user will be redirected to after login.

-  Configuring the login link on the SP

   Combine the login link obtained from the console with the specified URL using the format **Login link&service=Specified URL**.

-  Configuring the login link on the IdP

   Configure the IAM_SAML_Attributes_redirect_url assertion (the URL to be redirected to) in the SAML assertion of the enterprise IdP.

.. |image1| image:: /_static/images/en-us_image_0000001646293253.png
