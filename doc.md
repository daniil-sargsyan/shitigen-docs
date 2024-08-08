# Документация интеграции с 1С

## Пользователи
### Получить пользователя по GUID

* Запрос

```http request
GET https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/user.get?filter[UF_USR_1722587885970]={{GUID}}
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






## Контакты 

### Создать контакт

* Запрос

```http request
POST https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.contact.add
```

```json
{
    "fields":{
        "NAME":"Անուն", 
        "LAST_NAME":"Ազգանուն", 
        "SECOND_NAME":"Հայրանուն",
        "PHONE" : [
            {"VALUE":"+37498888888"},
            {"VALUE":"+37498888888"}
            ], 
        "EMAIL":[
            {"VALUE":"test1@gmail.com"}, 
            {"VALUE":"test2@gmail.com"}
        ], 
        "UF_CRM_1721896329420":"Իրավաբանական հասցե", 
        "UF_CRM_1723108337023":"Գործունեության հասցե",  
        "UF_CRM_664DBFBD43D75":[
            "Կայանի տեղադրման հասցե 1",
            "Կայանի տեղադրման հասցե 2"
            ],  
        "UF_CRM_1707822379207":"Անձնագիր", 
        "UF_CRM_1707822426950":"2024-08-08T14:05:21+04:00", 
        "UF_CRM_1707822448806":"Ում կողմից", 
        "UF_CRM_1707822458574":"ՀԾՀ", 
        "UF_CRM_1707822731302":"464", 
        "UF_CRM_1707822585830":"Հ/Հ", 
        "COMPANY":["62"], 
        "TYPE_ID":"UC_DIUN9M",
        "COMMENTS":"Մեկնաբանություն", 
        "ASSIGNED_BY_ID":"16", 
        "UF_CRM_1707822691457":[
            {"fileData":["test1.txt", "AA=="]},
            {"fileData":["test2.txt", "AA=="]}
        ],
        "UF_CRM_1723100443089":"GUID ID Contact",
        "UF_CRM_1723100456115":"CODE Contact "
    }
}
```
* Ответ

```json
{
    "result": 403,
    "time": {
        "start": 1723117855.28878,
        "finish": 1723117855.63746,
        "duration": 0.3486800193786621,
        "processing": 0.30963587760925293,
        "date_start": "2024-08-08T15:50:55+04:00",
        "date_finish": "2024-08-08T15:50:55+04:00"
    }
}
```

* Описание полей 
```
Запрос

"NAME" Անուն
"LAST_NAME" Ազգանուն
"SECOND_NAME" Հայրանուն
"PHONE"  Հեռախոսահամար 
"EMAIL" E-mail
"UF_CRM_1721896329420" Իրավաբանական հասցե
"UF_CRM_1723108337023" Գործունեության հասցե
"UF_CRM_664DBFBD43D75" Կայանի տեղադրման հասցե
"UF_CRM_1707822379207" Անձնագիր
"UF_CRM_1707822426950" Երբ է տրվել (дата в формате 2024-08-08T14:05:21+04:00)
"UF_CRM_1707822448806" Ում կողմից
"UF_CRM_1707822458574" ՀԾՀ
"UF_CRM_1707822731302" Բանկ (варианты можно получить сделав запрос https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.contact.fields)
"UF_CRM_1707822585830": Հ/Հ
"COMPANY" Կազմակերպություն (массив с id компаний)
"TYPE_ID" Կոնտակտի տեսակ (возможные варианты "CLIENT" - Հաճախորդ, "UC_JVEYP2" - Կոնտակտային անձ, "UC_DIUN9M" - Դիմորդ, "UC_KKSTDO" - Այլ, "" - Не Выбран)
"COMMENTS" Մեկնաբանություն
"ASSIGNED_BY_ID" Պատասխանատու (id пользователя)
"UF_CRM_1707822691457" Files (fileData должен быть массивом , который принемает массив [0] элементом которого является имя файла , [1] элементом файл в кодировке base64)
"UF_CRM_1723100443089" GUID ID Contact 
"UF_CRM_1723100456115" CODE Contact 


