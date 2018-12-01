# Managing applications
EnOS™ provides developers with the ability to create applications, delete applications, purchase applications, and manage application resources of the organization.

## Registering an application

On the **App Management** page of EnOS Console, click **Register App** and fill in the application information.

1. Enter a name and description for the application.
2. Select a domain category for the application.
3. Define whether the application is a web or mobile app.
4. Optionally, upload an icon for the application.

After the application is created, it is listed under the **Apps of Org** tab. Click the application name to view detailed information (like the secretKey) of the application. You can also register resources such as menus, views, and data of the application so that you can assign different permissions to the application for different users.

## Managing application resources

When you develop an application, the related resources in your organization are authorized for the application by default. To manage and allocate application resources to different users, take the following steps.

1. Click the application name under the **Apps of Org** tab to open the application details page.
2. Click the **Resource Registration** tab to view the list of application resources.
3. Under the table of resources, click the **Edit** button to start the editing mode.
4. Click **Add resource** and enter the resource ID and description in the pop-up window. 

The created resources can be assigned to application users under the **Client Management** tab. 

## Managing application users

When clients request to purchase your application through EnOS, you will need to process the requests and manage resource authorization to your clients on the **App Details** page. 

1. Click the **Client Management** tab to view the pending client requests.
2. In the **Approval Management** section, approve or reject the purchase requests as appropriate.
3. If a client request is approved, assign application resources to the client in the **Authorization Management** section. Assigned resources can be managed in the **Authorized resources** table.

## Purchasing an application

Application developers can sell or purchase applications through EnOS™. This facilitates application sharing and reduces repetitive work on developing similar applications.

If you want to purchase an application that is developed on EnOS, click **Purchased Apps** > **Buy an Application** on EnOS Console, and search for the application by application ID. After you reach an agreement with the application developer, your purchase request will be approved, and the EnOS system administrator or application owner will allocate the relevant application resources to you. You can then find the application under the **Purchased Apps** tab.