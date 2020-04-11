# Errors

Customize Your Demo uses conventional HTTP response codes to indicate the success or failure of an API request. 

## HTTP status codes

Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.). Codes in the 5xx range indicate an error with Customize Your Demo's servers.

Code | Status | Meaning
---- | ------ | -------
200 | OK | Everything worked as expected.
400 | Bad Request | Your request is invalid, often due to missing a required parameter.
401 | Authentication failed | Missing or invalid credentials. 
403 | Authorization failed | The requested action is not permitted for the authenticated user.
404 | Not Found | The requested resource doesn't exist.
405 | Method Not Allowed | The requested resource does not support the requested action. 
406 | Not Acceptable | You requested a format that isn't json.
410 | Gone | The requested resource or action has been removed from our servers.
429 | Too Many Requests | Too many requests hit the API too quickly. We recommend an exponential backoff of your requests.
500 | Internal Server Error | We had a problem with our server. Try again later.
503 | Service Unavailable | We're temporarily offline for maintenance. Please try again later.

## Attributes

Attribute | Type | Description
--------- | -----| -----------
code | string | Some 4xx errors that could be handled programmatically include an error code that briefly explains the error reported. See error codes specified in the endpoint section. 
parameter | string | The parameter related to the error. 
message | string | A human-readable message providing more details about the error.