Ответ

"result" id созданого контакта

```

### Удалить контакт

```http request
GET https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.contact.delete?ID={{ID}}
```

```{{ID}}``` - id контакта 

### Обновить контакт

* Запрос 

```http request
POST https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.contact.update?ID={{ID}}
```

```{{ID}}``` - id контакта

```json
{
    "fields": {
        "NAME": "Անուն", 
        "LAST_NAME": "Ազգանուն", 
        "SECOND_NAME": "Հայրանուն", 
        "PHONE": [
            {
                "ID":"",
                "VALUE": "+37498888888"
            },
            {
                "ID":"",
                "VALUE": "+37498888889"
            }
        ], 
        "EMAIL": [
            {
                "ID":"",
                "VALUE": "test1@gmail.com"
            },
            {
                "ID":"",
                "VALUE": "test2@gmail.com"
            }
        ], 
        "UF_CRM_1721896329420": "Իրավաբանական հասցե", 
        "UF_CRM_1723108337023": "Գործունեության հասցե", 
        "UF_CRM_664DBFBD43D75": [
            "Կայանի տեղադրման հասցե 1",
            "Կայանի տեղադրման հասցե 2"
        ], 
        "UF_CRM_1707822379207": "Անձնագիր", 
        "UF_CRM_1707822426950": "2024-08-08T14:05:21+04:00", 
        "UF_CRM_1707822448806": "Ում կողմից", 
        "UF_CRM_1707822458574": "ՀԾՀ", 
        "UF_CRM_1707822731302": "464", 
        "UF_CRM_1707822585830": "Հ/Հ", 
        "COMPANY": [
            "62"
        ], 
        "TYPE_ID": "UC_DIUN9M",
        "COMMENTS": "Մեկնաբանություն", 
        "ASSIGNED_BY_ID": "16", 
        "UF_CRM_1707822691457": [
            {
                "fileData": [
                    "test1.txt",
                    "AA=="
                ]
            },
            {
                "fileData": [
                    "test2.txt",
                    "AA=="
                ]
            }
        ], 
        "UF_CRM_1723100443089": "GUID ID Contact", 
        "UF_CRM_1723100456115": "CODE Contact " 
    }
}
```

* Описание полей
```
Запрос

Во всех множественных полях по типу PHONE, EMAIL нужно добавлять ID если если нужно изменить конкретный элемент, если нет ID то добавится новый элемент.
чтобы получить их нужно сделать запрос https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.contact.get?ID={{ID}} где {{ID}} это id контакта

Ответ

"result" true или false

