# Error Handling

> Example of failed API request: API key not provided

```shell
curl "https://staging.dental-referrals.org/react4r/v2/available_forms"
```
> Response:

```json
{
    "status":"error",
    "message":"Not Authorized. Check that you are providing a valid API key and that you have access to requested resource."
}
```

If a request is invalid or is missing required parameters, a standard HTTP 400 or 422 response code will be returned. Additionally, a custom error message response will be returned with additional clarifications.

### Error Response Format

In case of an error, in addition to an error status code, the response will contain the following fields:

Field | Description
--------- | -----------
status  | The value will be set to "error".
message | A human-readable description of the error.

## Error Codes

Code | Meaning
--------- | -----------
400  | Bad parameter value or required parameter is missing. Check `message` for more details.
401  | Authorization error. Make sure you are passing your API key as part of the `Authorization` header. Refer to [Authentication](#authentication) section.
404  | Entity not found. For example, you are making a call to [Add File](#add-file) API method with an expired `FILEUPLOAD_ID` (these expire after the prepared form has been submitted by user in the browser.)
422  | Required `patient_dob` parameter is missing.
500 | An unhandled API error has occurred. Please contact [API administrators](mailto:office@dental-referrals.org) to report.
