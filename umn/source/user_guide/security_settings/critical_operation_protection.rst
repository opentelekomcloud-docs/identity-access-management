:original_name: iam_07_0002.html

.. _iam_07_0002:

Critical Operation Protection
=============================

Only an :ref:`administrator <iam_01_0023__section1475194083513>` can configure critical operation protection, and IAM users can only view the configurations. If an IAM user needs to modify the configurations, the user can request the administrator to perform the modification or grant the required permissions.

.. note::

   Federated users do not need to verify their identity when performing critical operations.

Virtual MFA Device
------------------

An MFA device generates 6-digit verification codes in compliance with the Time-based One-time Password Algorithm (TOTP). MFA devices can be hardware- or software-based. Currently, only software-based virtual MFA devices are supported, and they are application programs running on smart devices such as mobile phones.

This section describes how to bind a virtual MFA device. If you have installed another MFA application, add a user by following the on-screen prompts. For details about how to bind or remove a virtual MFA device, see :ref:`MFA Authentication and Virtual MFA Device <iam_10_0002>`.

.. note::

   Before binding a virtual MFA device, ensure that you have installed an MFA application on your mobile device.

#. Go to the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page.

#. Click the **Critical Operations** tab, and click **Bind** in the **Virtual MFA Device** row.

#. Set up the MFA application by scanning the QR code or manually entering the secret key.

   You can bind a virtual MFA device to your account by scanning the QR code or entering the secret key.

   -  Scanning the QR code

      Open the MFA application on your mobile phone, and use the application to scan the QR code displayed on the **Bind Virtual MFA Device** page. Your account or IAM user is then added to the application.

   -  Manually entering the secret key

      Open the MFA application on your mobile phone, and enter the secret key.

      .. note::

         Your account is manually added using the time-based algorithm. Ensure that automatic time setting has been enabled on your mobile phone.

#. View the verification codes on the MFA application. The code is automatically updated every 30 seconds.

#. On the **Bind Virtual MFA Device** page, enter two consecutive verification codes and click **OK**.

Login Protection
----------------

After login protection is enabled, you and IAM users created using your account will need to enter a verification code in addition to the username and password during login. Enable this function for account security.

For the account, only the account administrator can enable login protection for it. For IAM users, both the account administrator and other administrators can enable this feature for the users.

-  **(Administrator) Enabling login protection for an IAM user**

   To enable login protection for an IAM user, go to the **Users** page and choose **More** > **Security Settings** in the row that contains the IAM user. In the **Login Protection** area on the displayed **Security Settings** tab, click |image1| next to **Verification Method**, and select a verification method from SMS, email, or virtual MFA device.

-  **Enabling login protection for your account**

   To enable login protection, click the **Critical Operations** tab on the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page, click **Enable** next to **Login Protection**, select a verification method, enter the verification codes, and click **OK**.

Operation Protection
--------------------

-  **Enabling operation protection**

   After operation protection is enabled, you and IAM users created using your account need to enter a verification code when performing a critical operation, such as deleting an ECS. This function is enabled by default. To ensure resource security, keep it enabled.

   The verification is valid for 15 minutes and you do not need to be verified again when performing critical operations within the validity period.

#. Go to the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page.

#. On the **Critical Operations** tab, locate the **Operation Protection** row and click **Enable**.

#. Select **Enable** and then select **Self-verification** or **Verification by another person**.

   If you select **Verification by another person**, an identity verification is required to ensure that this verification method is available.

   -  **Self-verification**: You or IAM users themselves perform verification when performing a critical operation.
   -  **Verification by another person**: The specified person completes verification when you or IAM users perform a critical operation. Only SMS and email verification are supported.

#. Click **OK**.

-  **Disabling operation protection**

If operation protection is disabled, you and IAM users created using your account do not need to enter a verification code when performing a critical operation.

#. Go to the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page.
#. On the **Critical Operations** tab, locate the **Operation Protection** row and click **Change**.
#. Select **Disable** and click **OK**.
#. Enter a verification code.

   -  **Self-verification**: The administrator who wants to disable operation protection completes the verification. SMS, email, and virtual MFA verification are supported.
   -  **Verification by another person**: The specified person completes the verification. Only SMS and email verification are supported.

#. Click **OK**.

