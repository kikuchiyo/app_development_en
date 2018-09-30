# Getting started with EnOS™ APIs

This article will quickly boot you into invoking the EnOS™ API services that are opened by the EnOS™ System. You need to complete the following steps in turn:

![](media/apiflow.png)

**Three elements for invoking APIs**

Invoking APIs requires three basic conditions:

- **API**: The API you are about to invoke, defining the API parameters.
- **Applicaiton app**: As the identity when you invoke an API, AppKey and AppSecret are used to verify your identity.
- **Token**: As the external interface of platform resources, EnOS™ API requires users to obtain the resources with permission through the account number, and Token can be obtained by invoking the login interface.
  Details will be given below to explain how to have three conditions and provide a Demon of API invocation for your reference.

## Step 1: Obtain EnOS™ API files
EnOS™ System provides unified interface files for easy access by developers. File address: **EnOS™ Console > API Services > EnOS API**

1. View the grouping of interface files

   First enter the **API service** module of EnOS™ console. Under this module, click the **EnOS™ API** menu to view the grouping of all EnOS™ APIs.
2. View the details of interface files

   You can click the grouping you need to view all the APIs under that grouping.

## Step 2: Create an application, access device
EnOS™ API is an interface provided by EnOS™ System to manage user’s resources registered in the platform. This tutorial takes access as an example to illustrate how to obtain device access data on the platform through EnOS™ API.

- **Create an application**

An application (APP) is the identity when you invoke an API service. Each APP has a set of Key and Secret, which you can understand as an account and password. When you invoke the API, you need to enter AppKey as a parameter. AppSecret is used for signature calculation, and the gateway verifies that this key authenticates you. Invoking the API requires this APP to have the permission to invoke the API, and any APP currently created on the EnOS™ System has the permission to invoke the EnOS™ API.
You can create your APP on the **Application management** page of console. Refer to the documentation for details: [Application management](../app_mgmt/app_mgmt_overview). After the creation is successful, the system assigns a pair of AppKey and AppSecret to APP. In the APP management page, click the application name to access details, and you can see the information of AppKey and AppSecret.

- **Create assets**

An asset is a request resource when you invoke an API service. Resources include device, APP, personnel, etc. All the requested resources must be registered on the EnOS™ System in order to obtain relevant data of the resources through corresponding interfaces. Take device resources as an example: You can create a field station, register the device and access the device in the **Asset management** page of console. For specific operation, please refer to the documentation:[Asset Management](https://docs.envisioniot.com/docs/device-connection/en/latest/asset_management/asset_overview.html)

*Note: The console provides the corresponding interface test page, which automatically obtains the interface parameters. If APP is not applied, the tool will provide the default APP for the developer*

## Step 3: Create an account and give permissions
Most EnOS™ APIs adopt data authentication to guarantee the security of data requests, that is, when requesting a resource, it is necessary to verify whether the requested account has the permission of a resource. Therefore, to invoke the EnOS™ API, you must register your account and its resource permissions with the EnOS™ System.
EnOS™ System provides a complete set of account creation, management and authorization system. For specific operation of creating account and permission, please see: [User Management](https://docs.envisioniot.com/docs/enos/en/latest/iam.html)
Please follow the following steps according to the files:

- **Create a user**

Create the account passed in when you need to invoke an interface

- **Create a policy and assign application permission and data permissions**
Abstract the permissions of the account into a policy, and assign the applications and data required for interface invocation to this policy.

- **Assign policy permissions to users**

Assign the policy to the user so that the user has data and application permissions and can pass the permission validation when the interface is invoked.

## Step 4: Invoke an API

EnOS™ API provides the java language to invoke SDK [Download](/devportal/index.html#/main/24/168/57baab5ed3eb4806104b045d/consoleMenu2). This tutorial will show you how to use the EnOS™ API SDK to obtain real-time and historical data for access devices
- **Get Token Using the Login Interface:**
```java
String baseUrl = "http://developer.envisioncn.com/eeop";
String appId = "App Id";
String appSec = "App Secret";
String name = "name";
String password = "password";
EnvisionClient client = new EnvisionDefaultClient( baseUrl , appId, appSec);
UserLoginRequest loginRequest = new UserLoginRequest();
loginRequest.setPassword(password);
loginRequest.setName(name);
UserLoginResponse loginResponse = client.execute(loginRequest);
String m_token = loginResponse.getAccessToken();
```
- **Access to Real Time Data of Assets**
```java
//Device field point list
List pointIDList =  Arrays.asList("point_name1", "point_name2", "point_name3");
//Device mdmid list
List    deviceIDList = Arrays.asList("dev_mdmid1","dev_mdmid1");    
//Field point keys
List fieldList = Arrays.asList("value", "timestamp");
//Master data ID query
MdmDomainPointsGetRequest request = new MdmDomainPointsGetRequest(deviceIDList, pointIDList, fieldList);
MdmDomainPointsGetResponse response = client.execute(request, token);
```
- **Access to Historical Data of Assets**
```java
//Please use version 0.0.8.9-SNAPSHOT and above:
String beginTime = "2017-06-01 00:00:00";
String endTime = "2017-06-04 00:00:00";
Integer interval = 600;
Integer limit = null;
//Master data ID query
DomainDetailsGetRequestV2 request = new DomainDetailsGetRequestV2(
        deviceIDList, pointIDList, beginTime, endTime, interval, limit);
DomainMetricsGetResponse response = client.execute(request, token);
```
