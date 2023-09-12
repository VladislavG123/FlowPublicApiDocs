# CheckWhatsapp#

The method checks WhatsApp account availability on a phone number.

## Request

To check WhatsApp account availability, you have to execute request at:

```
POST https://api/v1/waInstance{{idInstance}}/checkWhatsapp/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

### Request parameters

| **Parameter** |  **Type**   | **Mandatory** |                                             **Description**                                              |
|:-------------:|:-----------:|:-------------:|:--------------------------------------------------------------------------------------------------------:|
| `phoneNumber` | **integer** |      Yes      | 	Recipient's phone number in international format: 11 or 12 digits; Example: 11001234567 or 380123456789 |

## Request parameter

```json
{
    "phoneNumber": 11001234567
}
```

## Response

### Response parameters#

|  **Parameter**   |  **Type**   |                 **Description**                 |
|:----------------:|:-----------:|:-----------------------------------------------:|
| `existsWhatsapp` | **boolean** | Flag of WhatsApp availability on a phone number |

### Response body example#
```json
{
    "existsWhatsapp": true
}
```