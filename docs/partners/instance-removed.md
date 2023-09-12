# DeleteInstanceAccount#

The method is aimed for deleting an instance of the partners's account.

## Request

To delete an instance on the partner's part you have to execute a POST request at:

```
https://api/v1/partner/deleteInstanceAccount/{partnerToken}
```

### Request parameters

| **Parameter** | **Type** | **Mandatory** |   **Description**    |
|:-------------:|:--------:|:-------------:|:--------------------:|
| `idInstance`  | **int**  |      Yes      | 	account instance id |

### Request body example

```json
{
    "idInstance": 1101000000
}
```

## Response

### Response parameters#

|      **Parameter**       |  **Type**   |        **Description**         |
|:------------------------:|:-----------:|:------------------------------:|
| `deleteInstanceAccount	` | **boolean** | account instance deletion flag |

### Response body example#

If successful, in response to the request, you get a JSON string with HTTP 200 status of the below form:

```json
{
    "deleteInstanceAccount": true
}
```

In case of failure, you get a response with HTTP 200 status, a JSON string with a code and description of the error is returned in the response body:

```json
{
    "code": 401,
    "description": "Unauthorized"
}
```
