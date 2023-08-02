:original_name: iam_06_0004.html

.. _iam_06_0004:

Cloud Service Delegation
========================

Services on the cloud platform interwork with each other, and some cloud services are dependent on other services. To delegate a cloud service to access other services and perform resource O&M, create an agency for the service.

IAM provides two methods to create a cloud service agency:

#. :ref:`Creating a cloud service agency on the IAM console <iam_06_0004__en-us_topic_0175653574_section930952513442>`

   Take an OBS agency as an example. The agency allows OBS to call cloud services, for example, to read monitoring data from AOM.

#. Automatically creating a cloud service agency to use certain resources

   The following takes Scalable File Service (SFS) as an example to describe the procedure for automatically creating a cloud service agency:

   a. Go to the SFS console.
   b. On the **Create File System** page, enable static data encryption.
   c. A dialog box is displayed requesting you to confirm the creation of an SFS agency. After you click **OK**, the system automatically creates an SFS agency with **KMS CMKFullAccess** permissions for the current project. With the agency, SFS can obtain KMS keys for encrypting or decrypting file systems.
   d. You can view the agency in the agency list on the IAM console.

.. _iam_06_0004__en-us_topic_0175653574_section930952513442:

Creating a Cloud Service Agency on the IAM Console
--------------------------------------------------

#. Log in to the .

#. On the IAM console, choose **Agencies** from the navigation pane, and click **Create Agency**.

#. Enter an agency name.


   .. figure:: /_static/images/en-us_image_0000001562896221.png
      :alt: **Figure 1** Cloud service agency name

      **Figure 1** Cloud service agency name

#. Select the **Cloud service** agency type, and then select a service.

#. Select a validity period.

#. (Optional) Enter a description for the agency to facilitate identification.

#. Click **Next**.

#. Select the permissions to be assigned to the agency, click **Next**, and specify the authorization scope.

#. Click **OK**.
