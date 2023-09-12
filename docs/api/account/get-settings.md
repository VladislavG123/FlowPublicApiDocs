# GetSetting

The method is aimed for getting the current account settings.

## Request
To get the current account settings you have to execute a request at:

```
GET https://v1/api/waInstance{{idInstance}}/getSettings/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

## Response
### Response parameters
| **Parameter** |  **Type**  |                                              **Description**                                              |
|:-------------:|:----------:|:---------------------------------------------------------------------------------------------------------:|
|     `wid`     |  **int**   |                                          	Account ID in WhatsApp                                          |
|  `webhookUrl`   | **string** |                                           URL to receive incoming notifications                           |


### Response body example#
```json
{
  "wid": 0,
  "webhookUrl": "string"
}
```