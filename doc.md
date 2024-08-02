# Документация интеграции с 1С

## Пользователи
### Получить пользователя по GUID

* Запрос
* 
```http request
GET https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/user.get?filter[UF_WEB_SITES]={{GUID}}
```

```{{GUID}}``` - GUID пользователя в 1C

---

* Ответ

```json
{
    "result": [
      {
        "ID": "99",
        "XML_ID": "",
        "ACTIVE": true,
        "NAME": "Name",
        "LAST_NAME": "Last Name",
        "SECOND_NAME": "",
        "TITLE": "",
        "EMAIL": "email@gmail.com"
      }
    ]
}
```

```result[0][ID]``` - ID пользователя в Битрикс24


