# Reboot

The method is aimed for rebooting an account.

## Request
To reboot the account, you have to execute a request at:

```
GET https://v1/api/waInstance{{idInstance}}/reboot/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

## Response
### Response parameter
| **Parameter** |  **Type**   |                                                **Description**                                                |
|:-------------:|:-----------:|:-------------------------------------------------------------------------------------------------------------:|
|  `isReboot`   | **boolean** |                                     Result of rebooting WhatsApp account                                      |

### Response body example#

```json
{
    "isReboot": true
}
```