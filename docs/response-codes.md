The Record Stack Overflow API uses standard [HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) to indicate the success or failure of an API request.


| Error Code | Description |
| :--------: | :------------|
| 200        | OK - Your request was successful. | Error: Record id 
| 400        | Bad Request - Your request is invalid.
| 401        | Unauthorized - Authentication failed or was not provided. | ERROR: "Insufficient privileges" |
| 404        | Not Found - The specified information does not exist. | ERROR: "Record not found. Check record id." |
| 429        | Too Many Requests - Your account reached the maximum amount requests for the allotted time.
| 5xx        | Server error - Error with the Record Stack Overflow server.

### Sample success response

```json
{
  "success_message": "Record deleted",
  "response_code": 200
}
```

### Sample error response
```json
{
  "error_message": "Request failed",
  "response_code": 400  
}
```