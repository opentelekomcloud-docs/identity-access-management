:original_name: iam_01_0003.html

.. _iam_01_0003:

How Do I Bind a Virtual MFA Device?
===================================

MFA authentication provides an additional layer of protection on top of the username and password. If MFA-based login authentication is enabled, you will need to enter a verification code after your username and password are authenticated. Together, these factors make your account and resources more secure.

MFA devices can be based on hardware or software. The cloud system supports only virtual MFA devices.

A virtual MFA device is an application that generates 6-digit codes in compliance with the TOTP standard. Such applications can run on mobile devices (including smartphones) and are easy to use.

For more information, see :ref:`MFA Authentication and Virtual MFA Device <iam_10_0002>`.

Prerequisites
-------------

You have installed an MFA application (for example, Google Authenticator) on your smartphone.

Procedure
---------

#. On the management console, hover the mouse pointer over the username in the upper right corner and choose **My Credentials** from the drop-down list.

#. On the **My Credentials** page, click **Bind** next to the **Virtual MFA Device** parameter.

#. Go to the **Bind Virtual MFA Device** page.


   .. figure:: /_static/images/en-us_image_0000001420274825.png
      :alt: **Figure 1** Binding a virtual MFA device

      **Figure 1** Binding a virtual MFA device

   .. note::

      The secret key is a one-time credential that you can use to obtain an MFA verification code. To ensure account security, do not share the secret key with anyone.

#. Add your account to an MFA application.

   -  Scanning the QR code

      Open the MFA application on your mobile phone, click the plus sign **+** on the application, and scan the QR code displayed on the **Bind Virtual MFA Device** page. Your account is then automatically added to the application, with the username and secret key displayed.

   -  Manually entering the secret key

      Open the MFA application on your mobile phone, click the plus sign **+** on the application, and manually enter the secret key displayed on the **Bind Virtual MFA Device** page.

      .. note::

         The manual entry function is time-based. Ensure that automatic time setup has been enabled on your mobile phone.

#. View the verification code on the MFA application. The code is automatically updated every 30 seconds.

#. On the **Bind Virtual MFA Device** page, enter two consecutive verification codes and click **OK** to bind the virtual MFA device.
