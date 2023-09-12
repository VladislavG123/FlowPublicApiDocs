# Outgoing message status#

Incoming webhook of this type contains the status of a previously sent message: sent, delivered, read, etc.

## Webhook

### Webhook parameters#

| **Parameter**  |  **Type**   |                                                                                                                      **Description**                                                                                                                       |
|:--------------:|:-----------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| `typeWebhook	` | **string**  |                                                                          Incoming webhook type. For webhooks of this type the parameter takes on the value outgoingMessageStatus                                                                           |
|   `chatId	`    | **string**  |                                                                                              Chat Id. Chat with a message for which you received the status.                                                                                               |
| `instanceData` | **object**  |                                                                                                                        Account data                                                                                                                        |
| `timestamp		`  | **integer** |                                                                                                               Event timestamp in UNIX format                                                                                                               |
|  `idMessage	`  | **string**  |                                                 Outgoing message or file Id. Outgoing message Id is returned by methods: SendMessage, SendFileByUrl, SendFileByUpload, SendLocation, SendContact, SendLink                                                 |
|   `status	`    | **string**  |                                                                                                Outgoing message or file status. Status takes on the values:                                                                                                |
|                |             |                                                                                                                   `sent` - message sent                                                                                                                    |
|                |             |                                                                                                      `delivered` - message delivered to the recipient                                                                                                      |
|                |             |                                                                                                    `read` - message read/viewed/heard by the recipient                                                                                                     |
|                |             |                                                                                          `failed` - an error occurred while sending a message to WhatsApp server                                                                                           |
|                |             |                         `noAccount` - the recipient's phone number does not have a WhatsApp account (this status cannot be disabled in the settings SetSettings, it is necessary to implement the processing of this notification)                         |
|                |             |                                                                             `notInGroup` - the sender is not a participant of a group chat where the message is being sent to                                                                              |
|                |             |                                                                                             `yellowCard` - suspension of sending messages due to spam activity                                                                                             |
|        `sendByApi`        |    **boolean**     |                                                                                                       Is the message sent through API: true , false                                                                                                        |


`instanceData` object parameters

|  **Parameter**  |  **Type**   |        **Description**        |
|:---------------:|:-----------:|:-----------------------------:|
|  `idInstance	`  | **integer** |          Account Id           |
|     `wid	`      | **string**  | Account Id in WhatsApp format |
| `typeInstance	` | **object**  |    Account messenger type     |

## Webhook body example#

```json
{
  "typeWebhook": "outgoingMessageStatus",
  "chatId": "71234567890@c.us",
  "instanceData": {
    "idInstance": 1234,
    "wid": "11001234567@c.us",
    "typeInstance": "whatsapp"
  },
  "timestamp": 1586700802,
  "idMessage": "3EB0608D6A2901063D63",
  "status": "noAccount",
  "sendByApi": true
}
```

## Webhook body example#

```
{
    "typeWebhook": "outgoingMessageStatus",
    "chatId": "71234567890@c.us",
    "instanceData": {
        "idInstance": 1234,
        "wid": "11001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1586700802,
    "idMessage": "3EB0608D6A2901063D63",
    "status": "noAccount",
    "sendByApi": true
}
```