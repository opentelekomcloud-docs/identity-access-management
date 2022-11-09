:original_name: en-us_topic_0066738518.html

.. _en-us_topic_0066738518:

Managing Projects
=================

Projects are used to group and isolate OpenStack resources, including compute, storage, and network resources. A project can be a department or a project team. Resources in your account must be managed under projects. As a security administrator, you can access IAM, and create projects in a region to manage resources.

Procedure
---------

#. In the navigation pane, choose **Projects**.

#. On the **Projects** page, click **Create Project**.

#. On the **Create Project** page, select a region from the **Region** drop-down list.

#. Set **Project Name**.

   .. note::

      -  The project name format is *Region Name*\ \_\ *Project Name*. *Region Name* cannot be modified.
      -  The project name can only contain letters, digits, hyphens (-), and underscores (_). The length of *Region Name*\ \_\ *Project Name* cannot exceed 64 characters.

#. (Optional) Enter a description for the project.

#. Click **OK**.

   The project list is displayed, and the newly created project is in the **Normal** state.

Follow-Up Procedure
-------------------

Assigning permissions for a specific project

On the user group details page, click the **Permissions** tab, select **Project View**, click **Modify Permissions** in the row containing the target project, and then modify the permissions for this project. For details, see :ref:`Creating a User Group <en-us_topic_0046611269>`.

Related Operations
------------------

-  Viewing project details

   #. View the projects of the corresponding region in the project list.

   #. Click **View** in the **Operation** column of the row that contains the target project.

      View project details and the users bound to the project.

      .. note::

         After you add a user to a user group that has been granted permissions for a specific project, the user inherits permissions of the group and is associated with the project. The user can switch to this project to access resources in it.

   #. Click **View Permissions** in the **Operation** column of the user permission list.

      View the permissions of the user for the project.

-  Modifying project information

   #. In the project list, expand the region where the target project resides.
   #. Click **Modify** in the **Operation** column of the row that contains the target project. In the displayed **Modify Project** dialog box, modify **Project Name** and **Description**.

   .. note::

      The project name format is *Region Name*\ \_\ *Project Name*. *Region Name* cannot be modified.

-  Deleting a project

   .. important::

      After a project is deleted successfully, the resources in the project are also deleted.

   #. Click **Delete** in the row that contains the project you want to delete.

      .. note::

         Only subprojects created in a region can be deleted. The default project of the region cannot be deleted.

   #. Enter the password and verification code.

   #. Click **Yes**.

      In the project list, the status of the project changes to **Deleting**.

      .. note::

         After resources in the project are deleted, the project is deleted completely.

-  For details about how to switch between projects, see :ref:`Switching Projects or Regions <en-us_topic_0079497018>`.
