# Home work 4

{% file src="../.gitbook/assets/contacts_hw4.zip" %}

Написати API REST для роботи з контактами. Для роботи з REST API використовуй __ [_Postman_](https://www.getpostman.com/)_/_[_Swagger_](https://editor.swagger.io/) _eta._

Для цього створіть гілка з ім'ям node\_hw4

Перед виконанням виконайте такі дії:

* Встановити [npm](https://www.npmjs.com/) - модулі: [express](https://www.npmjs.com/package/express) , [fs](https://www.npmjs.com/package/fs)
* Перевірити .**gitignore**
* Перевірити **README.md**
* Додати скрыпти до **package.json**

## 1 - Отримати список усіх контактів

Додати endpoint для отримання всіх контактів. Контакти мають надходити у форматі `json`.

* Не отримує body
* Викликає функцію `listContacts` для роботи з json-файлом `contacts.json`
* Повертає масив усіх контактів у json-форматі зі статусом 200

{% swagger method="get" path="" baseUrl="http://localhost:3000/api/contacts" summary="Отримати список усіх контактів" %}
{% swagger-description %}
Сервер відправляє відповідь у форматі 

`JSON`

. 

\


Дивіться приклади у вкладках 

_`Request`, `Response`_
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "id": 1,
        "name": "Vasya",
        "email": "vasya@gmail.com",
        "phone": "+380779879992"
    }
]
```
{% endswagger-response %}
{% endswagger %}



## 2 - Отримати контакт з id

Додати endpoint для отримання контакту з id. Контакти мають надходити у форматі json.

* Не отримує `body`
* Отримує параметр `contactId`
* Викликає функцію getById для роботи з json-файлом `contacts.json`
* Якщо такий `id` є, повертає об'єкт контакту у json-форматі зі статусом `200`
* Якщо такого `id` немає, повертає `json` з ключем _"message": "Not found"_ та статусом `404 GET`

{% swagger method="get" path="" baseUrl="http://localhost:3000/api/contacts/:contactId" summary="Отримати контакт з id" %}
{% swagger-description %}
Сервер надсилає відповідь у форматі json. Parameters Path
{% endswagger-description %}

{% swagger-parameter in="path" name="contactId" type="number" required="true" %}
ID контака.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "id": 1,
    "name": "Vasya",
    "email": "vasya@gmail.com",
    "phone": "+380779879992"
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
{
    "message": "Contact not found"
}
```
{% endswagger-response %}
{% endswagger %}

## 3 - Створити контакт

Додати endpoint для створення контакту. Id для контакту створюється за сервера (продовжуємо використовувати логіку першого дз). Створений контакт повинен надходити у форматі json.

* Отримує bodyу форматі _`{name, email, phone}`_
* Якщо body немає якихось обов'язкових полів, повертає json з ключем `{"message": "Missing required name field"}`і статусом 400
* Якщо `bod` yвсе добре, додає унікальний ідентифікатор в об'єкт контакту
* Викликає функцію `addContact(body) д`ля збереження контакту у файлі `contacts.json`
* За результатом роботи функції повертає об'єкт із доданим та статусомid `{id, name, email, phone}` 201&#x20;

{% swagger method="post" path="" baseUrl="http://localhost:3000 /api/contacts" summary="Створити контакт" %}
{% swagger-description %}
Надсилаємо дані на сервер у форматі json. Сервер надсилає відповіддю створений контакт у форматі json. Parameters Header
{% endswagger-description %}

{% swagger-parameter in="header" %}

{% endswagger-parameter %}
{% endswagger %}
