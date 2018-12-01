# APP Framework Overview
APP Framework is a standalone module provided by EnOS System to support application developers on central management of application users and access permissions within the organization. It helps application developers and organization administrators efficiently manage internal and external user accounts, define application resources, and allocate resource access permissions.

## Terminology
**Application**

Software tools that are registered and developed on the EnOS Portal. In APP Framework, applications can be registered as public applications and private applications.

**Company / Organization**
Entities or units to which applications and developers belong. In APP Framework, defining company and organization information facilitates management of application users and permissions.

**Application permission**
Access control to application resources that is enabled by EnOS system. Different application permissions can be classified into several types like menu, UI view, and data, which can be granted to different users based on business requirements.

**System administrator**
EnOS platform administrator or super administrator of an organization. The system administrator is responsible for defining company/organization, registering public applications, defining application permissions, assigning applications for organizations, and creating organization administrator accounts.

**Organization administrator**
Application administrator of an organization. The organization administrator is responsible for managing applications by groups, creating user accounts, and managing user access permissions.

**Application user**
Consumer of applications by using the accounts created by the organization administrator.

## Product features
Features of the APP Framework include:

**Data integration**: EnOS system integrates connected asset data, application data, and APIs, which enables allocating resources to different users through application authorization.

**Security and reliability**: EnOS system isolates the business data of different clients and ensures data security by asset authorization. The assets of a client can only be accessed with the proactive authorization of the client.

**Cross-organization authorization**: To grant external users with resource access, clients can authorize an application with access permissions. External users can use the application to view asset information.