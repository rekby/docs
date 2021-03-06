# options method

Checks whether a CORS request to an object can be made.

## Request {#request}

```
OPTIONS /{bucket}/{key} HTTP/1.1
```

### Path parameters {#path-parameters}

| Parameter | Description |
| ----- | ----- |
| `bucket` | Name of the bucket. |
| `key` | Object key. ID to use for saving the object in Object Storage. |

### Headers {#request-headers}

| Header name | Description |
| --------- | -------- |
| `Origin` | Request source domain.<br/><br/>For instance, `http://www.example.com`.<br/><br/>Mandatory. |
| `Access-Control-Request-Method` | HTTP method to be used to send a request to a resource.<br/><br/>Mandatory. |
| `Access-Control-Request-Headers` | List of headers to be sent in a subsequent request to the object. Headers are separated by commas.<br/><br/>Optional. |

You should also use the necessary [common request headers](../common-request-headers.md)

## Response {#response}

### Headers {#response-headers}

In addition to the [common response headers](../common-response-headers.md), a response may contain:

| Header name | Description |
| --------- | -------- |
| `Access-Control-Allow-Origin` | The domain that was passed in the `Origin` request header.<br/><br/>If the [CORS configuration](../cors/upload.md#request-scheme) has the `AllowedOrigin` element set to `*`, then the `Access-Control-Allow-Origin` header value will also be `*`.<br/><br/>If access from the domain is not allowed, Object Storage returns error 403 and all `Access-Control-*` headers are missing. |
| `Access-Control-Max-Age` | Allowed response caching time (in seconds). |
| `Access-Control-Allow-Methods` | Allowed request methods. If there are no methods allowed, Object Storage returns error 403 and all `Access-Control-*` headers are missing. |
| `Access-Control-Allow-Headers` | List of HTTP headers that can be used in a subsequent request to the object. If there are no headers allowed, this header is not included in a response. |
| `Access-Control-Expose-Headers` | List of HTTP headers that the JavaScript client will receive. |

### Response codes {#response-codes}

The method returns:

- 200: if requests to the object are allowed.
- 403: if requests to the object are not allowed.

For detailed descriptions of response codes, see [#T](../response-codes.md).

