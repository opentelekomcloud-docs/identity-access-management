:original_name: iam_01_0007.html

.. _iam_01_0007:

Concepts
========

Common concepts used when you call IAM APIs are described as follows:

-  Account

   An account is created upon successful registration with the cloud platform. The account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions.

-  Domain

   A domain, also called an "account", is created upon successful registration. The domain has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions.

-  User

   A user is created using a domain to use cloud services. Each user has their own identity credentials (password and access keys).

   An IAM user can view the domain ID and user ID on the **My Credentials** page of the console. The account name, username, and password will be required for API authentication.

-  Region

   A region contains a physical data center, which is completely isolated to improve fault tolerance and stability. The region that is selected during resource creation cannot be changed after the resource is created. Regions are classified into universal regions and dedicated regions. A universal region provides universal cloud services for common tenants. A dedicated region provides specific services for specific tenants.

-  AZ

   An AZ is a physical location where resources use independent power supplies and networks. A region contains one or more AZs that are physically isolated but interconnected through internal networks. Because AZs are isolated from each other, any fault that occurs in an AZ will not affect other AZs.

-  Project

   Projects group and isolate resources (including compute, storage, and network resources) across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. For more refined access control, create subprojects under a project and create resources in the subprojects. Users can then be assigned permissions to access only specific resources in the subprojects.


   .. figure:: /_static/images/en-us_image_0283051422.gif
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model
