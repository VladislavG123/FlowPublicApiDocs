# Incoming text message or URL message#

This section describes `messageData` object incoming webhook format for incoming text message with URL. For a description
of the general format of incoming webhooks, refer to [Incoming messages](index.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `extendedTextMessage`

## Webhook

### Webhook parameters#

`messageData`  object parameters

|         **Parameter**         |  **Type**  |                                         **Description**                                          |
|:-----------------------------:|:----------:|:------------------------------------------------------------------------------------------------:|
|         `typeMessage`         | **string** | Received message type. For messages of this type, the parameter takes on the value `textMessage` |
|      `textMessageData	`       | **object** |                                     Text message data object                                     |
|  `ExtendedTextMessageData	`   | **object** |                                     Text message data object                                     |
|      `FileMessageData	`       | **object** |                                     Text message data object                                     |
| `TemplateButtonReplyMessage	` | **object** |                                     Text message data object                                     |
|   `ButtonsResponseMessage	`   | **object** |                                     Text message data object                                     |
|    `ListResponseMessage	`     | **object** |                                     Text message data object                                     |
|       `ButtonsMessage	`       | **object** |                                     Text message data object                                     |



`extendedTextMessageData` object parameters

|   **Parameter**    |  **Type**  |                                         **Description**                                         |
|:------------------:|:----------:|:-----------------------------------------------------------------------------------------------:|
|       `text`       | **string** |                                   Link text or ordinary text                                    |


### Webhook body example#
```json
{
	"typeWebhook": "incomingMessageReceived",
	"timestamp": 1693566841314,
	"instanceData": {
		"idInstance": 216869,
		"wid": "79955500008@s.whatsapp.net",
		"typeInstance": "whatsapp"
	},
	"idMessage": "3A641D1D383dsa89DFF72C",
	"senderData": {
		"chatId": "79312003547@s.whatsapp.net",
		"sender": "79312573500@s.whatsapp.net",
		"senderName": "Mrs"
	},
	"messageData": {
		"typeMessage": "reactionMessage",
		"textMessageData": null,
		"buttonsMessage": null,
		"buttonsResponseMessage": null,
		"extendedTextMessageData": {
          "text": "https://flow-api.com/docs/video"
        },
		"fileMessageData": null,
		"listResponseMessage": null,
		"templateButtonReplyMessage": null,
		"contactMessageData": null
	}
}
```