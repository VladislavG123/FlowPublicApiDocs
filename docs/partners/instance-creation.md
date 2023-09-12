# CreateInstance#

The method is aimed for creating a messenger account instance on the partner's part.

## Request#

To create an account instance on the partner's part you have to execute a POST request at:

```
https://api/v1/partner/createInstance/{partnerToken}
```

### Request parameters

| **Parameter** |  **Type**  | **Mandatory** |            **Description**             |
|:-------------:|:----------:|:-------------:|:--------------------------------------:|
| `webhookUrl`  | **string** |      Yes      | 	URL for sending webhook notifications |

### Request body example

```json
{
    "webhookUrl": "https://mysite.com/webhook/flow-api/",
}
```

## Response

### Response parameters#

|    **Parameter**     |  **Type**  |      **Description**       |
|:--------------------:|:----------:|:--------------------------:|
|    `idInstance	`     |  **int**   |    account instance id     |
| `apiTokenInstance		` | **string** | account instance API token |

### Response body example#

If successful, in response to the request, you get a JSON string with HTTP 200 status of the below form:

```json
{
    "idInstance": 1101728000,
    "apiTokenInstance": "c1b0474542144e0ead529eb4861ca5f583c346eb00564f64a8",
}
```

In case of failure, you get a response with HTTP 200 status, a JSON string with a code and description of the error is
returned in the response body:

```json
{
    "code": 401,
    "description": "Unauthorized"
}
```
