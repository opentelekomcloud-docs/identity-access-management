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

#. Go to the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page.

#. Click the **Critical Operations** tab, and click **Bind** in the **Virtual MFA Device** row.


   .. figure:: /_static/images/en-us_image_0000002525746603.png
      :alt: **Figure 1** Binding a virtual MFA device

      **Figure 1** Binding a virtual MFA device

#. Add a virtual MFA device to your MFA application.


   .. figure:: /_static/images/en-us_image_0000002525618428.png
      :alt: **Figure 2** Adding a virtual MFA device

      **Figure 2** Adding a virtual MFA device

#. Bind a virtual MFA device to your account by scanning the QR code or entering the secret key.

   -  Scanning the QR code

      Open the MFA application on your mobile phone, select **Scan QR code**. Click **Show QR code** in step 1 and scan the QR code. Then, the MFA application automatically adds the virtual MFA device.

   -  Entering the secret key

      Open the MFA application on your mobile phone, and enter the secret key.

      .. note::

         TOTP-based virtual MFA devices can only be manually added. You are advised to enable automatic time setting on your mobile device.

#. View the dynamic verification codes on the home page of the MFA application. The code is automatically updated every 30 seconds.

#. On the **Bind Virtual MFA Device** page, enter two consecutive verification codes and click **OK**.
