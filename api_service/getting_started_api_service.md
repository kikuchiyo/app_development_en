# Getting started with api service

## Step1: Create an API group
Users can log in to the configuration center to configure the parameters and information of the API gateway.

After logging in to the configuration center, users use the operations shown below to configure the API Gateway.

1) Create a group: On the API gateway, a group must be created before creating an API and may contain more than one API.

2) Enter the API list to create and manage APIs.


## Step 2: Create an API

Example: Basic information --> Define API requests --> Define back-end API services --> Define return results.

- Basic information: This step completes the API group selection, API name setting and API description.

- Define API requests: This step completes the request style when a third-party user invokes an API on EnOS™.

- Define back-end API services: This step completes the style definition of API requests that the backend service receives. That is, the user sends the API invocation to the API gateway according to the front-end configuration completed in the previous step, and then the API gateway requests your back-end by parsing your mapping rules and according to your requirements, so as to guarantee the lowest cost transformation and maximum compatibility of the back-end service. In other words, this step is to configure the gateway request style definition when the gateway requests your back end, so as to conform to the established format of your back end.

- At present, the return results are not parsed in the API gateway, and the API gateway directly forwards them to the requester of the API.


## Step3: Release API

Click Release to fill in  relevant information to release the API.

- Whether to enable data permission validation: Data permission validation can be enabled to confirm whether the user is legal. Token: used to verify the user's token (required), mdmids: used to verify that the user has permission to operate mdmid under the App.

- Whether to enable signature: The API gateway service authenticates each access request, and any user’s request needs to include signature information in the request. (In order to prevent the malicious tampering or embezzlement during API invocation, the developer needs to generate the signature according to the App Key, App Secret and request parameters, and the server will validate the signature. A request with illegal signature will be rejected.)

## Step4: Access to API

After you release the API, you can check the url by clicking the API details. You can access the data by entering the url using tools such as postman and filling in appropriate parameters.
