# Application management overview

Application management enables developers to quickly register applications, manage their purchased and self-developed applications, register application resources, view authorized APIs, and so on.

## Key concepts

**Application key**

To call the EnOS™ APIs, an application must have an application key. The application key is the identifier of an application that is assigned by EnOS™ after the application is registered on EnOS™. An application can have one or more application keys.

**Application secret**

The application secret is the secret to the application key. When an application attempts to access resources on EnOS™ through the EnOS™ APIs, the application must present both the application key and application secret to be authenticated and authorized.

**Application resources**

Application resources indicate the menus, operations, other graphic interface controls and elements in an application.

EnOS™ allows application developers to manage the access permissions to the application resources. Developers can register application resources as controlled resources. When the application is sold to a client, the application developer can assign appropriate permissions to the controlled resources for the client.

<!--
**Application purchase**

After an application is developed, the developer might put the application on the marketplace so that other organizations can purchase the application. The buyer or the application owner from the buyer's organization can then assign asset permissions to the application.
-->

## Key benefits

The application management function provides the following benefits:

**Ready-to-use**

An application can access the EnOS™ APIs immediately after the application is registered on EnOS™.

**Secure and reliable**

EnOS™ isolates the data of different clients and ensures that different clients can only access their own asset data when using the same application.
