# Getting Started with EnOS™ APIs

This topic will quickly get you started with invoking the EnOS™ APIs that are opened by the EnOS™ System. The basic flow is as follows:

1. Obtain API documentation.
2. Register an application on EnOS to get the application key and secret.
3. Call the API by presenting the application key and secret, and providing other required request parameters as instructed in the API documentation.

## Step 1: Obtain the EnOS™ API Documentation

1. Click **API Servics > EnOS API** from the left navigation panel to show the list of EnOS APIs.

2. Search the API by name or locate the API from the list directly.

## Step 2: Register an Application

To request the EnOS APIs, you need to register an application in the EnOS cloud and obtain the application key and secret that are assigned by EnOS. The application is the account to use for accessing EnOS APIs. When you invoke an API, you need to present the application key and secret to be authenticated by EnOS.

An application must have the permission to invoke an API, and any application currently registered on EnOS™ has the permission to invoke EnOS™ APIs. The resource authorization, that is which devices or data you can access through the API, is enforced through IAM at the account level.

To register an application, click **Application management** from the left navigation panel. For more information, see [Application management](../app_mgmt/app_mgmt_overview).

After the application is successful registered, EnOS assigns a pair of application key and secret. You can view the application details to access the assigned key-secret pair.

## Step 3: Invoking an API
