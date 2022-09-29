# Lesson 1 - Фундаментальний Node.js

## Налаштування оточення для Node js

{% content-ref url="quick-start.md" %}
[quick-start.md](quick-start.md)
{% endcontent-ref %}



## Прийом та обробка HTTP-запитів.

### **HTTP**

HTTP означає Hypertext Transfer Protocol (\* протокол прикладного рівня для "переговорів" про доставлення Web-сервером документа Web-браузеру. Зазвичай використовує порт 80, а у якості протоколу транспортного рівня - TCP

TCP (\* Transmission Control Protocol; протокол керування передаванням; широко використовуваний в Інтернеті мережний протокол транспортного рівня з набору TCP/IP.

**HTTP дозволяє спілкуватися системам з різною архітектурою та конфігурацією мережі (\* певний склад обладнання ЛОМ (локальна обчислювальна мережа), схему його з'єднання та ПЗ мережі).**\


<figure><img src="https://lh6.googleusercontent.com/RKyV4fPqL_rWMX0xKiin2nX7rl9_9i0S4gjqGS6Zp_iZs7aNwbfWUqQPeoitFwQZkx7i-fbLJXzwzqvhBZ6CXXzaySvCpeC5HEZpFhvUr7FhtF4cuix20QRG8zARGUiy1pM3eTH1ZlQPsNgdfrBq0mxa9XeSCbgootTu4nJHb3PNn9_tpWWDYPPYWQ" alt=""><figcaption></figcaption></figure>

### URL-адреси

В основі комунікації по Всесвітній павутині лежать повідомлення запитів, які пересилаються за допомогою URL-адрес (\* Uniform Resource Locator – уніфікований покажчик \[місцезнаходження інформаційного] ресурсу).

<figure><img src="https://lh6.googleusercontent.com/_Oft27nnkzTkeYRDMnLsswYVkdRLXoeUcHbmD9Gg0FOKNvUYQBQJpYra7TshOoMYZ25w3BjMWmiG_rVuIr6pKMW0F-ZcpZCeaIOE5mh1ja9tNJvp2sGSf4e2cVSS96rgl0C9UsJ0l4qDdkQfnwiVkKPwVEjIT9Mv8F65sbAWw4dVyV_UHHmx9TnjgQ" alt=""><figcaption></figcaption></figure>

HTTPS (інші назви: HTTP over TLS, HTTP over SSL, і HTTP Secure) — схема URI, що синтаксично ідентична http: схемі, яка зазвичай використовується для доступу до ресурсів Інтернет. Використання https: URL вказує, що протокол HTTP має використовуватися, але з іншим портом за замовчуванням (443) і додатковим шаром шифрування/автентифікації між HTTP і TCP.

### Методи

URL-адреси ідентифікують певний сервер, із яким ми хочемо налагодити обмін повідомленнями, проте дія, яку необхідно виконати на сервері, вказується за допомогою методів HTTP

* GET: для запиту ресурсу. В URL-адресі міститься вся необхідна інформація для визначення місцезнаходження та повернення ресурсу сервером.&#x20;
* POST: для створення нового ресурсу. Запити POST звичайно містять дані для створення нового ресурсу.&#x20;
* PUT: для оновлення існуючого ресурсу. У вмісті можуть знаходитися оновлені дані для ресурсу.
* &#x20;DELETE: для видалення існуючого ресурсу.&#x20;
* HEAD: подібний до GET, проте не передається тіло повідомлення. Він використовується для отримання заголовків певного ресурсу від сервера, звичайно для того, щоб перевірити за допомогою тимчасової позначки, чи не змінився ресурс.&#x20;
* TRACE: використовується для отримання від сервера інформації про "стрибки" (\*найближчий маршрутизатор, маршрутизатор, що знаходиться на відстані одного "стрибка"), через які пройшов запит.
  1.

<figure><img src="https://lh5.googleusercontent.com/WUuNMm5DMIwZT2SU4vujiw4ATYdahSgLGj2T9-wMD2IlaJvjItbn-Iq9keLZbXfTlmMKFtuA33qoEDNZ552xl6K28rSRNkdmtRvPVkbefupoAfDAAOCZGp1WDx7wC1NjoGeMxtoIURfoA3rK8e2yDVMHMLANow8YFHtoPPke6r8vf7jVxXBmioxsCQ" alt=""><figcaption></figcaption></figure>

* OPTIONS: для отримання підтримуваних сервером можливостей. На стороні клієнта його можна використовувати для зміни запиту в залежності від можливостей, підтримуваних сервером.

### **Коди стану (коди помилок).**

**1xx: Інформація про процес передачі**

* **100** Continue (Продовжувати) (код та відповідна пояснююча фраза)

**2xx: Інформація про вдалий прийом та оброблення запиту клієнта**

* **202** Accepted (\* Прийнято): запит було прийнято на оброблення але у відповіді може не бути запитуваних даних. Цей варіант корисний для асинхронної обробки на стороні сервера.
* **204** No Content (Немає вмісту): тіло повідомлення не передається.
* **205** Reset Content (Скинути вміст): клієнт повинен скинути) уведені користувачем дан.
* **206** Partial Content (Частковий вміст) вказує, що у відповіді міститься тільки частина даних.

**3xx: Переадресація**

* **301** Moved Permanently (Постійно переміщений): запитуваний об'єкт було остаточно перенесено на новий URL.
* **303** See Other (Дивитися інший): запитуваний об'єкт було тимчасово перенесено на нову URL-адресу. Тимчасовий URL вказується у заголовку Location відповіді.
* **304** Not Modified (Не модифікований): сервер виявив, що ресурс не було змінено і клієнту варто використовувати копію з кеш-пам'яті. Це реалізується за допомогою того, що клієнт відправляє певне хеш-значення значення у заголовку ETag (Entity Tag). Сервер порівнює це значення зі своїм власним токеном для запитуваного ресурсу на наявність змін.

**4xx: Інформація про помилки з боку клієнта**

* **400** Bad Request (Зіпсований запит): у запиті знайдено помилку.
* **401** Unauthorized (Несанкціонований доступ): для здійснення запиту необхідна автентифікація
* **403** Forbidden (Заборонено): сервер відмовив клієнту у доступі до вказаного ресурсу.
* **405** Method Not Allowed (Метод не допустимий): у рядку запиту використовувався неприпустимий метод HTTP або ж сервер не підтримує цей метод.
* **409** Conflict (Конфлікт): сервер не зміг виконати запит, оскільки клієнт спробував змінити ресурс, відмітка часу якого не співпадає з такою клієнта. У більшості випадків конфліктна ситуація виникає при сумісному редагуванні ресурсу за допомогою запитів за методом PUT.

**5xx: Інформація про помилки з боку сервера**

* **501 Not Implemented** (\* Не реалізовано): сервер на цей момент не підтримує можливостей, необхідних для оброблення запиту.
* **503 Service Unavailable** (\* Сервіс недоступний): сервер не має можливості оброблювати запити з технічних причин або перевантажений.

більше інформації [тут](https://www.w3.org/Protocols/rfc2616/rfc2616.html)

## Организация коду Node.js

У сучасному JavaScript залишилося два основні стандарти модульних систем. Це CommonJS, яка є основною для платформи Node.js, та ESM (ECMAScript 6 модулі), яка була прийнята як стандарт для мови та внесена до специфікації [**ES2015**](https://262.ecma-international.org/6.0/#sec-modules)****

### Що таке модулі?

Node js програма має модульну архітектуру побудови, причому кожен файл JavaScript розглядається як окремий модуль, який може залежати від інших модулів. Node js модулі можуть бути встановлювані (з використанням npm) та власні, які створюються у процесі розробки. Будь-який проект складніше Hello World складається з деякої кількості файлів, по яких розносять код.

### &#x20;**М**одули на commonjs та ES modules синтаксисе

Модулі CommonJS — це оригінальний спосіб упаковки коду JavaScript для Node.js. Node.js також підтримує стандарт [**модулів**](https://nodejs.org/api/esm.html) **** [**ECMAScript**](https://nodejs.org/api/esm.html) **** який використовується в браузерах та інших середовищах виконання JavaScript.

У Node.js кожен файл розглядається як окремий модуль. Наприклад, розглянемо файл з назвою foo.js:

```
const circle = require('./circle.js');
console.log(`The area of a circle of radius 4 is ${circle.area(4)}`);
```

У першому рядку foo.js завантажує модуль circle.js, який знаходиться в тому ж каталозі, що й foo.js.&#x20;

Ось вміст circle.js

```
const { PI } = Math;
exports.area = (r) => PI * r ** 2;
exports.circumference = (r) => 2 * PI * r;
```

Модуль circle.js експортував функції area()та circumference(). Функції та об’єкти додаються до кореня модуля шляхом визначення додаткових властивостей спеціального exports об’єкта. Змінні, локальні для модуля, будуть приватними, оскільки модуль загорнутий у функцію Node.js (дивіться оболонку модуля ). У цьому прикладі змінна PI є приватною для circle.js. Властивості module.exports можна призначити нове значення (наприклад, функцію чи об’єкт). Нижче bar.js використовується square модуль, який експортує клас Square:

```
const Square = require('./square.js');
const mySquare = new Square(2);
console.log(`The area of mySquare is ${mySquare.area()}`);
```

Модуль square визначено в square.js:

```
// Assigning to exports will not modify module, must use module.exports
module.exports = class Square {
  constructor(width) {
    this.width = width;
  }

  area() {
    return this.width ** 2;
  }
};
```

За замовчуванням Node.js розглядатиме наступне як модулі CommonJS:

* Файли з .cjs розширенням;
* Файли з .js розширенням, коли найближчий батьківський package.json файл містить поле верхнього рівня "type"зі значенням "commonjs".
* Файли з .js розширенням, коли найближчий батьківський package.json файл не містить поля верхнього рівня "type". Автори пакетів повинні включити це "type"поле, навіть у пакетах, де всі джерела є CommonJS. Якщо чітко typeрозповісти про пакет, інструментам збірки та завантажувачам буде легше визначити, як слід інтерпретувати файли в пакеті.
* Файли з розширенням, відмінним від .mjs, .cjs, .json, .node або .js (якщо найближчий батьківський package.json файл містить поле верхнього рівня "type"зі значенням "module", ці файли будуть розпізнані як модулі
* CommonJS лише в тому випадку, якщо їх буде створено require, а не під час використання команди -точка входу рядка програми).

{% hint style="info" %}
Виклик require() завжди використовує завантажувач модуля CommonJS. Для виклику import() завжди використовуйте завантажувач модуля ECMAScript.
{% endhint %}

[**Область застосування модуля**](https://nodejs.org/api/modules.html#the-module-scope)

* [**\_\_dirname**](https://nodejs.org/api/modules.html#\_\_dirname)
* [**\_\_filename**](https://nodejs.org/api/modules.html#\_\_filename)
* [**exports**](https://nodejs.org/api/modules.html#exports)
* [**module**](https://nodejs.org/api/modules.html#module)
* [**require(id)**](https://nodejs.org/api/modules.html#requireid)

[**Об'єкт module\_**](https://nodejs.org/api/modules.html#the-module-object)

* [**module.children**](https://nodejs.org/api/modules.html#modulechildren)
* [**module.exports**](https://nodejs.org/api/modules.html#moduleexports)
* [**module.filename**](https://nodejs.org/api/modules.html#modulefilename)
* [**module.id**](https://nodejs.org/api/modules.html#moduleid)
* [**module.isPreloading**](https://nodejs.org/api/modules.html#moduleispreloading)
* [**module.loaded**](https://nodejs.org/api/modules.html#moduleloaded)
* [**module.parent**](https://nodejs.org/api/modules.html#moduleparent) **(depricated)**
* [**module.path**](https://nodejs.org/api/modules.html#modulepath)
* [**module.paths**](https://nodejs.org/api/modules.html#modulepaths)
* [**module.require(id)**](https://nodejs.org/api/modules.html#modulerequireid)

## Налагодження процесу Node.js: скрипти, витоку пам'яті.



## Життя та смерть Node.JS-процесу, подійний цикл. Макротаски та мікротаски, особливості роботи в Node.js.

## HTTP сервер, асинхронна модель Node.js.



*