.. note::

   -  Each cloud service defines its own critical operations.
   -  When IAM users created using your account perform a critical operation, they will be prompted to choose a verification method from email, SMS, and virtual MFA device.

      -  If a user is only associated with a mobile number, only SMS verification is available.
      -  If a user is only associated with an email address, only email verification is available.
      -  If a user is not associated with an email address, mobile number, or virtual MFA device, the user will need to associate at least one of them before the user can perform any critical operations.

   -  You may not be able to receive email or SMS verification codes due to communication errors. In this case, you are advised to use a virtual MFA device for verification.
   -  If operation protection is enabled, IAM users need to enter verification codes when performing a critical operation. The verification codes are sent to the mobile number or email address bound to the IAM users.

Access Key Management
---------------------

-  **Enabling access key management**

   After access key management is enabled, only the administrator can create, enable, disable, or delete access keys of IAM users. This function is disabled by default. To ensure resource security, enable this function.

   To enable access key management, click the **Critical Operations** tab on the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page, and click |image2| in the **Access Key Management** row.

-  **Disabling access key management**

   After access key management is disabled, all IAM users can create, enable, disable, or delete their own access keys.

   To enable access key management, click the **Critical Operations** tab on the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page, and click |image3| in the **Access Key Management** row.

Information Self-Management
---------------------------

-  **Enabling information self-management**

   By default, information self-management is enabled, indicating that all IAM users can manage their own :ref:`basic information <iam_01_0703>` (login password, mobile number, and email address). Determine whether to allow IAM users to manage their own information and what information they can modify.

   To enable information self-management, click the **Critical Operations** tab on the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page, and click **Enable** next to **Information Self-Management**. Select **Enable**, select the information types that IAM users can modify, and click **OK**.

-  **Disabling information self-management**

   After you disable information self-management, only administrators can manage their own :ref:`basic information <iam_01_0703>`. If IAM users need to modify their login password, mobile number, or email address, they can contact the administrator. For details, see :ref:`Viewing and Modifying User Group Information <en-us_topic_0085605493>`.

   To disable information self-management, click the **Critical Operations** tab on the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page, and click **Change** in the **Information Self-Management** row. In the displayed pane, select **Disable** and click **OK**.

Critical Operations
-------------------

The following tables list the critical operations defined by each cloud service.

.. _iam_07_0002__en-us_topic_0177717039_table1143213281227:

