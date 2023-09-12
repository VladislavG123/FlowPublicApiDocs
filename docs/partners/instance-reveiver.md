# GetInstances#

The method is aimed for getting all the account instances created by the partner.

## Request

To get all the account instances you have to execute a GET request at:

```
https://api/v1/partner/getInstances/{partnerToken}
```

## Response
### Response parameters#

|   **Parameter**    |   **Type**   |                     **Description**                     |
|:------------------:|:------------:|:-------------------------------------------------------:|
|    `idInstance`    | **intenger** |                   Account instance id                   |
| `apiTokenInstance` |  **string**  |               Account instance API token                |
|  `expirationDate`  |  **string**  | Instance expiration date (Partner instances auto-renew) |

### Response body example#
If successful, in response to the request, you get a JSON string with HTTP 200 status of the below form:

```json
{
  "idInstance": 1101728004,
  "apiTokenInstance": "1f2485e80f474293b935f77d78c64e76fa4bdceb417a4998a4",
  "expirationDate": "2022-06-09T18:39:44"
}
```
In case of failure, a response with HTTP 400 status and an error text is returned.

