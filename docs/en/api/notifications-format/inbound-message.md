# Формат входящего сообщения

Уведомление данного формата приходит при получении входящего сообщения: текст, изображение, видео, голосовое сообщение, документ, контакт, геопозиция.

## Формат уведомления

```json
{
    "type": "notification-type",
    "account": {
        "id": "account-id",
        "wa_id": "account-wa-id"
    },
    "messages": [
        {
            "from": "sender-wa-id",
            "id": "message-id",
            "timestamp": "message-timestamp",
            "type": "text | image | video | voice | document | contacts | location",

            "text": {
                "body": "text-message-content"
            },

            "image": {
                "id": "media-id",
                "mime_type": "media-mime-type",
                "file_extension": "source-file-extension",
                "caption": "image-caption"
            },

            "video": {
                "id": "media-id",
                "mime_type": "media-mime-type",
                "file_extension": "source-file-extension",
                "caption": "video-caption"
            },

            "voice": {
                "id": "media-id",
                "mime_type": "media-mime-type",
                "file_extension": "source-file-extension"
            },

            "document": {
                "id": "media-id",
                "mime_type": "media-mime-type",
                "file_extension": "document-file-extension",
                "filename": "document-file-name"
            },

            "contacts": {
                "vcard": "vcard-data"
            },

            "location": {
                "link": "location-link"
            }

        }
    ],
    "contacts": [
        {
            "profile": {
                "name": "sender-profile-name"
            },
            "wa_id": "sender-wa-id"
        }
    ]
}
```

> Тело уведомления приведено в качестве примера. В примере перечислены все возможные варианты входящих сообщений. Тело действительного ответа может содержать только один объект сообщения: `text`, `image`, `video`, `voice`, `document`, `contacts`, `location`.

## Параметры уведомления {#notification-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`type` | **string** | Тип уведомления. Для входящих сообщений поле принимает значение `inbound_message`
`account` | **object** | [Объект аккаунта](notification-object-account). Содержит данные аккаунта, который получил уведомление
`messages` | **object** | [Объект сообщения](notification-object-messages). Содержит данные полученного сообщения
`contacts` | **object** | [Объект контакта](notification-object-contacts). Содержит данные отправителя сообщения

### Объект `account` {#notification-object-account}

Объект содержит данные аккаунта в системе Green-API

Параметр | Тип | Описание
----- | ----- | -----
`id` | **integer** | Номер аккаунта 
`wa_id` | **string** | Номер телефона аккаунта; получатель входящего уведомления


### Объект `contacts` {#notification-object-contacts}

Объект содержит данные контакта отправителя сообщения

Параметр | Тип | Описание
----- | ----- | -----
`profile` | **object** | Профиль контакта. Содержит имя контакта в поле `name` 
`wa_id` | **string** | Номер телефона контакта


### Объект `messages` {#notification-object-messages}

Объект содержит данные входящего сообщения. В зависимости от параметра `type` сообщение может содержать различные данные: текст, изображение, видео, голосовое сообщение, документ, контакт, геопозицию. 

