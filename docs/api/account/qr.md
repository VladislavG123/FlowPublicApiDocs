# QR

The method is aimed for getting QR code.
To authorize your account, you have to scan a QR code from application WhatsApp Business on your phone.
You can also get a QR code and authorize your account in your profile.
The procedure for authorizing an account in your profile is described in section Before you start.

> QR code is updated every 20 seconds, therefore, it is recommended to request the method for getting a QR code with a
> delay in 1 second.

To get a QR code, the account must have an unauthorized status. If the account is authorized, you have first to log out
the account using Logout method. After successful scanning a QR code and authorizing the account incoming notification
in
form of Account Status is generated.

> You can also get a QR code via websocket-connection

## Request

To get a QR code, you have to execute a request at:

```
GET https://api.v1/waInstance{{idInstance}}/qr/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

## Response

### Response parameter

| **Parameter** |  **Type**  |                                                 **Description**                                                 |
|:-------------:|:----------:|:---------------------------------------------------------------------------------------------------------------:|
|    `type`     | **string** |                       Message type, possible variants `qrCode`, `error`, `alreadyLogged`                        |
|   `message`   | **string** | `base64` - R code image. To display in the browser, you need to add a string `data:image/png;base64, {message}` |

#### Got QR

| **Parameter** |  **Type**  |                                                 **Description**                                                 |
|:-------------:|:----------:|:---------------------------------------------------------------------------------------------------------------:|
|    `type`     | **string** |                                          `qrCode` - got QR code image                                           |
|   `message`   | **string** | `base64` - R code image. To display in the browser, you need to add a string `data:image/png;base64, {message}` |

#### Error occurred

| **Parameter** |  **Type**  |                                                                                        **Description**                                                                                        |
|:-------------:|:----------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `type`     | **string** |                                                                                `error` -  an error is occurred                                                                                |
|   `message`   | **string** |                                                                                       Error description                                                                                       |      
|               |            | `Instance has auth. You need to make log out` - there is authorization data, but they are not suitable for authorization, it is necessary to execute the logout method and rescan the QR code |

> Getting a QR code can take up to 10 minutes

#### Account already authorized

| **Parameter** |  **Type**  |                                                         **Description**                                                          |
|:-------------:|:----------:|:--------------------------------------------------------------------------------------------------------------------------------:|
|    `type`     | **string** | `alreadyLogged` - account is already authorized. To get a QR code, you have first to log out of your account using Logout method |
|   `message`   | **string** |                                     Takes on the value `instance account already authorized`                                     |

## Example of getting a QR code in a browser

```
https://api/v1/waInstance{{idInstance}}/{{apiTokenInstance}}
```

- `idInstance` - account unique number
- `apiTokenInstance` - account access key

> You need to replace the idInstance and apiTokenInstance values with yours to get a link like this:
>
> `https://api/v1/waInstance11015502/ccc44689b17435537c15a939d0a478b71c3bd7d7d52d312345`