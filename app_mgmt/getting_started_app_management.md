# Getting started with application management

This topic gets you started with application management on EnOS.

## Before you begin

Use the EnOS™ device connection service to connect your asset data into EnOS™ cloud. For more information, see [Device connection](https://docs.envisioniot.com/docs/device-connection/en/latest/deviceconnection_overview.html).

If you do not have devices to connect, you can use the device simulator that EnOS™ provides to simulate data transmission and build your application based on the simulated data. For more information, see [Simulating devices](simulating_device).

## Step 1: Register an application and test authorization

EnOS™ provides a complete application development process to help you access the data through EnOS APIs and perform application development offline.

Click **Application Management** from the left navigation panel and click **New App**, fill in the application information and save. The application is successfully registered.

## Step 2: Purchase the application

After an application is registered, the application exists on EnOS™ cloud and is available for purchase. You can access the data only after purchasing the application.

Currently, the purchase action is done by the EnOS™ system administrator. But if you are the application owner, you can purchase the application registered by yourself.

## Step 3: Authorize application to access assets and data

After an application is purchased by a client, asset authorization can then be performed for the application. The application can access the asset data of the client only when the application asset authorization is completed. The major procedure is as follows:

1. Click **Access Control > Application Authorization** to check the overview of asset authorization for all applications.

2. Click the application to authorize for accessing assets and data.

## Step 4: Test authorization

After an application is purchased and the asset authorization is completed, you can test authorization through **API Service > API Test**. This tool can verify whether the authorization is successful or not when client data is obtained through the EnOS™ API.

## Step 5: Develop applications with EnOS™ SDK offline

EnOS™ provides EnOS™ APIs and supporting Java SDKs to help you quickly develop applications offline.

1. Create a project and import EnOS™ SDK.

   Create a test project in the application development IDE and import the EnOS™ SDKs.

2. Obtain the latest device data

   After importing the SDK, you can start programming with the SDK APIs.

   The following code sample shows how to obtain the latest data of a device:

   ```java
   import com.envision.eeop.api.EnvisionClient;
   import com.envision.eeop.api.EnvisionDefaultClient;
   import com.envision.eeop.api.domain.DomainPoint;
   import com.envision.eeop.api.request.MdmDomainPointsGetRequest;
   import com.envision.eeop.api.request.UserLoginRequest;
   import com.envision.eeop.api.response.MdmDomainPointsGetResponse;
   import com.envision.eeop.api.response.UserLoginResponse;

   import java.util.Arrays;
   import java.util.List;
   import java.util.Map;

   public class eeop_test {
      // Please  ENTER the url of EnOS API
      static String baseUrl = "https://xxx.envisioncn.com/eeop";
      //Please ENTER the applicationKey of your application
      static String applicationKey = "applicationId";
      //Please ENTER the applicationSecret of your application
      static String applicationSec = "applicationSec";

      static String name = "name";
      static String password = "password";

      public static void main(String[] args) throws Exception {
          EnvisionClient client = new EnvisionDefaultClient( baseUrl , applicationId, applicationSec);

          //1. get access token
          UserLoginRequest loginRequest = new UserLoginRequest();
          loginRequest.setName(name);
          loginRequest.setPassword(password);
          UserLoginResponse loginResponse = client.execute(loginRequest);
          String token = loginResponse.getAccessToken();

          //the points of your devices
          List pointIDList =  Arrays.asList("INV.Freq", "INV.State");
          //the devices
          List    deviceIDList = Arrays.asList("1c15eecc96002000");
          //the fields of these points
          List fieldList = Arrays.asList("value", "timestamp");

          //Request and Response
          MdmDomainPointsGetRequest request = new MdmDomainPointsGetRequest(deviceIDList, pointIDList, fieldList);
          MdmDomainPointsGetResponse response = client.execute(request,token);

          for(Map.Entry<String, DomainPoint> entry : response.getMdmMap().entrySet()) {
              System.out.println(entry.getKey() + " => " + entry.getValue().getPointValueMap());
          }
      }
   }

   ```

3. After you complete the coding, click **Run** to test application.