```

## Компании

### Создать компанию 

* Запрос

```http request
POST https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.company.add
```

```json
{
    "fields":{
        "TITLE":"Կազմակերպության անվանում",
        "UF_CRM_1721909503670":"Աշխատանքային անվանում", 
        "PHONE" : [
            {"VALUE":"+37498888888"},
            {"VALUE":"+37498888889"}
            ], 
        "EMAIL":[
            {"VALUE":"test1@gmail.com"}, 
            {"VALUE":"test2@gmail.com"}
        ], 
        "UF_CRM_1721896430796": "Իրավաբանական հասցե", 
        "UF_CRM_1721896453819":"Գործունեության  հասցե", 
        "UF_CRM_1707823114526":"ՀՎՀՀ", 
        "UF_CRM_1707823136855":"259", 
        "UF_CRM_1707823142254":"Հ/Հ", 
        "UF_CRM_664DBFBD53217":["Կայանի տեղադրման հասցե 1", "Կայանի տեղադրման հասցե 2"],  
        "CONTACT":["720"], 
        "COMMENTS":"COMMENTS", 
        "ASSIGNED_BY_ID":"16", 
        "UF_CRM_1707823223708":[
            {"fileData":["test1.txt", "AA=="]},
            {"fileData":["test2.txt", "AA=="]}
        ],
        "UF_CRM_1723100322669":"CODE Company",
        "UF_CRM_1723100288587":"GUID ID Company"
    }
}
```

* Ответ
```json
{
    "result": 404,
    "time": {
        "start": 1723122634.834688,
        "finish": 1723122635.047344,
        "duration": 0.21265602111816406,
        "processing": 0.18756604194641113,
        "date_start": "2024-08-08T17:10:34+04:00",
        "date_finish": "2024-08-08T17:10:35+04:00"
    }
}
```

* Описание полей
```
Запрос

        "TITLE" Կազմակերպության անվանում 
        "UF_CRM_1721909503670" Աշխատանքային անվանում 
        "PHONE" Հեռախոսահամար +
        "EMAIL" E-mail 
        "UF_CRM_1721896430796" Իրավաբանական հասցե 
        "UF_CRM_1721896453819" Գործունեության  հասցե 
        "UF_CRM_1707823114526" ՀՎՀՀ  
        "UF_CRM_1707823136855": Բանկ (варианты можно получить сделав запрос https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.contact.fields)
        "UF_CRM_1707823142254" Հ/Հ 
        "UF_CRM_664DBFBD53217": Կայանի տեղադրման հասցե  
        "CONTACT" Contact (id контакта)
        "COMMENTS" Մեկնաբանություն 
        "ASSIGNED_BY_ID": Պատասխանտու (id пользователя)
        "UF_CRM_1707823223708" Files (fileData должен быть массивом , который принемает массив [0] элементом которого является имя файла , [1] элементом файл в кодировке base64)
        "UF_CRM_1723100322669" CODE Company 
        "UF_CRM_1723100288587" GUID ID Company 

Ответ

"result" id созданой компании

```

### Удалить компанию 

```http request
GET https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.company.delete?ID={{ID}}
```

```{{ID}}``` - id компании


### Обновить компанию

```http request
POST https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.company.update?ID={{ID}}
```
```{{ID}}``` - id компании


* Запрос

```json
{
    "fields":{
        "TITLE":"Կազմակերպության անվանում",
        "UF_CRM_1721909503670":"Աշխատանքային անվանում", 
        "PHONE" : [
            {
              "ID":"9999",
              "VALUE":"+37498888888"
            },
            {
              "ID":"9999",
              "VALUE":"+37498888889"
            }
            ], 
        "EMAIL":[
            {
              "ID":"9999",
              "VALUE":"test1@gmail.com"
            }, 
            {
              "ID":"9999",
              "VALUE":"test2@gmail.com"
            }
        ], 
        "UF_CRM_1721896430796": "Իրավաբանական հասցե", 
        "UF_CRM_1721896453819":"Գործունեության  հասցե", 
        "UF_CRM_1707823114526":"ՀՎՀՀ", 
        "UF_CRM_1707823136855":"259", 
        "UF_CRM_1707823142254":"Հ/Հ", 
        "UF_CRM_664DBFBD53217":["Կայանի տեղադրման հասցե 1", "Կայանի տեղադրման հասցե 2"],  
        "CONTACT":["720"], 
        "COMMENTS":"COMMENTS", 
        "ASSIGNED_BY_ID":"16", 
        "UF_CRM_1707823223708":[
            {"fileData":["test1.txt", "AA=="]},
            {"fileData":["test2.txt", "AA=="]}
        ],
        "UF_CRM_1723100322669":"CODE Company",
        "UF_CRM_1723100288587":"GUID ID Company"
    }
}
```

* Описание полей
```
Запрос

Во всех множественных полях по типу PHONE, EMAIL нужно добавлять ID если если нужно изменить конкретный элемент, если нет ID то добавится новый элемент.
чтобы получить их нужно сделать запрос https://www.shtigen-group.com/rest/1675/asukkakqg9mc3xpz/crm.company.get?ID={{ID}} где {{ID}} это id контакта

Ответ

"result" true или false

```





