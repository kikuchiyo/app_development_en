# Getting started with EnOS™ APIs

This topic will quickly get you started with invoking the EnOS™ APIs that are opened by the EnOS™ System. The basic flow is as follows:

1. Obtain API documentation.
2. Register an application on EnOS to get the application key and secret.
3. Call the API by presenting the application key and secret, and providing other required request parameters as instructed in the API documentation.


**Three elements for invoking APIs**

Invoking APIs requires three types of parameters:

- API: The name of the API that you are about to invoke and the request paramters as required by the API.
- Application identity: As the identity when you invoke an API, `AppKey` and `AppSecret` are used to verify your identity.
- Token: to access the resources in the EnOS Cloud, a API requester must present the username to be authenticated and access the authorized resources. You can obtain the token by invoking the `login` API.

## Before you start

Ensure you have resources on EnOS that you are authorized to access. The resources can be devices, data, events, user accounts, and so on. So before you start using EnOS APIs, you typically have finished connecting your devices and data into EnOS, and have a user account that has proper access policies assigned through EnOS IAM service.

## Step 1: Obtain the EnOS™ API documentation

1. Click **API Servics > EnOS API** from the left navigation panel to show the list of EnOS APIs.

2. Search the API by name or locate the API from the list directly.

## Step 2: Register an application

To request the EnOS APIs, you need to register an application in the EnOS cloud and obtain the application key and secret that are assigned by EnOS. The application is the account to use for accessing EnOS APIs. When you invoke an API, you need to present the application key and secret to be authenticated by EnOS.

An application must have the permission to invoke an API, and any application currently registered on EnOS™ has the permission to invoke EnOS™ APIs. The resource authorization, that is which devices or data you can access through the API, is enforced through IAM at the account level.

To register an application, click **Application management** from the left navigation panel. For more information, see [Application management](../app_mgmt/app_mgmt_overview).

After the application is successful registered, EnOS assigns a pair of application key and secret. You can view the application details to access the assigned key-secret pair.

## Step 3: Invoking an API

EnOS™ provides Java SDKs for you to program Java codes that invoke EnOS APIs.

This following code samples show you how to use the EnOS™ Java SDKs to obtain the real-time and historical data of assets.

1. Obtain token by calling the `login` API:

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
2. Obtain the real-time data from certain data acquisition points of certain devices.

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
3. Obtain historical data from certain devices for a specified range of time

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
