# HTTP Status Codes - Client and Server Errors

## Client Errors (4xx)

### 400 Bad Request
- **Description**: Request cannot be processed due to client error
- **Common Scenario**: Something in the request doesn't make sense or doesn't exist
- **Impact**: The server cannot understand or process the request

### 401 Unauthorized
- **Description**: Authorization required for resource access
- **Details**: Server indicates required authentication method(s)
- **Resolution**: Client must provide valid credentials
- **Note**: Common authentication schemes are supported

### 403 Forbidden
- **Description**: Access to the requested resource is not allowed
- **Details**: Server understands request but refuses to authorize
- **Impact**: Non-specific response indicating request is not permitted
- **Difference from 401**: Authentication isn't the issue, but rather permissions

### 404 Not Found
- **Description**: Resource not found at specified address
- **Common Causes**: 
  - Dead links
  - Misspelled addresses
  - Removed or relocated resources
- **Impact**: Resource cannot be located at the specified URL

### 413 Request Entity Too Large
- **Description**: Request body exceeds server limits
- **Details**: Message body is too large for server processing
- **Response**: May include Retry-After header if temporary
- **Impact**: Connection might be closed by server

### 414 Request URI Too Large
- **Description**: URI length exceeds server limits
- **Details**: Server unwilling to process due to URI length
- **Common Cause**: Extremely long query parameters

### 429 Too Many Requests
- **Description**: Rate limit exceeded
- **Details**: Too many HTTP requests within time period
- **Scope**: May be user-specific or resource-level
- **Resolution**: Wait for rate limit reset

## Server Errors (5xx)

### 500 Internal Server Error
- **Description**: Generic server error
- **Details**: Server encountered unexpected error fulfilling request
- **Impact**: Request cannot be completed due to server issues
- **Type**: Catch-all server error response

### 502 Bad Gateway
- **Description**: Proxy error with upstream server
- **Common Scenario**: Invalid response from application server to proxy
- **Example**: Nginx as reverse proxy failing to get valid response
- **Cause**: Often due to misconfigurations

### 503 Service Unavailable
- **Description**: Server temporarily unable to handle requests
- **Common Causes**:
  - Maintenance
  - Traffic overload
  - Service downtime
- **Nature**: Temporary condition
- **Response**: May include retry information

## General Notes
1. These status codes are part of the HTTP protocol
2. 4xx errors indicate client-side issues
3. 5xx errors indicate server-side issues
4. Proper error handling should implement appropriate responses
5. Monitoring these errors helps maintain service quality
