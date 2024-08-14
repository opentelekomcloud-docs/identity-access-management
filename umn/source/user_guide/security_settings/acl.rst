:original_name: iam_07_0003.html

.. _iam_07_0003:

ACL
===

The **ACL** tab of the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page provides the :ref:`IP Address Ranges <iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section1659055844011>`, :ref:`IPv4 CIDR Blocks <iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section5282253478>`, and :ref:`VPC Endpoints <iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section148601027258>` settings for allowing user access only from specified IP address ranges, IPv4 CIDR blocks, or VPC endpoints.

Only the :ref:`administrator <iam_01_0034>` can configure the ACL. If an IAM user needs to configure the ACL, the user can request the administrator to perform the configuration or grant the required permissions.

**Access type:**

-  **Console Access** (recommended): The ACL takes effect only for IAM users who are created using your account and have access to the console.
-  **API Access**: The ACL controls users' API access through API Gateway and takes effect only for IAM users two hours after you complete the configuration.

.. note::

   -  You can configure a maximum of 200 access control items.

.. _iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section1659055844011:

IP Address Ranges
-----------------


.. figure:: /_static/images/en-us_image_0000001209614103.png
   :alt: **Figure 1** IP Address Ranges

   **Figure 1** IP Address Ranges

Specify IP address ranges from 0.0.0.0 to 255.255.255.255 to allow access to the cloud platform. The default value is **0.0.0.0-255.255.255.255**. If this parameter is left blank or the default value is used, your IAM users can access the management console from anywhere.

.. _iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section5282253478:

IPv4 CIDR Blocks
----------------

Specify IPv4 CIDR blocks to allow access to the cloud platform. For example, set **IPv4 CIDR block** to **10.10.10.10/32**.

.. _iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section148601027258:

VPC Endpoints
-------------

Specify VPC endpoints, such as **0ccad098-b8f4-495a-9b10-613e2a5exxxx**, to allow API-based access to the cloud platform. If access control is not configured, you can access APIs from all VPC endpoints by default.

.. note::

   -  User access is allowed if any of **IP Address Ranges**, **IPv4 CIDR Blocks**, and **VPC Endpoints** is met.
   -  To restore **IP Address Ranges** to the default settings (0.0.0.0-255.255.255.255) and clear the settings in **IPv4 CIDR Blocks** and **VPC Endpoints**, click **Restore Defaults**.
