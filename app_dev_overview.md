# Application Development Overview

The process of application development on EnOS portal may include registering applications, managing applications (purchased and self-developed), assigning application resources to users, and using EnOS SDKs to develop applications offline.

The application management function of EnOS portal provides the following benefits:

**Ready-to-use**

An application can access the EnOS™ APIs immediately after the application is registered on EnOS™.

**Secure and reliable**

EnOS™ isolates the data of different clients and ensures that different clients can only access their own asset data when using the same application.

**Data integration**

EnOS™ System integrates the ingested asset data, applications, and EnOS APIs, so that all asset data can be accessed and modified through APIs after authorized with applications.

**Cross-organization application authorization**

When you need to use an application developed by a third party organization, you can authorize the application to access the asset data of your organization.

## Concepts

**accessKey**

To call the EnOS™ APIs, an application must have an *accessKey* (application key). The *accessKey* is the identifier of an application that is assigned by EnOS™ after the application is registered on EnOS™. An application can have one or more application keys.

**secretKey**

The *secretKey* (application secret) is the secret to the application key. When an application attempts to access resources on EnOS™ through the EnOS™ APIs, the application must present both the application key and application secret to be authenticated and authorized.

**Application resources**

Application resources indicate the menus, operations, data, and graphic interface controls and elements in an application.

EnOS™ allows application developers to manage the access permissions to the application resources. Developers can register application resources as controlled resources. When the application is shared with a client, the application developer can assign appropriate permissions to the controlled resources for the client using the EnOS Application Framework.

## Personas

The following personas are involved in application management:
- **System administrator**: a party who manages organizations, users, and resources on the EnOS platform.
- **Organization administrator**: a party who manages users and resources of an organization.
- **Application developer**: a party who develops an application through calling EnOS APIs.
- **Application provider**: a party who provisions an application on EnOS to be consumed by other parties. An application developer can be an application provider.
- **Application user/consumer**: who consumes the application that is provided by the application provider.
