# REST API interpretation

This article aimes to interprete the API request,  request parameters and values, generating signature, assembling HTTP request URL, sending HTTP request, getting HTTP response, and parsing JSON results.

## Components of API request

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

#### Common request parameters

The following table lists the common request parameters required by each EnOS API.

<table>
  <tr>
    <td>Parameter</td>
    <td>Data type</td>
    <td>Required</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>accessKey</td>
    <td>String</td>
    <td>Yes</td>
    <td>APP Key assigned to your application after it is created on EnOS Developer Center.</td>
  </tr>
  <tr>
    <td>secretKey</td>
    <td>String</td>
    <td>Yes</td>
    <td>APP Secret generated for your application after it is created on EnOS Developer Center.</td>
  </tr>
  <tr>
    <td>requestTimestamp</td>
    <td>String</td>
    <td>Yes</td>
    <td>Time when the request is sent (Unix timestamp) from the client. The value of the timestamp is the total UTC milliseconds starting from 00:00:00 of 1970-01-01, for example1536560363020. The server accepts a time difference of no more than 30 minutes.</td>
  </tr>
  <tr>
    <td>sign</td>
    <td>String</td>
    <td>Yes</td>
    <td>The API request signature that is generated based on the accessKey, secretKey, timestamp, and API request parameters. Signature can prevent API requests from malicious tempering. The API gateway will verify the signature, and rejects a request when its signature is invalid. Currently, SHA-1 algorithm is used for generating signature. For more information, see [Generating signature](generating_signature).</td>
  </tr>
</table>

#### Business parameters

In addition to the common parameters, the business parameters for the API requests are also required in the request URL. The business parameters for each API can be found through **EnOS API** > **API Documents** in the EnOS Console.

### Request methods

EnOS API calling methods, including `GET`, `POST`, `PUT`, and `DELETE`. The calling method of each API can be found in the API reference documentation. 


### Request body

`content-type`: The content type of the message body, which defines the data type of the API request body. For example, `application/json;charset=UTF-8`.

## Components of API response

### Response message header

#### Common response parameters

<table>
<tr>
<th>Field</th>
<th>Data type</th>
<th>Description</th>
</tr>
<tr>
<td>requestId</td>
<td>String</td>
<td>API request ID</td>
</tr>
<tr>
<td>status</td>
<td>Int</td>
<td>Status code, see the following section for details.</td>
</tr>
<tr>
<td>msg</td>
<td>String</td>
<td>Message</td>
</tr>
<tr>
<td>submsg</td>
<td>String</td>
<td>Detailed description of the message </td>
</tr>
</table>

#### Status code

HTTP status code, ranging from 2xx success codes to 4xx or 5xx error codes, that indicates the status of the API invocation.

<table>
<tr>
<th>Status code</th>
<th>Description</th>
</tr>
<tr>
<td class="code">0</td>
<td>Request success</td>
</tr>
<tr>
<td class="code">400</td>
<td>Invalid parameter</td>
</tr>
<tr>
<td class="code">401</td>
<td>Authentication failed, possibly caused by unmatch of accessKey and secretKey.</td>
</tr>
<tr>
<td class="code">403</td>
<td>No permission</td>
</tr>
<tr>
<td class="code">404</td>
<td>Resource not found</td>
</tr>
<tr>
<td class="code">405</td>
<td>Method not supported</td>
</tr>
<tr>
<td class="code">409</td>
<td>Resource already exists</td>
</tr>
<tr>
<td class="code">414</td>
<td>Request body size exceeds limit</td>
</tr>
<tr>
<td class="code">415</td>
<td>Request parameter value exceeds limit</td>
</tr>
<tr>
<td class="code">429</td>
<td>Number of requests exceed limit</td>
</tr>
<tr>
<td class="code">497</td>
<td>Timestamp or signature verification failed</td>
</tr>
<tr>
<td class="code">498</td>
<td>No access to resources or API</td>
</tr>
<tr>
<td class="code">499</td>
<td>Client error</td>
</tr>
<tr>
<td class="code">500</td>
<td>Internal service error</td>
</tr>
<tr>
<td class="code">501</td>
<td>API not supported</td>
</tr>
<tr>
<td class="code">503</td>
<td>API service not available</td>
</tr>
<tr>
<td class="code">504</td>
<td>Request timeout</td>
</tr>
<tr>
<td class="code">6xx</td>
<td>Third-party service error codes</td>
</tr>
</table>

### Response message body

You can find the response message body interpretation for each API in the API reference documentation in the EnOS Console.

## Sample HTTP request

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

**Notes：**

- Both the request parameters and response data are in UTF-8 format. Parameters and values must be URL-encoded. If the content type of the request is application/x-www-form-urlencoded, then parameters in the request body must also be URL-encoded. If the content type of the request is multipart/form-data, then parameter of each form field does not need to be encoded, but the charset of each form field should be in UTF-8 format. If the content type of the request is application/json, then the HTTP body should be included in signature generation but does not need to be URL encoded.
- The signature generation process applies to calling APIs without the official API SDK. If you use the official API SDK, the SDK will generate the signature automatically.