Параметр | Тип | Описание
----- | ----- | -----
`from` | **string** | [Идентификатор корреспондента или группы](../chat-id.md) - отправитель сообщения
`id` | **string** | Идентификатор полученного сообщения
`timestamp` | **integer** | Время получения сообщения в UNIX-формате
`type` | **string** | Тип полученного сообщения. Возможные значения: `text`, `image`, `video`, `voice`, `document`, `contacts`, `location`
`text` | **object** | [Объект текстового сообщения](#notification-object-messages-text)
`image` | **object** | [Объект с данными изображения](#notification-object-messages-image)
`video` | **object** | [Объект с данными видео](#notification-object-messages-video)
`voice` | **object** | [Объект с данными голосового сообщения](#notification-object-messages-voice)
`document` | **object** | [Объект с данными документа](#notification-object-messages-document)
`contacts` | **object** | [Объект с данными контакта](#notification-object-messages-contacts)
`location` | **object** | [Объект с данными геопозиции](#notification-object-messages-location)

#### Объект `text` {#notification-object-messages-text}

Параметр | Тип | Описание
----- | ----- | -----
`body ` | **string** | Текст полученного сообщения. Может содержать несколько URL и [форматирование](../formatting.md). Максимальная длина текстового сообщения составляет 4096 символов. Поддерживаются символы emoji 😃


#### Объект `image` {#notification-object-messages-image}

Параметр | Тип | Описание
----- | ----- | -----
`id` | **string** | Идентификатор файла изображения из облачного хранилища `media`. Для загрузки файла используйте метод [Получение медиаданных](../media/download.md)
`mime_type` | **string** | [MIME](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_MIME-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2) тип файла
`file_extension` | **string** | Расширение полученного файла, например `jpeg`
`caption` | **string** | Описание полученного изображения. Отображается в чате под изображением

#### Объект `video` {#notification-object-messages-video}

Параметр | Тип | Описание
----- | ----- | -----
`id` | **string** | Идентификатор видео-файла из облачного хранилища `media`. Для загрузки файла используйте метод [Получение медиаданных](../media/download.md)
`mime_type` | **string** | [MIME](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_MIME-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2) тип файла
`file_extension` | **string** | Расширение полученного файла, например `mp4`
`caption` | **string** | Описание полученного видео. Отображается в чате под видео

#### Объект `voice` {#notification-object-messages-voice}

Параметр | Тип | Описание
----- | ----- | -----
`id` | **string** | Идентификатор файла голосового сообщения из облачного хранилища `media`. Для загрузки файла используйте метод [Получение медиаданных](../media/download.md)
`mime_type` | **string** | [MIME](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_MIME-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2) тип файла
`file_extension` | **string** | Расширение полученного файла, например `ppt`

#### Объект `document` {#notification-object-messages-document}

Параметр | Тип | Описание
----- | ----- | -----
`id` | **string** | Идентификатор файла документа из облачного хранилища `media`. Для загрузки файла используйте метод [Получение медиаданных](../media/download.md)
`mime_type` | **string** | [MIME](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_MIME-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2) тип файла
`file_extension` | **string** | Расширение полученного файла, например `pdf`
`filename` | **string** | Полное имя файла документа, указанное при отправке


#### Объект `contacts` {#notification-object-messages-contacts}

Параметр | Тип | Описание
----- | ----- | -----
`vcard ` | **string** | Данные карточки контакта. Например: "\nN:;Green-API\nFN:Green-API\nTEL;WAID=79001234567:+7 900 123 4567\nTEL;WAID=79001234567:+7 900 123 4567\nX-AB-LABEL:\nX-AB-LABEL:\n"


#### Объект `location` {#notification-object-messages-location}

Параметр | Тип | Описание
----- | ----- | -----
`link ` | **string** | Ссылка на геообъект на картах maps.google.com. Например: https://maps.google.com/maps?q=55.7416,37.6201&z=17&hl=ru


## Примеры {#notifications-example}

### Получено текстовое сообщение {#notification-example-text}

```json
{
    "type": "inbound_message",
    "account": {
        "id": 22123456,
        "wa_id": "79001234567"
    },
    "messages": [
        {
            "from": "79001234568",
            "id": "1234",
            "timestamp": 1603666324,
            "text": {
                "body": "I use Green-API to get this message from you!"
            },
            "type": "text"
        }
    ],
    "contacts": [
        {
            "profile": {
                "name": "Andrew"
            },
            "wa_id": "79001234568"
        }
    ]
}
```

### Получено сообщение с изображением {#notification-example-image}

```json
{
    "type": "inbound_message",
    "account": {
        "id": 22123456,
        "wa_id": "79001234567"
    },
    "messages": [
        {
            "from": "79001234568",
            "id": "1234",
            "timestamp": 1603666324,
            "image": {
                "id": "bca567ba-0bd7-4211-8792-0c123fbd2716",
                "mime_type": "image/jpeg",
                "file_extension": "jpeg",
                "caption": "Green-API Logo"
            },
            "type": "image"
        }
    ],
    "contacts": [
        {
            "profile": {
                "name": "Andrew"
            },
            "wa_id": "79001234568"
        }
    ]
}
```

### Получено сообщение с документом {#notification-example-document}

```json
{
    "type": "inbound_message",
    "account": {
        "id": 22123456,
        "wa_id": "79001234567"
    },
    "messages": [
        {
            "from": "79001234568",
            "id": "1234",
            "timestamp": 1603666324,
            "document": {
                "id": "bca567ba-0bd7-4211-8792-0c123fbd2716",
                "mime_type": "application/pdf",
                "file_extension": "pdf",
                "filename": "green-api-presentation.pdf"
            },
            "type": "document"
        }
    ],
    "contacts": [
        {
            "profile": {
                "name": "Andrew"
            },
            "wa_id": "79001234568"
        }
    ]
}
```