.. table:: **Table 1** Critical operations defined by cloud services

   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Service Type            | Service                              | Critical Operation                                            |
   +=========================+======================================+===============================================================+
   | Compute                 | Elastic Cloud Server (ECS)           | -  Stopping, restarting, or deleting an ECS                   |
   |                         |                                      | -  Resetting the password for logging in to an ECS            |
   |                         |                                      | -  Detaching a disk                                           |
   |                         |                                      | -  Unbinding an EIP                                           |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Bare Metal Server (BMS)              | -  Stopping or restarting a BMS                               |
   |                         |                                      | -  Resetting the BMS password                                 |
   |                         |                                      | -  Detaching a disk                                           |
   |                         |                                      | -  Unbinding an EIP                                           |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Auto Scaling (AS)                    | Deleting an AS group                                          |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Storage                 | Object Storage Service (OBS)         | -  Deleting a bucket                                          |
   |                         |                                      | -  Creating, editing, or deleting a bucket policy             |
   |                         |                                      | -  Configuring an object policy                               |
   |                         |                                      | -  Creating, editing, or deleting a bucket ACL                |
   |                         |                                      | -  Configuring access logging                                 |
   |                         |                                      | -  Configuring URL validation                                 |
   |                         |                                      | -  Creating or editing a bucket inventory                     |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Elastic Volume Service (EVS)         | Deleting an EVS disk                                          |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Cloud Backup and Recovery (CBR)      | -  Deleting a vault                                           |
   |                         |                                      | -  Deleting a backup                                          |
   |                         |                                      | -  Restoring a backup                                         |
   |                         |                                      | -  Deleting a policy                                          |
   |                         |                                      | -  Dissociating a resource                                    |
   |                         |                                      | -  Accepting a backup                                         |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Network                 | Domain Name Service (DNS)            | -  Modifying, disabling, or deleting a record set             |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Virtual Private Cloud (VPC)          | -  Releasing or unbinding an EIP                              |
   |                         |                                      | -  Deleting a VPC peering connection                          |
   |                         |                                      | -  Security group operations                                  |
   |                         |                                      |                                                               |
   |                         |                                      |    -  Deleting an inbound or outbound rule                    |
   |                         |                                      |    -  Modifying an inbound or outbound rule                   |
   |                         |                                      |    -  Deleting inbound or outbound rules                      |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Elastic Load Balance (ELB)           | -  Classic load balancers                                     |
   |                         |                                      |                                                               |
   |                         |                                      |    -  Deleting a load balancer                                |
   |                         |                                      |    -  Deleting a listener                                     |
   |                         |                                      |    -  Deleting a certificate                                  |
   |                         |                                      |    -  Disabling a load balancer                               |
   |                         |                                      |                                                               |
   |                         |                                      | -  Shared load balancers                                      |
   |                         |                                      |                                                               |
   |                         |                                      |    -  Deleting a load balancer                                |
   |                         |                                      |    -  Deleting a listener                                     |
   |                         |                                      |    -  Deleting a certificate                                  |
   |                         |                                      |    -  Removing a backend server                               |
   |                         |                                      |    -  Unbinding an EIP                                        |
   |                         |                                      |    -  Unbind a public or private IPv4 address                 |
   |                         |                                      |    -  Unbinding an IPv6 address                               |
   |                         |                                      |    -  Removing from IPv6 shared bandwidth                     |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   |                         | Elastic IP (EIP)                     | -  Deleting a shared bandwidth                                |
   |                         |                                      | -  Releasing or unbinding an EIP                              |
   |                         |                                      | -  Releasing or unbinding EIPs                                |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Management & Deployment | Identity and Access Management (IAM) | -  Disabling operation protection                             |
   |                         |                                      | -  Disabling login protection                                 |
   |                         |                                      | -  Changing the mobile number                                 |
   |                         |                                      | -  Changing the email address                                 |
   |                         |                                      | -  Changing the login password                                |
   |                         |                                      | -  Changing the login authentication method                   |
   |                         |                                      | -  Deleting an IAM user                                       |
   |                         |                                      | -  Disabling an IAM user                                      |
   |                         |                                      | -  Deleting an agency                                         |
   |                         |                                      | -  Deleting a user group                                      |
   |                         |                                      | -  Deleting a policy                                          |
   |                         |                                      | -  Deleting permissions                                       |
   |                         |                                      | -  Creating an access key                                     |
   |                         |                                      | -  Deleting an access key                                     |
   |                         |                                      | -  Disabling an access key                                    |
   |                         |                                      | -  Deleting the project                                       |
   |                         |                                      | -  Modifying the status of access key management              |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Application             | Distributed Cache Service (DCS)      | -  Resetting the password of a DCS instance                   |
   |                         |                                      | -  Deleting a DCS instance                                    |
   |                         |                                      | -  Clearing DCS instance data                                 |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Database                | RDS for MySQL                        | -  Resetting the administrator password                       |
   |                         |                                      | -  Deleting a DB instance                                     |
   |                         |                                      | -  Deleting a database backup                                 |
   |                         |                                      | -  Switching between primary and standby DB instances         |
   |                         |                                      | -  Changing the database port                                 |
   |                         |                                      | -  Deleting a database account                                |
   |                         |                                      | -  Deleting a database                                        |
   |                         |                                      | -  Unbinding an EIP                                           |
   |                         |                                      | -  Downloading a full backup                                  |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+
   | Databases               | Document Database Service (DDS)      | -  Resetting the password                                     |
   |                         |                                      | -  Restarting or deleting a DB instance                       |
   |                         |                                      | -  Restarting a node                                          |
   |                         |                                      | -  Switching the primary and secondary nodes of a replica set |
   |                         |                                      | -  Deleting a security group rule                             |
   |                         |                                      | -  Enabling IP addresses of shard and config nodes            |
   |                         |                                      | -  Restoring the current DB instance from a backup            |
   |                         |                                      | -  Restoring an existing DB instance from a backup            |
   +-------------------------+--------------------------------------+---------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001207368543.png
.. |image2| image:: /_static/images/en-us_image_0000001162406406.png
.. |image3| image:: /_static/images/en-us_image_0000001207367895.png
