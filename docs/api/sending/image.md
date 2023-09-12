# SendFileByUrl#

The method is aimed for sending a file uploaded by Url. The message will be added to the send queue. Right now only
images supported.

> The minimum interval for sending messages from the queue using the SendFileByUrl method is 5 seconds.

Images are sent in the same way as in native-mode WhatsApp. Description can be added to images

> The maximum size of outgoing files is 100 MB.

## Request

To send a file, you have to execute a request at:

```
POST https://api/v1/waInstance{{idInstance}}/sendFileByUrl/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

### Request parameters

| **Parameter** |  **Type**  | **Mandatory** |    **Description**    |
|:-------------:|:----------:|:-------------:|:---------------------:|
|   `chatId`    | **string** |      Yes      |       	Chat Id        |
|  `urlImage`   | **string** |      Yes      | Link to outgoing file |
|   `caption`   | **string** |      No       |    	File caption.     |

### Request body example#

Sending a message to a chat:

```json
{
    "chatId": "11001234567@c.us",
    "urlFile": "https://my.site.com/img/horse.png",
    "fileName": "horse.png",
    "caption": "Little horse"
}
```

## Response#

### Response parameters#

| **Parameter** |  **Type**  |   **Description**   |
|:-------------:|:----------:|:-------------------:|
|  `idMessage`  | **string** | Outgoing message Id |

### Response body example#
```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```