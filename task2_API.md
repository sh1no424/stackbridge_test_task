# Проектирование API
* Принято допущение что пользователь авторизован. Запрос к API выполняется с передачей токена доступа.

## Запрос на отображение магазинов партнеров.
Метод: GET<br>endpoint: api/v1/stores
### Пример запроса на сервер.
```http
GET /api/v1/stores HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
```
## Успешный ответ:

HTTP status 200 OK
```http
HTTP/1.1 200 OK
Content-Type: application/json
```
```json
    {"stores":
        [
            {
                "id": "metro",
                "name": "METRO",
                "logoUrl": "https://img.examples/metro.png",
                "dilivery":{
                    "type": "ontime",
                    "title": "Ближайшая доставка",
                    "text": "сегодня 21:00 - 23:00"
                },
                "storeURL": "https://metro.example"
            },
            {
                "id": "ashan",
                "name": "Ашан",
                "logoUrl": "https://img.examples/ashan.png",
                "dilivery":{
                    "type": "ontime",
                    "title": "Ближайшая доставка",
                    "text": "сегодня 18:00 - 20:00"
                },
                "storeURL": "https://ashan.example"
            },
            {
                "id": "vkusvill",
                "name": "ВкусВилл",
                "logoURL": "https://img.examples/vkusvill.png",
                "dilivery":{
                    "type": "express",
                    "title": "Быстрая доставка",
                    "text": "от 20 до 60 минут"
                },
                "storeURL": "https://vkusvill.example"
            },
            {
                "id": "victoria",
                "name": "ВИКТОРИЯ",
                "logoURL": "https://img.examples/victoria.png",
                "dilivery":{
                    "type": "ontime",
                    "title": "Ближайшая доставка",
                    "text": "сегодня 17:00 - 19:00"
                },
                "storeURL": "https://victoria.example"
            }

        ]

    }
```
## Возможные ошибки

* 400 - Bad Request. Неккоректный запрос.
* 401 - Пользователь не авторизирован.
* 403 - Нет прав. 
* 500 - Внутренняя ошибка сервера. 

### Пример ответа с ошибкой. 

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json
```
```json
{
    "error": {
        "code": "Bad Request",
        "message": "Некорректный запрос"
    }
}
```