# API Management
API Service provides API hosting service of high performance and high availability, and can supply you with comprehensive API publishing, management, and maintenance life cycle management. All you need to do is some simple operations to open data or services quickly at low cost and low risk.

At API Service you can:

**Manage your API**

You can manage the whole life cycle of your API, covering operations such as create, test, publish, deactivate and delete.

**Easy safety protection**

- Support Appkey authentication, support SHA-1 algorithm signature.
- Support SSL/TSL encryption.
- Support to enable data access validation, and there is authentication for the access permission for resources on EnOS™ System.


**Openness cost reduction**

Automatically generate API document for you, reduce the openness cost for API

## Create an API
- To create an API is to type in the definition of the API, support the request mode of "input parameters mapping"
- To create an API, you need to type in the general information, service information, request information and return information of the API.

### Part 1: Define the general information of the request
General information of an API includes API group, API name, security authentication method, API type and description.

When creating an API, you need to select the group. Group is the management unit of the API, before creating an API, you need to create a group first (See API Openness for the detailed description of API group).  
API name: the name identification of an API, which needs to be manually input.  
Description: Functional description of an API, which would be   generated in the API document.
### Part 2: Define API request
This part is to define how the users can request your API, including protocols, Method, Path and definition of input parameters.

- Protocols  
 API calling supports HTTP/HTTPS protocol.
- Method  
Support standard HTTP Method, you can choose from GET and POST

- Path  
Path refers to the request path of an API relative to the service host. The Request Path may be diffrent from the actual Path of the backend service, you can randomly wirte a legitimate Path with clear semantics for user. You can configure dynamic parameters in the Request Path, i.e. request users to input parameters in the Path, meanwhile, your backend doesn't need to recive in the Path, it may be mapped to be received in positions such as Query, Header, etc. There are detailed illustrations in Open API Access API Service, which have clearer screenshot displays.

- Request mode of input parameters.  
Processing mode of API Service for input parameters, support "Input Parameters Mapping"

- Definition of input parameters.  
Define your API's request input parameters, including, parameter name, parameter position, type, required or not, defaut value, example, description, etc. There is no need to input parameters under the Input Parameters Transparent Mode.

**Parameter name**: parameter name displys for users.  
**Parameter position**: Position of the parameter in the request, including, Head, Query, Body, Path（Parameter Path), when you configure dynamic parameters in the Path, there is an eponymous parameter at the position of Parameter Path.  
**Type**: type of field, support: String, Int, Long, Float, Double, and Boolean.  
**Required or not**: refers to whether required to be filled or not, when select Yes, API Service would verify whether there is the parameter in user's request, if it is absent, the user request would be refused.  
**Exemple**: refers to the example for the filled parameters, and parameter exemples when an API document is generated, and when the API is published in the market.     
**Description**：Description of the purpose of the parameter and relevant precautions in use, and parameters description when an API document is generated, and when the API is published in the market.
### Part 3: Define the backend service information
This part is primarily to define the front- and back-end mapping of some parameters, the specific description is the API configuration of your actual backedn service. When user's request arrives API Service, API Service will map it into the corresponding request form of the actual backend service according to your backend configuration, to request your backend. Including backend service address, Backend Path and backend timeout.

- Backend service type.  

At present, we support HTTP and HTTPS. If your service is HTTPS, please note that there must be an SSL certificate.
- Backend service address  

The host of backend service, can be a domain name, as well as in form of host:port.
- Backend Path  

Path is the request path for your API service at your backend server, it is the actual request path. If your Backend Path needs to receive dynamic parameters, please declare which parameter at the position from which the caller input the parameter, i.e. declare the mapping relation.
- Backend timeout  

It means that when an API request arrives API Service, the responding time taken by API Service to call the API backend service. It starts from the backend of API Service request to the point that API Service receives the return result from the backend. It should not be longer than 30 seconds. API Service would give up requesting backend service for values over 30 seconds, and return the corresponding error to user.

.. note:: All the input parameters, including, dynamic parameters in Path, Headers parameter, Query parameter, Body parameter (non-binary), constant parameter, system parameter, the parameter name of which should be globally unique. That means, it is not allowed to have parameters in Headers and Query with the same name.

### Part 4: Define return result
You need to input return ContentType, return result example, example of failed return result and definition of error code, which will be generated as an API document and display in the API market.

## API openness

You can open the API service after finishing creating an API. EnOS™ System provides every API hosted with a unified access domain name: https://ag-cn2.envisioniot.com, after defining and publishing an API, input the unified access domain name+API request path and  relevant configuration parameter in postman, then you can access the interface data.
During the process from the creation to the openess of an API, you can also create, modify, delete, view, test, publish and deactivate the API at any time.

## API management
The definition of API refers to the various definitions for the request structure of API when you create an API. You can view, edit, delete, create, publish, deactivate, and test API definition at the console. Special attentions should be paid to the following tips:

- If you need to edit the definition of some API and the API has already been published, no influence on the online production would be caused by the modification, the modified definition could only be updated to the online environment after republishing.
- If you want to delete some API and the API has already been published, you can't delete the API definition directly, the API should be deactivated first, then be deleted.

**API publishing management**
When you finish creating an API, you can publish the API online. You can also deactivate the API which has been published online.

**API permission and security validation**
If your API has already been published, all the APPs created on EnOS™ System have permission to call this API.

- Data permission validation: you can enable data permission validation to confirm the legitimacy of users and whether the user has the permission to the interface data. token: used to validate the user's token（required), mdmids: used to validate whether the user has the authority to operate mdmid under the App.

- Signature validation: API gateway service can authenticate every request for visit, all user requests should include signature information of sign.(To avoid malicious tempering or usurp during API calling, the developer should generate the signature according to App Key, App Secret and request parameters, the Server side would validate the signature and a request without valid signature would be refused).


## API test tool
EnOS™  system provides a unified API test tools, for all the API on the system (including EnOS™ API, the public API, private API), the testing tool has the following advantages

- According to the definition of each API, automatic loading API parameters, sample- with its platform and integrated application through some general algorithm (such as a signature algorithm)
- Help the user to automatically generate appKey, sign and token parameters, etc

When you're done after the release of the API, you can to test these apis.

1. **choose a API**  
For you have permission to API, you can choose a API group under a API for testing.
2. **enter the parameter**  
Test tool willautomatic load parameters and samples  according to the definition of the API, at the same time it get through the APP management and integrated management through some of the common algorithm, help API automatically generated appKey, sign and token parameters.
3. **test the api**  
click the "test" button ，you can test this api with these parameters and result will be shown on the right.
