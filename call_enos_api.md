# Calling EnOS REST APIs

This topic describes how to call EnOS REST APIs by assembling API request URL with parameters, generating signature, sending HTTP request, getting HTTP response, and parsing JSON results.

## Components of Request

Assembling HTTP requests to call APIs is the process of the building REST API URL manually or with API calling tools and then calling EnOS APIs through the URL.

### Request URL

EnOS REST API URL takes the following format:

```
{service-url} / {api-path} ? {query-string}
```
where,
- `service-url`: https://enos-api-cn1.envisioniot.com/
- `api-path`：The URL of each EnOS API (refer to the API documentation)
- `query-string`: Request parameters to be included in the request URL. The string comprises of common request parameters and business-specific request parameters.

In the following sample request URL, the `api-path` segment is `/connectService/products/{productKey}` and the `query-string` segment is `accessKey={}&requestTimestamp={}&sign={}&orgId={}`.
```
GET https://enos-api-cn1.envisioniot.com/connectService/products/{productKey}?accessKey={}&requestTimestamp={}&sign={}&orgId={}
```

### Common Request Parameters

The following table lists the common request parameters required by each EnOS API.

.. list-table::
   :widths: 20 20 10 50

   * - Parameter
     - Data type
     - Required
     - Description
   * - Content-Type
     - String
     - Yes
     - Data uploading method. Generally, set its value as "application/json;charset=UTF-8"; For uploading files or forms, set its value as "multipart/form-data;charset=UTF-8".
   * - accessKey
     - String
     - Yes
     - APP Key assigned to your application after it is created on EnOS Developer Center.
   * - secretKey
     - String
     - Yes
     - APP Secret generated for your application after it is created on EnOS Developer Center.
   * - requestTimestamp
     - String
     - Yes
     - Time when the request is sent (Unix timestamp) from the client. The value of the timestamp is the total UTC milliseconds starting from 00:00:00 of 1970-01-01, for example1536560363020. The server accepts a time difference of no more than 30 minutes.
   * - sign
     - String
     - Yes
     - The API request signature that is generated based on the accessKey, secretKey, timestamp, and API request parameters. Signature can prevent API requests from malicious tempering. The API gateway will verify the signature, and rejects a request when its signature is invalid. Currently, SHA-1 algorithm is used for generating signature. For more information, see Generating signature.

### Business Parameters

In addition to the common parameters, the business parameters for the API requests are also required in the request URL. The business parameters for each API can be found through **EnOS API** > **API Documents** in the EnOS Console.

### Request Methods

EnOS API calling methods, including `GET`, `POST`, `PUT`, and `DELETE`. The calling method of each API can be found in the API reference documentation.


### Request Body

`content-type`: The content type of the message body, which defines the data type of the API request body. For example, `application/json;charset=UTF-8`.

## Components of Response

The following table lists the common response parameters of each API request.

### Common Response Parameters

.. list-table::
   :header-rows: 1
   :widths: 25 25 50

   * - Field
     - Data type
     - Description
   * - requestId
     - String
     - API request ID
   * - status
     - Int
     - Status code, see the following section for details.
   * - msg
     - String
     - Message
   * - submsg
     - String
     - Detailed description of the message


### Status Code

HTTP status code, ranging from 2xx success codes to 4xx or 5xx error codes, that indicates the status of the API invocation.

.. list-table::
   :header-rows: 1

   * - Status code
     - Description
   * - 0
     - Request success
   * - 400
     - Invalid parameter
   * - 401
     - Authentication failed, possibly caused by unmatch of accessKey and secretKey.
   * - 403
     - No permission
   * - 404
     - Resource not found
   * - 405
     - Method not supported
   * - 409
     - Resource already exists
   * - 414
     - Request body size exceeds limit
   * - 415
     - Request parameter value exceeds limit
   * - 429
     - Number of requests exceed limit
   * - 497
     - Timestamp or signature verification failed
   * - 498
     - No access to resources or API
   * - 499
     - Client error
   * - 500
     - Internal service error
   * - 501
     - API not supported
   * - 503
     - API service not available
   * - 504
     - Request timeout
   * - 6xx
     - Third-party service error codes


### Response Message Body

You can find the response message body interpretation for each API in the API reference documentation in the EnOS Console.

## Sample HTTP Request

Using the `getProduct` API as an example, take the following steps to assemble the HTTP request.

**1. List request parameters and values**

Common request parameter:

```
requestTimestamp = "1536560363020"
```

Business parameter:

```
orgId = "123"
productKey = "12345"
```

**2. Sort the parameters by parameter name in ASCII order**

```
orgId = "123"
productKey = "12345"
requestTimestamp = "1536560363020"

```

**3. Concatenate the sorted parameters and values into a string**

```
orgId123productKey12345requestTimestamp1536560363020
```

**4. Generate signature**

Assume that the values of `accessKey` and `secretKey` are `accessKeyExample` and `secretKeyExample`, then the signature is:

```
hex(md5(accessKeyExample+orgId123productKey12345requestTimestamp1536560363020+secretKeyExample)) = "4A6936C442CC34C5C42B9E06D97F2FA268B7E52F"
```

**5. Put everything together**

Encode all parameters and values (including the sign parameter) in UTF-8 format (parameters can be in random order) and send the request by the correct API method (GET or POST). For example:

```
http://xxx.envisioniot.com/enosapi/connectService/products/12345?orgId=123&productKey=12345&requestTimestamp=1536560363020&accessKey=accessKeyExample&secretKey=secretKeyExample&sign=4A6936C442CC34C5C42B9E06D97F2FA268B7E52F
```

.. note:: - Both the request parameters and response data are in UTF-8 format. Parameters and values must be URL-encoded. If the content type of the request is application/x-www-form-urlencoded, then parameters in the request body must also be URL-encoded. If the content type of the request is multipart/form-data, then parameter of each form field does not need to be encoded, but the charset of each form field should be in UTF-8 format. If the content type of the request is application/json, then the HTTP body should be included in signature generation but does not need to be URL encoded.
         - the signature generation process applies to calling apis without the official api sdk. if you use the official api sdk, the sdk will generate the signature automatically.

<!--end-->
