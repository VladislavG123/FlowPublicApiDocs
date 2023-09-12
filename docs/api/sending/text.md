# SendMessage#

The method is aimed for sending a text message to a personal or a group chat. The message will be added to the send
queue.

## Request

To send a text message, you have to execute a request at:

```
POST https://api/v1/waInstance{{idInstance}}/sendMessage/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

### Request parameters

| **Parameter** |  **Type**  | **Mandatory** |                **Description**                |
|:-------------:|:----------:|:-------------:|:---------------------------------------------:|
|   `chatId`    | **string** |      Yes      |                   		Chat Id                   |
|   `message`   | **string** |      Yes      | 		Message text. Emoji 😃 characters supported |

> The maximum length of a text message is 4096 characters

### Request body example#

Sending a message to a chat:

```json
{
    "chatId": "11001234567@c.us",
    "message": "I use Flow-API to send this message to you!"
}
```

## Response

### Response parameters#

| **Parameter** |  **Type**  | **Description** |
|:-------------:|:----------:|:---------------:|
|  `idMessage`  | **string** | Sent message Id |

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```
