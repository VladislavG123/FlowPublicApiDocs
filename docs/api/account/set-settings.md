# SetSetting

The method is aimed for setting account settings.

> When this method is requested, the account is rebooted.

## Request

To set account settings, you have to execute a request at:

```
POST https://v1/api/waInstance{{idInstance}}/setSettings/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

### Request parameters

| **Parameter** |  **Type**  | **Mandatory** |                                                  **Description**                                                  |
|:-------------:|:----------:|:-------------:|:-----------------------------------------------------------------------------------------------------------------:|
| `webhookUrl`  | **string** |      No       | 	URL for sending notifications. If it is required to disable getting notifications, then specify an empty string. |

### General request body example#

```json
{
    "webhookUrl": "https://mysite.com/webhook/flow-api/"
}
```

## Response

### Response parameters#

| **Parameter**  |  **Type**   |         **Description**          |
|:--------------:|:-----------:|:--------------------------------:|
| `saveSettings` | **boolean** | Flag that the settings are saved |

### Response body example#

```json
{
    "saveSettings": true
}
```