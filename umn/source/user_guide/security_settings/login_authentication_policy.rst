:original_name: iam_01_0704.html

.. _iam_01_0704:

Login Authentication Policy
===========================

The **Login Authentication Policy** tab of the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page provides the :ref:`Session timeout <iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section10968105732412>`, :ref:`Account Lockout <iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section13189358>`, :ref:`Account Disabling <iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section1694311288250>`, :ref:`Recent Login Information <iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section446533912253>`, and :ref:`Custom Information <iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section733474592515>` settings. These settings take effect for both your account and the IAM users created using the account.

Only the administrator and entrusted identities can configure the login authentication policy. IAM users can only view the configurations. If an IAM user needs to modify the configurations, the user can request the administrator to perform the modification or grant the required permissions.

.. _iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section10968105732412:

Session timeout
---------------

Set the session timeout that will apply if you or users created using your account do not perform any operations within a specific period.


.. figure:: /_static/images/en-us_image_0000002530649051.png
   :alt: **Figure 1** Session timeout

   **Figure 1** Session timeout

Only administrators and authorized identities can change the session timeout. The timeout ranges from 15 minutes to 24 hours, and the default timeout is 15 minutes.

.. _iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section13189358:

Account Lockout
---------------

Set a duration to lock users out if a specific number of unsuccessful login attempts has been reached within a certain period. You cannot unlock your own account or an IAM user's account. Wait until the lock time expires.


.. figure:: /_static/images/en-us_image_0000002492731764.png
   :alt: **Figure 2** Account lockout

   **Figure 2** Account lockout

The administrator and entrusted identities can set the account lockout duration, maximum number of unsuccessful login attempts before the account is locked, and time for resetting the account lockout counter.

-  Lockout duration: The value ranges from 15 to 30 minutes, and the default value is 15 minutes.
-  Maximum number of unsuccessful login attempts: The value ranges from 3 to 10, and the default value is 5.
-  Time for resetting the account lockout counter: The value ranges from 15 to 60 minutes, and the default value is 15 minutes.

.. _iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section1694311288250:

Account Disabling
-----------------

Set a validity period to disable IAM users if they have not accessed the cloud platform using the console or APIs within a certain period.

This option is disabled by default. It can be enabled by the administrator or an entrusted identity. The validity period is from 1 day to 240 days.

**If you enable this option, the setting will take effect only for IAM users created using your account.** If an IAM user is disabled, the user can request the administrator to enable their account again.

.. _iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section446533912253:

Recent Login Information
------------------------

Configure whether you want the system to display the previous login information after you log in. If incorrect login information is displayed on the **Login Verification** page, change your password immediately.

This option is disabled by default and can be enabled by the administrator or an entrusted identity.

.. _iam_01_0704__en-us_topic_0177717040_en-us_topic_0176803438_section733474592515:

Custom Information
------------------

The administrator or an entrusted identity can set custom information (for example, *Welcome*) that will be displayed upon successful login.

This option is disabled by default and can be enabled by the administrator or an entrusted identity.

You and all the IAM users created using your account will see the same information upon successful login.
