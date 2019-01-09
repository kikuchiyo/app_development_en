# User Guide
This guide introduces how system administrators and organization administrators define application permissions, assign application resources to users, and manage user accounts on EnOS APP Framework.

##  For system administrators
The system administrator is usually EnOS platform administrator or the super administrator of an organization. System administrator is responsible for the following operations:

- Create organizations
- Register public applications
- Define application permissions
- Assign applications to organization
- Create organization administrator accounts

### Creating an organization

In APP Framework, defining the organization information facilitates management of application users and application permissions. System administrator can take the following steps to create an organization.

1. Log in the APP Framework with the system administrator account and click the **Settings** icon to open the page for system settings.

2. Click **Organization Management** in the left control panel and click the **+ New Organization** button.

3. On the **New Organization** pop-up window, enter the name, address, and description of the organization.

4. Click **Save** to complete creating the organization.

Information of the created organizations will be listed in the table on the organization management page. In this table, system administrator can change organization status, update organization information, and manage the list of applications that are assigned to the organization. See the following screen capture.

.. image:: image/company_en.png
   :width: 600px

### Registering a public application

Public applications on EnOS platform can be assigned to organizations if needed. System administrator can take the following steps to register a public application on the APP Framework.

1. Click **Application Management** in the left control panel and click the **+ New Application** button.

2. On the **New Application** pop-up window, enter the name, URL, and description of the application, and select the background color, icon, and status for the application.

3. Click **Save** to complete registering the public application.

Information of the created applications will be listed in the table on the application management page. In this table, system administrator can change application status, update application information, and define application permissions. See the following screen capture.

.. image:: image/public_app_en.png
   :width: 600px

### Defining application permissions

Application permissions are access control points to application resources that are pre-defined by application developers using the EnOS Web SDK. Application permissions can be classified into several types like menu, UI view, and data, which can be granted to different users based on business requirements. System administrator can take the following steps to define application permissions on the APP Framework.

1. Click **Application Management** in the left control panel.

2. In the table of applications, click the **Permission** icon for the target application to open the permission management page.

3. Click the **+ New Permission** button.

4. On the **New Permission** pop-up window, enter the name, element ID, and description of the permission, and select a type and status for the permission. The following permission types are supported:

   - Menu: Menu type application resources, like drop-down menus and navigation panels
   - View: UI control type application resources, like buttons and videos
   - Data: Data type application resources, like reports and table fields

5. Click **Save** to complete defining the application permission.

6. Repeat the above steps to define more permissions.

Defined application permissions will be listed in the table on the permission management page of the application. In this table, system administrator can edit or delete defined permissions. See the following screen capture.

.. image:: image/app_permission_en.png
   :width: 600px

### Assigning applications to an organization

Public applications on EnOS platform can be shared with users by assigning them to organizations. System administrator can take the following steps to assign public applications to an organization.

1. Click **Organization Management** in the left control panel.

2. In the table of organizations, click the **Permission** icon for the target organization to open the list of public applications.

3. Select the checkbox of applications to be assigned to the organization.

4. Click **Save**. See the following screen capture.

   .. image:: image/assign_app_en.png
      :width: 600px

The assigned public applications will be listed on the **Application Management** page of the target organization.

### Creating an organization administrator account

Application resources and users of an organization must be managed by its own administrators, known as organization administrators in the APP Framework. System administrator can take the following steps to create an organization administrator account.

1. Click **OU Administrator** in the left control panel and click the **+ New Administrator** button.

2. On the **New Administrator** pop-up window, enter the name, email, and phone number (optional) of the administrator account, and select the organization and status of the administrator account.

3. Click **Save**.

4. In the list of accounts, find the created account and click the **Reset** icon to generate the initial password for it.

Created organization administrator accounts will be listed in the table on the administrator management page. In this table, system administrator can edit or delete accounts, or reset the account password. See the following screen capture.

.. image:: image/create_ouadmin_en.png
   :width: 600px

##  For organization administrators

The organization administrator is responsible for managing the applications and users of a specific organization. Organization administrator logs in the APP Framework using the account that is created by the system administrator and performs the following operations:

- Register private applications
- Define application permissions
- Create user accounts
- Manage user authorization
- Manage application groups

### Registering a private application

Private applications are usually developed for the internal use of an organization but can also be shared with external users as needed. Organization administrator can take the following steps to register a private application.

1. Log in the APP Framework with the organization administrator account and click the **Settings** icon to open the page for system settings.

2. Click **Application Management** in the left control panel. If there are public applications assigned to the organization, they will be listed in the table.

3. Click the **+ New Application** button.

4. On the **New Application** pop-up window, enter the name, URL, and description of the private application, and select the background color, icon, and status for the application.

5. Click **Save** to complete registering the private application.

Information of the created private applications will be listed in the table on the application management page with assigned public applications. In this table, organization administrator can change the status, update information of private applications, and define application permissions. See the following screen capture.

.. image:: image/private_app_en.png
   :width: 600px

### Defining application permissions

Organization administrator can define the permissions of private applications. The steps are the same with those of system administrator defining permissions for public applications.

### Creating a user account

To support application usage of both internal and external users, different types of user accounts are needed. Organization administrator can take the following steps to create a user account.

1. Click **User Management** in the left control panel and click the **+ New User** button.

2. On the **New User** pop-up window, enter the name, email, and phone number (optional) of the user account, and select the type (internal user or external user) and status of the user account.

3. Click **Save**.

4. In the list of user accounts, find the created account and click the **Reset** icon to generate the initial password for it.

Created user accounts will be listed in the table on the user management page. In this table, organization administrator can edit or delete accounts, reset the account password, or manage user authorization. See the following screen capture.

.. image:: image/create_user_en.png
   :width: 600px

### Managing user authorization

After a user account is created, organization administrator can manage the application authorization of the user account by the following steps.

1. Click **User Management** in the left control panel to open the list of created user accounts.

2. Click the **Permission** icon for the target user to open the user permission management page.

3. In turn, select an application group and application name to expand the list of application permissions.

4. Select the permissions to grant for the user.

5. Click **Save**. See the following screen capture.

   .. image:: image/user_permission_en.png
      :width: 600px

To grant platform management authorization to a user account, select **Settings Group** on the above page to expand the list of management permissions. Select one or more of the permissions (user management, application management, or desktop configuration) to grant for the user account.

With the granted application permissions, users can log in the platform, click the application icon, and use the application to access the authorized resources.

### Managing application groups

When the organization has multiple applications, they can be grouped for easier management. Organization administrator can manage application groups by the following steps.

1. Click **Desktop Configuration** in the left control panel and click the **+ New Group** button.

2. In the **New Group** pop-up window, enter the group name and select the applications to be included in the group.

3. Click **OK**. Note that an application can belong to one group only.

When users log in the APP Framework, they can view the grouped applications on the desktop.

## For users

Users are the consumer of applications. When logging in the APP Framework with the accounts created by organization administrator, users can see the authorized applications that they have permissions to access on the desktop. Users can click the application icon to open it and view the authorized resources. See the following screen capture.

.. image:: image/user_view.png
   :width: 600px
