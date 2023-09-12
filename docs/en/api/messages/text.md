# Отправка текстовых сообщений

`/v1/messages`

Для отправки текстовых сообщений корреспонденту или в группу используйте узел `messages`.

## Запрос {#request}

Для отправки текстового сообщения требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/v1/messages
```

```json
{
    "recipient_type": "individual" | "group",
    "to": "whatsapp-id" | "whatsapp-group-id",
    "type": "text",
    "text": {
        "body": "your-text-message-content"
    }
}
```

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`recipient_type` | **string** | Нет | Определяет тип получателя - корреспондент или группа. Возможные значения: `individual` - отправка корреспонденту; `group` - отправка в группу. Значение по умолчанию: `individual`
`to` | **string** | Да | [Идентификатор корреспондента или группы](../chat-id.md) - получатель сообщения
`type` | **string** | Нет | Тип отправляемого сообщения. При отправке текстового сообщения указывать параметр не обязательно. Значение по умолчанию: `text`
`text ` | **object** | Да | Объект текстового сообщения

Объект `text`

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`body ` | **string** | Да | Текст сообщения. Может содержать несколько URL и [форматирование](../formatting.md). Максимальная длина текстового сообщения составляет 4096 символов. Поддерживаются символы emoji 😃

### Пример тела запроса {#request-example-body}

Отправка сообщения корреспонденту:
```json
{
    "to": "79001234567",
    "type":"text",    
    "text": {
        "body": "I use Green-API to send this message to you!"
    }    
}
```

Отправка сообщения в группу:
```json
{
    "recipient_type": "group",
    "to": "79001234567-1581234048",
    "type":"text",    
    "text": {
        "body": "I use Green-API to send this message to the Group!"
    }    
}
```
## Ответ {#response}

При успешном ответе возвращается код HTTP `201`

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | -----
`messages` | **array** | Массив идентификаторов отправленных сообщений 


Массив `messages`

Поле | Тип |  Описание
----- | ----- | -----
`id ` | **string** | Идентификатор отправленного сообщения 

### Пример тела ответа {#response-example-body}

```
201 Created
```

```json
{
    "messages": [
        {
            "id": "1234"
        }
    ],
    "meta": {
        "api_status": "stable",
        "version": "2.0.1"
    }
}
```

### Ошибки {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../errors.md)

В случае ошибки возвращается код HTTP `400` с подробным описанием ошибки в теле ответа.

### Пример тела ответа с ошибкой {#response-example-body-error}

```json
{
    "errors": [
        {
            "code": 82,
            "details": "Outgoing messages limit exceeded",
            "title": "Превышено колличество исходящих сообщений"
        }
    ],
    "meta": {
        "api_status": "stable",
        "version": "2.0.1"
    }
}
```

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/v1/messages"

payload = "{\r\n    \"to\": \"79001234567\",\r\n    \"type\":\"text\",    \r\n    \"text\": {\r\n        \"body\": \"I use Green-API to send this message to you!\"\r\n    }    \r\n}"
headers = {
  'Authorization': 'Bearer {{AuthToken}}',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```