# Lesson 3 - Юніт- та функціональне тестування

## Типи тестування, тестові фреймворки, відмінності, інструментарій

Тестування є невід'ємною частиною програмного забезпечення. Зазвичай програмісти запускають код, який тестує розроблені ними додатки, при внесенні змін, щоб переконатися, що все працює, як треба. При правильних налаштуваннях цей процес можна автоматизувати, що дозволяє значно заощадити час. Запуск тестів безпосередньо після написання нового коду гарантує збереження функцій, що існували раніше. Таким чином, розробник може бути впевненим у базі коду, особливо коли вона впроваджується у виробниче середовище, щоб користувачі могли взаємодіяти з нею.

### **Підхід до створення тестів**

Досягти якісного написання тестів можна у разі, якщо під час написання тестів орієнтуватися **** на вимоги до продукту. Структура тесту ділиться на три частини:

* Що тестується? Наприклад - метод `ProductsService.addNewProduct`&#x20;
* За яким сценарієм та за яких обставин проводиться тест? Наприклад, перевіряється реакція системи у ситуації, коли методу не передали ціну товару;
* Якими є очікувані результати тестування? Наприклад, у подібній ситуації система відмовляється підтверджувати додавання до неї нового товару.

Нижче наведено приклад такого коду:

{% code lineNumbers="true" %}
```javascript
//1. тестований модуль
describe('Products Service', function() {
  //2. сценарій 
  describe('Add new product', function() {
    // 3. те, чого чекають від тесту
    it('When no price is specified, then the product status is pending approval', ()=> {
      const newProduct = new ProductService().add(...);
      expect(newProduct.status).to.equal('pendingApproval');
    });
  });
});
```
{% endcode %}

Звіт про тестування нагадує документ, що містить виклад вимог до продукту.

<figure><img src="https://lh3.googleusercontent.com/PQ-YbnI10JCh6o8wxXAox0ToVVeJk9iW_p4rtA02a0Oml8WRYzNtq6tlb0puJ8Wg1QNc03lc5IwDZpwwxPz0a7LaX0NaHbNabVt2iC43TmlQG1sJ_XbOUZLP6gkfF1CWL3U_mubIglodWNw4iM5bf9gcw5BiNhAh_LjRAXkxmjx9LQc76VNkFYZ0CA" alt=""><figcaption></figcaption></figure>

Ось як це виглядає на різних рівнях.

### **Різновид тестів**

Ось найбільш важливі типи тестування веб-сайтів:

#### **Юніт-тестування**

Це таке тестування окремих блоків (юнітів), таких як функції або класи, шляхом порівняння вихідних даних з очікуваним результатом:  `expect(fn(5)).to.be(10)`

#### **Інтеграційне тестування**&#x20;

Тестування процесів декількох блоків, разом з їхніми сторонніми ефектами:

{% code lineNumbers="true" %}
```javascript
const flyDroneButton = document.getElementById('fly-drone-button')
flyDroneButton.click()
assert(isDroneFlyingCommandSent())
//або навіть
drone.checkIfFlyingViaBluetooth()
.then(isFlying => assert(isFlying))
```
{% endcode %}

#### **Функціональне тестування (також відоме як e2e)**

Тестування поведінки функцій безпосередньо на готовому продукті шляхом контролю браузера чи веб-сайту. Зазвичай такі тести ігнорують внутрішню структуру застосунку та розглядають його як чорну скриньку.&#x20;

Перейдіть на сторінку "https://localhost:3303"

Введіть "test-user" у полі "#username"&#x20;

Введіть "test-pass" у полі "#password"&#x20;

Натисніть на "#login"&#x20;

Очікуйте перехід на сторінку "https://localhost:3303/dashboard"

Очікуйте, що значення "#name" буде "test-name

### **Типи інструментів тестування**

Інструменти для тестування можна згрупувати за їх функціональними можливостями. Деякі обмежуються однією функціональністю, інші більш універсальні. Для досягнення максимальної гнучкості зазвичай використовують поєднання декількох інструментів.

1. Лаунчери тестів запускають ваші тести у браузері чи Node.js з конфігурацією користувача за допомогою CLI або UI. Такого ж ефекту можна досягнути, відкриваючи браузер вручну ([**Karma**](https://karma-runner.github.io/)**,** [**Jasmine**](http://jasmine.github.io/)**,** [**Jest**](https://facebook.github.io/jest/)**,** [**TestCafe**](https://github.com/DevExpress/testcafe)**,** [**Cypress**](https://www.cypress.io/));
2. Інструменти, що піклуються про структуру тестування, допоможуть організувати тестові файли ([**Mocha**](https://mochajs.org/)**,** [**Jasmine**](http://jasmine.github.io/)**,** [**Jest**](https://facebook.github.io/jest/)**,** [**Cucumber**](https://github.com/cucumber/cucumber-js)**,** [**TestCafe**](https://github.com/DevExpress/testcafe)**,** [**Cypress**](https://www.cypress.io/));
3. Assert-функції перевіряють результат тесту на відповідність очікуваному ([**Chai**](http://chaijs.com/)**,** [**Jasmine**](http://jasmine.github.io/)**,** [**Jest**](https://facebook.github.io/jest/)**,** [**Unexpected**](http://unexpected.js.org/)**,** [**TestCafe**](https://github.com/DevExpress/testcafe)**,** [**Cypress**](https://www.cypress.io/));
4. Інструменти, що генерують і відображають перебіг тесту та його результати([**Mocha**](https://mochajs.org/)**,** [**Jasmine**](http://jasmine.github.io/)**,** [**Jest**](https://facebook.github.io/jest/)**,** [**Karma**](https://karma-runner.github.io/)**,** [**TestCafe**](https://github.com/DevExpress/testcafe)**,** [**Cypress**](https://www.cypress.io/));
5. Mock, spy та stub для ізоляції певних частин тестів та відстеження їх сторонніх ефектів ([**Sinon**](http://sinonjs.org/)**,** [**Jasmine**](http://jasmine.github.io/)**,** [**enzyme**](http://airbnb.io/enzyme/docs/api/)**,** [**Jest**](https://facebook.github.io/jest/)**,** [**testdouble**](https://github.com/testdouble/testdouble.js));
6. Інструменти, що генерують та порівнюють знімки структур компонентів та даних, аби переконатися у застосуванні змін від попередніх запусків ([**Jest**](https://facebook.github.io/jest/)**,** [**Ava**](https://github.com/avajs/ava));
7. Інструменти, що генерують звіти про покриття коду, щоб дізнатись, скільки коду покривається вашими тестами ([**Istanbul**](https://gotwarlost.github.io/istanbul/)**,** [**Jest**](https://facebook.github.io/jest/)**,** [**Blanket**](http://blanketjs.org/));
8. Контролери браузера імітують дії користувача для функціональних тестів ([**Nightwatch**](http://nightwatchjs.org/)**,** [**Nightmare**](http://www.nightmarejs.org/)**,** [**Phantom**](http://phantomjs.org/)**,** [**Casper**](http://casperjs.org/)**,** [**TestCafe**](https://github.com/DevExpress/testcafe)**,** [**Cypress**](https://www.cypress.io/));
9. Інструменти візуальної регресії використовуються для візуального порівняння сайту з попередніми версіями за допомогою методів порівняння зображень ([**Applitools**](https://applitools.com/)**,** [**Percy**](https://percy.io/)**,** [**Wraith**](http://bbc-news.github.io/wraith/)**,** [**WebdriverCSS**](https://github.com/webdriverio-boneyard/webdrivercss)).

Почніть з вибору структури тестування та синтаксису, який вам подобається, бібліотеки assert-функцій та вирішіть, як ви хочете запускати тести. Деякі фреймворки, на зразок [**Jest**](https://facebook.github.io/jest/docs/en/snapshot-testing.html)**,** [**Jasmine**](https://jasmine.github.io/)**,** [**TestCafe**](https://devexpress.github.io/testcafe/) та [**Cypress**](https://www.cypress.io/), мають увесь перелічений функціонал з коробки. Інші ж пропонують лише частковий функціонал, який можна доповнити комбінацією декількох бібліотек (наприклад, [**mocha**](https://mochajs.org/) + [**chai**](https://www.chaijs.com/) + [**sinon**](https://sinonjs.org/)). Найкраще створювати два різних процеси. Один для запуску модульних та інтеграційних тестів, а інший — для функціональних тестів. Усе тому, що функціональні тести зазвичай потребують більше часу, особливо для запуску набору тестів в декількох різних браузерах. Подумайте, коли запускати той чи інший тип тесту. Наприклад: модульний+інтеграційний для кожної зміни, функціональний — лише перед комітами.

## Написання юніт-тестів за допомогою Mocha, для тестування класів та функцій.

### Створення модуля Node

Давайте начнем с написания модуля Node.js, который мы будем тестировать. Этот модуль будет управлять списком элементов TODO. Для начала необходимо настроить среду программирования. Создайте папку с именем проекта в своем терминале. В данном обучающем руководстве будет использоваться имя <mark style="color:yellow;">`todos`</mark>:

```bash
mkdir todos
```

Потім відкрийте цю папку:

```bash
cd todos
```

Тепер ініціалізуйте [npm](https://www.npmjs.com/), оскільки пізніше ми будемо використовувати його функцію командного рядка для запуску тестування:

```bash
npm init -y
```

У нас є лише одна залежність, Mocha, яку ми будемо використовувати для організації та запуску тестів. Для завантаження та встановлення Mocha скористайтеся наступною командою:

```bash
npm i request --save-dev mocha
```

Ми встановимо Mocha як залежність dev, оскільки він не використовується для production. Створимо файл, який міститиме код нашого модуля:

```bash
touch index.js
```

Тепер ми готові створити наш модуль. Відкрийте <mark style="color:blue;">`index.js`</mark>​​​  у текстовому редакторі, наприклад <mark style="color:blue;">`nano`</mark>

```bash
nano index.js
```

Почнемо з визначення класу <mark style="color:yellow;">`Todos`</mark> . Цей клас містить усі функції , необхідні для керування нашим списком TODO. Додайте наступні рядки коду до <mark style="color:blue;">`index.js`</mark>:

{% code title="todos/index.js" lineNumbers="true" %}
```javascript
class Todos {
    constructor() {
        this.todos = [];
    }
}

module.exports = Todos;
```
{% endcode %}

Почнемо із створення класу `Todos`. Його функція `constructor()` не приймає аргументів, тому нам не потрібно надавати значення для створення об'єкта для цього класу. Все, що ми робимо, коли ініціалізуємо об'єкт `Todos`, - це створює властивість `todos`, яка є порожнім масивом.

Лінія `модулів` дозволяє іншим модулям Node.js вимагати нашого класу `Todos`. Без прямого експорту класу тестовий файл, який ми створимо пізніше, зможе використовувати його.

Додамо функцію повернення збереженого масиву `todos:`

{% code title="todos/index.js" lineNumbers="true" %}
```javascript
class Todos {
    constructor() {
        this.todos = [];
    }

    list() {
        return [...this.todos];
    }
}

module.exports = Todos;
```
{% endcode %}

Функція `list()` повертає копію масиву класу. Вона робить копію масиву, використовуючи JavaScript, що деструктурує синтаксис. Ми створюємо копію масиву, щоб зміни, які користувач вносить до масиву, поверненого функцією `list()`, не впливали на масив, який використовується об'єктом `Todos`.

{% hint style="info" %}
Масиви JavaScript – це _довідкові файли_. Це означає, що для будь-якого надання змінної для масиву або виклику функції з масивом як параметр JavaScript звертається до оригінального створеного масиву. Наприклад, якщо у нас є масив з трьома елементами з ім'ям <mark style="color:orange;">`x`</mark> і ми створюємо нову змінну <mark style="color:orange;">`y`</mark>, то <mark style="color:orange;">`y =`</mark>` ``x`, <mark style="color:orange;">`y`</mark> і <mark style="color:orange;">`x`</mark> відносяться до одного і того ж. Всі зміни, що виконуються для масиву з y впливають на змінну <mark style="color:orange;">`x`</mark> і навпаки.
{% endhint %}

Тепер створимо функцію `add()`, яка додає новий елемент TODO:

{% code title="todos/index.js" lineNumbers="true" %}
```javascript
class Todos {
    constructor() {
        this.todos = [];
    }

    list() {
        return [...this.todos];
    }

    add(title) {
        let todo = {
            title: title,
            completed: false,
        }

        this.todos.push(todo);
    }
}

module.exports = Todos;
```
{% endcode %}

Наша функція `add()` бере рядок і поміщає її у властивість `title` нового об'єкта JavaScript. Новий об'єкт також має властивість `completed`, яка за умовчанням встановлюється на `false`. Потім ми додаємо новий об'єкт до нашого масиву TODO.

Важливою функцією менеджера TODO є позначка елементів як завершені. Для виконання цього завдання ми пройдемо в циклі нашим масивом `todos`, щоб знайти елемент TODO, який шукає користувач. Якщо елемент знайдено, позначимо його як завершений. Якщо нічого не знайдено, видамо помилку.

Додайте функцію `complete()`​ наступним чином:

{% code title="" lineNumbers="true" %}
```javascript
class Todos {
    constructor() {
        this.todos = [];
    }

    list() {
        return [...this.todos];
    }

    add(title) {
        let todo = {
            title: title,
            completed: false,
        }

        this.todos.push(todo);
    }

    complete(title) {
        let todoFound = false;
        this.todos.forEach((todo) => {
            if (todo.title === title) {
                todo.completed = true;
                todoFound = true;
                return;
            }
        });

        if (!todoFound) {
            throw new Error(`No TODO was found with the title: "${title}"`);
        }
    }
}

module.exports = Todos;
```
{% endcode %}

Збережіть файл і вийдіть із текстового редактора.

Тепер у нас базовий менеджер TODO, з яким можна експериментувати. Далі перевіримо код вручну, щоб переконатися у роботі програми.

### Ручне тестування коду

На даному етапі ми запустимо функції нашого коду та подивимося на висновок, щоб переконатися, що він відповідає очікуванням. Це називається _тестуванням вручну_. Воно виконується аналогічно найпоширенішим методам тестування, які використовуються програмістами. Хоча пізніше ми автоматизуємо тестування за допомогою Mocha, спочатку протестуємо наш код вручну, щоб мати найкраще уявлення про те, як тестування вручну відрізняється від тестових фреймворків.

Додамо до нашого додатку два елементи TODO і відзначимо один із них як завершений. Запустіть [Node.js REPL](https://www.digitalocean.com/community/tutorials/how-to-use-the-node-js-repl) у тій же папці, що й файл `index.js`

Ви побачите командний рядок `>` REPL, який вказує, що ми можемо ввести код JavaScript.

За допомогою `require()` ми завантажуємо модуль TODO змінну `Todos`. Пам'ятайте, що модуль повертає клас `Todos` за замовчуванням. Тепер інстанцуємо об'єкт цього класу.

Ми можемо використовувати об'єкт `todos` для перевірки роботи реалізації.

Досі ми не бачили жодних висновків у нашому терміналі. Упевнімося, що ми зберегли елемент TODO `run code`, отримавши список всіх наших TODO:

```javascript
const Todos = require('./index');
const todos = new Todos();
todos.add("run code");
todos.list();
```

Ви побачите наступний висновок у вашому REPL:

```javascript
Output
[ { title: 'run code', completed: false } ]
```

Це очікуваний результат: ми маємо один елемент TODO у нашому масиві TODO, і він не завершений за умовчанням.

Додамо інший елемент TODO:

```bash
todos.add("test everything");
```

Відзначимо перший елемент TODO як завершений:

```bash
todos.complete("run code");
```

Тепер наш об'єкт `todos` буде управляти двома елементами: `run code` і `test everything`. TODO `run code` також буде завершено. Підтвердимо це, викликавши `list()` ще раз:

```bash
todos.list();
```

Результат REPL буде виглядати так:

```javascript
Output
[
  { title: 'run code', completed: true },
  { title: 'test everything', completed: false }
]
```

Закрити REPL потрібно так:

```bash
.exit
```

Ми підтвердили, що наш модуль працює належним чином. Хоча ми не помістили наш код у тестовий файл та не використовували тестову бібліотеку, ми вручну протестували код. На жаль, ця форма тестування займе багато часу, якщо її використовувати під час кожної зміни. Далі спробуємо виконати автоматизоване тестування в Node.js і подивимося, чи можна вирішити цю проблему за допомогою тестового фреймворку Mocha.

### Створення першого тесту за допомогою Mocha та Assert

В останньому кроці ми вручну протестували нашу програму. Це працюватиме в окремих випадках, але в міру масштабування модуля цей метод стане менш доцільним. Оскільки тестуються нові функції, необхідно переконатись, що додана функціональність не створила проблем у попередньому варіанті. Ми хотіли б протестувати кожну функцію ще раз для кожної зміни в коді, але виконання цього завдання вручну вимагатиме величезних зусиль і збільшить ймовірність виникнення помилок.

Набагато ефективніше настроїти _автоматичне тестування_. Тестування за сценарієм створюється аналогічно іншим блокам коду. Ми запускаємо наші функції з певними введеннями та перевіряємо їхню дію, щоб переконатися, що вони працюють відповідним чином. У міру зростання бази коду ми автоматизуватимемо тестування. Коли ми прописуємо тести поряд із функціями, то можемо перевірити працездатність всього модуля без необхідності щоразу запам'ятовувати, як використовувати ту чи іншу функцію.

У цьому навчальному посібнику ми використовуємо тестовий фреймворк Mocha з модулем Node.js `assert`. Давайте на практиці подивимося, як вони працюють разом.

Для початку створимо новий файл для зберігання коду тесту:

```bash
touch index.test.js
```

Тепер за допомогою текстового редактора відкрийте файл тестування. Можна використовувати `nano` як раніше:

```bash
nano index.test.js
```

У першому рядку текстового файлу ми завантажимо модуль TODO аналогічно до того, як ми робили в оболонці Node.js. Потім ми завантажимо модуль `assert`, щоб він був на момент створення тестів:&#x20;

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
const Todos = require('./index');
const assert = require('assert').strict;
```
{% endcode %}

Властивість `strict` ​​ модуля `assert` дозволить нам використовувати спеціальні тести еквівалентності, рекомендовані Node.js, які також підходять для перевірок надалі, оскільки відповідають за більшу кількість варіантів використання.

Перш ніж приступити до написання тестів, обговоримо, як Mocha організує наш код. Тестування з використанням Mocha, як правило, використовує такі шаблони:

{% code lineNumbers="true" %}
```javascript
describe([String with Test Group Name], function() {
    it([String with Test Name], function() {
        [Test Code]
    });
});
```
{% endcode %}

Зверніть увагу на дві ключові функції: `describe()` та `it()`. Функція `describe()` використовується для угруповання аналогічних тестів. Для Mocha не потрібно запускати тести, але їхнє угруповання спростить підтримку нашого коду тесту. Рекомендується групувати тести таким чином, щоб легше було оновлювати аналогічні разом.

`it()` містить код тесту. Саме тут ми могли б взаємодіяти з функціями нашого модуля та використовувати бібліотеку `assert`. Багато функцій `it()` можуть бути визначені функції `describe()`.

Мета цього розділу полягає у використанні Mocha та `assert` для автоматизації нашого ручного тесту. Ми робитимемо це поступово, почавши з блоку опису. Додайте до файлу наступне, після рядків модуля:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
});
```
{% endcode %}

За допомогою цього блоку коду ми створили угруповання для наших об'єднаних тестів. _Тести блоку_ перевіряють за однією функцією за раз. _Інтеграційні тести_ перевіряють, наскільки добре функції у модулях чи між ними працюють разом. Коли Mocha запускає наш тест, всі тести цього блоку опису будуть запущені в групі `інтеграційних тестів`.

Давайте додамо функцію `it()`, щоб розпочати тестування нашого коду модуля:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
    it("should be able to add and complete TODOs", function() {
    });
});
```
{% endcode %}

Зверніть увагу, на назву тесту. Для всіх, хто запустить наш тест, стане зрозуміло, що пройдено, а що — ні. Добре протестований додаток — це, як правило, добре задокументований додаток, і тести можуть бути ефективним способом документування.

Для першого тесту ми створимо новий об'єкт `Todos` і перевіримо, що в ньому немає елементів:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
    it("should be able to add and complete TODOs", function() {
        let todos = new Todos();
        assert.notStrictEqual(todos.list().length, 1);
    });
});
```
{% endcode %}

Перший новий рядок коду інстанціював новий об'єкт `Todos`, як ми робили в Node.js REPL або іншому модулі. У другому новому рядку ми використовували модуль `assert`.

З модуля `assert` ми використовуємо метод `notStrictEqual()`. Ця функція враховує два параметри: значення, яке необхідно протестувати (називається `фактичне` значення), та значення, яке ми очікуємо отримати (називається `очікуване` значення). Якщо ці обидва аргументи однакові, `notStrictEqual()` видає помилку про непроходження тесту.

Збережіть та закрийте `index.test.js`.

Базовий сценарій буде істинним, тому що довжина має бути `0`, що не дорівнює `1`. Давайте переконаємось у цьому, запустивши Mocha. Для цього нам потрібно буде модифікувати наш файл `package.json`. Відкрийте файл `package.json` у текстовому редакторі:

```bash
nano package.json
```

Тепер у властивості `scripts` змініть його наступним чином:

{% code title="todos/package.json" lineNumbers="true" %}
```javascript
...
"scripts": {
    "test": "mocha index.test.js"
},
...

```
{% endcode %}

Змінивши поведінку команди `test` командного рядка `npm`. Коли ми запустимо `npm test`, npm перевірить команду, яку ми тільки-но ввели в `package.json`. Він буде шукати бібліотеку Mocha в нашій папці `node_modules` і запустить команду `mocha` з нашим файлом тестування.

Збережіть та закрийте `package.json`.

З'ясуємо, що відбувається, коли ми запускаємо наш тест. У своєму терміналі введіть:

```bash
npm test
```

Команда видасть наступний вивід:

{% code lineNumbers="true" %}
```javascript
Output
> todos@1.0.0 test your_file_path/todos
> mocha index.test.js



integrated test
    ✓ should be able to add and complete TODOs


  1 passing (16ms)
```
{% endcode %}

Цей вивід спершу покаже нам, яка група тестів зараз запуститься. Для кожного окремого тесту групи тестовий сценарій є ступінчастим. Ми бачимо наше ім'я тесту так, як ми описали його функції `it()`. Галочка з лівого боку тестового сценарію вказує на те, що тест пройдено.

Внизу ми отримаємо резюме всіх наших тестів. У нашому випадку один тест було виконано та завершено протягом 16 мс (час залежить від комп'ютера).

Тестування розпочалося успішно. Проте поточний тестовий сценарій може допускати хибні позитивні результати. _Помилкові позитивні результати_ - це тестовий сценарій, коли тест пройдено тоді, коли цього не повинно було статись.

Тепер ми перевіряємо, що довжина масиву не дорівнює `1`. Давайте змінимо тест, щоб ця умова була істинною, коли не повинно. Додайте наступні рядки до `index.test.js`:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
    it("should be able to add and complete TODOs", function() {
        let todos = new Todos();
        todos.add("get up from bed");
        todos.add("make up bed");
        assert.notStrictEqual(todos.list().length, 1);
    });
});
```
{% endcode %}

Збережіть та закрийте файл.

Ми додали два елементи TODO. Давайте запустимо тест, щоб побачити, що станеться:

```bash
npm test
```

В результаті ви отримаєте наступний висновок:

{% code lineNumbers="true" %}
```javascript
Output
...
integrated test
    ✓ should be able to add and complete TODOs


  1 passing (8ms)
```
{% endcode %}

Він проходить згідно з очікуваннями, оскільки довжина більше 1. Однак він не досягає початкової мети проведення цього першого тесту. Перший тест мав би підтвердити, що ми починаємо з чистого стану. Більш досконалий тест підтвердить це у всіх випадках.

Давайте змінимо тест таким чином, що його успішне проходження буде можливим лише за повної відсутності TODO у пам'яті. Виконаэм такі зміни в `index.test.js`:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
    it("should be able to add and complete TODOs", function() {
        let todos = new Todos();
        todos.add("get up from bed");
        todos.add("make up bed");
        assert.strictEqual(todos.list().length, 0);
    });
});
```
{% endcode %}

Замінивши `notStrictEqual()`​ на `strictEqual()`​, функцію, яка перевіряє еквівалентність між фактичним та очікуваним аргументом.

Збережіть та закрийте файл, потім запустіть тест, щоб побачити, що станеться:

```bash
npm test
```

На цей раз вивід покаже помилку:

{% code lineNumbers="true" %}
```javascript
Output
...
  integration test
    1) should be able to add and complete TODOs


  0 passing (16ms)
  1 failing

  1) integration test
       should be able to add and complete TODOs:

      AssertionError [ERR_ASSERTION]: Input A expected to strictly equal input B:
+ expected - actual

- 2
+ 0
      + expected - actual

      -2
      +0

      at Context.<anonymous> (index.test.js:9:10)



npm ERR! Test failed.  See above for more details.
```
{% endcode %}

Цей текст стане в нагоді лише для налагодження причини непроходження тесту. Зверніть увагу, що оскільки тест не пройдено, на початку тестового сценарію не було галочки.

Резюме тесту знаходиться вже не внизу виводу, а одразу після нашого списку відображених тестових сценаріїв:

{% code lineNumbers="true" %}
```javascript
...
0 passing (29ms)
  1 failing
...
```
{% endcode %}

В решті висновку надано дані про непройдені тести. Спочатку ми бачимо, які тестові сценарії не пройдено:

{% code lineNumbers="true" %}
```javascript
...
1) integrated test
       should be able to add and complete TODOs:
...
```
{% endcode %}

Потім ми побачимо причину непроходження тесту:

{% code lineNumbers="true" %}
```javascript
...
      AssertionError [ERR_ASSERTION]: Input A expected to strictly equal input B:
+ expected - actual

- 2
+ 0
      + expected - actual

      -2
      +0

      at Context.<anonymous> (index.test.js:9:10)
...
```
{% endcode %}

Видається `AssertionError`, коли не виконується `strictEqual()`. Ми бачимо, що очікуване значення 0 відрізняється від `фактичного` значення 2.

Потім ми побачимо рядок у файлі тестування, де код не виконується. І тут це рядок 10.

Тепер ми переконалися, що наш тест не буде пройдений, якщо ми чекатимемо некоректні результати. Давайте змінимо тестовий сценарій назад на правильне значення:

```bash
nano index.test.js
```

Потім виберіть рядки `todos.add`, щоб ваш код виглядав так:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function () {
    it("should be able to add and complete TODOs", function () {
        let todos = new Todos();
        assert.strictEqual(todos.list().length, 0);
    });
});
```
{% endcode %}

Збережіть та закрийте файл.

Запустіть його ще раз, щоб переконатися у проходженні без жодних хибних позитивних результатів:

```bash
npm test
```

Вивід виглядатиме так:

{% code lineNumbers="true" %}
```javascript
Output
...
integration test
    ✓ should be able to add and complete TODOs


  1 passing (15ms)
```
{% endcode %}

Тепер ми значно покращили відмовостійкість нашого тесту. Давайте перейдемо до нашого інтеграційного тесту. Наступний крок - додати новий елемент TODO до `index.test.js`:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
    it("should be able to add and complete TODOs", function() {
        let todos = new Todos();
        assert.strictEqual(todos.list().length, 0);

        todos.add("run code");
        assert.strictEqual(todos.list().length, 1);
        assert.deepStrictEqual(todos.list(), [{title: "run code", completed: false}]);
    });
});
```
{% endcode %}

Після використання функції `add()` ми підтверджуємо, що ми маємо один елемент TODO, керований нашим об'єктом `todos`, при цьому ми будемо використовувати `strictEqual()`. Наш наступний тест підтверджує дані в `todos` за допомогою `deepStrictEqual()`. Функція `deepStrictEqual()` рекурсивно перевіряє, чи мають наші передбачувані та реальні об'єкти одні й самі властивості. У цьому випадку перевіряється, чи містять обидва очікувані масиву об'єкт JavaScript. Потім перевіряється, чи мають ці об'єкти JavaScript однакові властивості, тобто обидві властивості `title` — це `run code`, а обидві властивості `completed` — `false`.

Потім виконаємо тести, що залишилися, використовуючи ці два тести рівності, додавши наступні виділені рядки:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("integration test", function() {
    it("should be able to add and complete TODOs", function() {
        let todos = new Todos();
        assert.strictEqual(todos.list().length, 0);

        todos.add("run code");
        assert.strictEqual(todos.list().length, 1);
        assert.deepStrictEqual(todos.list(), [{title: "run code", completed: false}]);

        todos.add("test everything");
        assert.strictEqual(todos.list().length, 2);
        assert.deepStrictEqual(todos.list(),
            [
                { title: "run code", completed: false },
                { title: "test everything", completed: false }
            ]
        );

        todos.complete("run code");
        assert.deepStrictEqual(todos.list(),
            [
                { title: "run code", completed: true },
                { title: "test everything", completed: false }
            ]
    );
  });
});
```
{% endcode %}

Збережіть та закрийте файл.

Тепер додамо новий тест для цієї нової функції. Нам потрібно переконатися, що якщо ми викликаємо команду complete об'єкту `Todos`, в якому немає елементів, буде повернена помилка.

Поверніться до `index.test.js` :

```bash
nano index.test.js
```

В кінці файлу додайте наступний код:

{% code title="todos/index.test.js" lineNumbers="true" %}
```javascript
...
describe("complete()", function() {
    it("should fail if there are no TODOs", function() {
        let todos = new Todos();
        const expectedError = new Error("You have no TODOs stored. Why don't you add one first?");

        assert.throws(() => {
            todos.complete("doesn't exist");
        }, expectedError);
    });
});
```
{% endcode %}

Знову використовуємо `describe()` та `it()`. Цей тест починається із створення нового об'єкта `todos`. Потім ми визначаємо помилку, яку очікуємо отримати під час виклику функції `complete()`.

Далі використовуємо функцію `throws()` модуля `assert`. Ця функція була створена для перевірки помилок, які видаються у коді. Перший аргумент - це функція, що містить код, який видає помилку. Другий аргумент – це помилка, яку ми очікуємо отримати.

Знову запустіть тест за допомогою `npm test` у своєму терміналі і ви побачите наступний вивід:

{% code lineNumbers="true" %}
```javascript
Output
...
integrated test
    ✓ should be able to add and complete TODOs

  complete()
    ✓ should fail if there are no TODOs


  2 passing (25ms)
```
{% endcode %}

Цей вивід підтверджує переваги автоматизованого тестування за допомогою Mocha та `assert`. Оскільки наші тести виконуються скриптами, щоразу, коли ми запускаємо `npm test`, ми перевіряємо, що всі тести успішно пройдені. Нам не потрібно вручну перевіряти, чи працює інший код. Ми знаємо, що працює, оскільки наш тест успішно пройдено.

Таким чином за допомогою цих тестів ми перевірили результати синхронного коду. Подивимося, як можна адаптувати ці методи тестування до роботи з асинхронним кодом.

### Тести з використанням Sinon

У проектах, у яких частини програм складно тестувати такі як Ajax-запити, таймери, дати, доступ до інших функцій браузера, бази даних, доступ до мережі або файлу. На допомогу прийде бібліотека тестування Sinon.

Все це важко перевірити, тому що ви не можете контролювати їх у коді. Якщо ви використовуєте Ajax, вам потрібний сервер для відповіді на запит, щоб тести пройшли успішно. Якщо ви використовуєте `setTimeout`, ваш тест повинен буде чекати. З базами даних або мережами це те саме – вам потрібна база даних з правильними даними або мережевий сервер.

### Що таке Sinon?

Простіше кажучи, Sinon дозволяє вам замінити складні частини ваших тестів на щось, що робить тестування простим.

При тестуванні фрагмента коду ви не хочете, щоб на нього вплинуло щось поза тестом. Якщо щось зовнішнє впливає на тест, тест стає складнішим.

Якщо ви хочете перевірити код, що робить Ajax-дзвінок, як ви можете це зробити? Вам потрібно запустити сервер і переконатися, що він дає точну відповідь, необхідну для вашого тесту. Він складний у налаштуванні та ускладнює написання та запуск модульних тестів.

### Як працює Sinon?

Sinon допомагає усунути складність у тестах, дозволяючи легко створювати так звані тест-двійники.

Тест-двійники, як випливає з назви, замінюють фрагменти коду, що використовуються у тестах.  Як ми бачимо зприкладу Ajax, замість налаштування сервера ми замінили б виклик Ajax на `test-double`.

### Все, що потрібно знати про Sinon.JS

Наступні сторінки містять всю документацію **API Sinon.JS**, а також коротке введення в концепції, які реалізує Sinon.

* [**General setup**](https://sinonjs.org/releases/v14/general-setup)
* [**Fakes**](https://sinonjs.org/releases/v14/fakes)
* [**Spies**](https://sinonjs.org/releases/v14/spies)
* [**Stubs**](https://sinonjs.org/releases/v14/stubs)
* [**Mocks**](https://sinonjs.org/releases/v14/mocks)
* [**Spy calls**](https://sinonjs.org/releases/v14/spy-call)
* [**Promises**](https://sinonjs.org/releases/v14/promises)
* [**Fake timers**](https://sinonjs.org/releases/v14/fake-timers)
* [**Fake XHR and server**](https://sinonjs.org/releases/v14/fake-xhr-and-server)
* [**JSON-P**](https://sinonjs.org/releases/v14/json-p)
* [**Assertions**](https://sinonjs.org/releases/v14/assertions)
* [**Matchers**](https://sinonjs.org/releases/v14/matchers)
* [**Sandboxes**](https://sinonjs.org/releases/v14/sandbox)
* [**Utils**](https://sinonjs.org/releases/v14/utils)

### **Get Started**

Установка за допомогою `npm`

```bash
npm install sinon
```

Системи побудови вузлів

{% code lineNumbers="true" %}
```javascript
import * as sinon from 'sinon'
```
{% endcode %}

Наступна функція приймає функцію як аргумент і повертає нову функцію. Ви можете викликати отриману функцію скільки завгодно разів, але оригінальна функція буде викликана лише один раз:

{% code lineNumbers="true" %}
```javascript
export function once(fn) {
   let returnValue,
       called = false;
   return function () {
       if (!called) {
           called = true;
           returnValue = fn.apply(this, arguments);
       }
       return returnValue;
   };
}
```
{% endcode %}

### Підробки **(Фейки)**

Перевірити цю функцію можна досить елегантно за допомогою [**test fake**](https://sinonjs.org/releases/v14/fakes)**:**

{% code lineNumbers="true" %}
```javascript
it("calls the original function only once", () => {
   let callback = sinon.fake();
   let proxy = once(callback);
   proxy();
   proxy();

   assert.equal(callback.callCount, 1);
});
```
{% endcode %}

Ми також дбаємо про це значення та аргументи:

```javascript
it("calls original function with right this and args", function () {
  var callback = sinon.fake();
  var proxy = once(callback);
  var obj = {};

  proxy.call(obj, 1, 2, 3);

  assert(callback.calledOn(obj));
  assert(callback.calle
```

### Поведінка

Функція, яку повертає `once`, повинна повертати те, що повертає оригінальна функція. Щоб перевірити це, ми створюємо фейк з поведінкою:

```javascript
it("returns the return value from the original function", function () {
  var callback = sinon.fake.returns(42);
  var proxy = once(callback);

  assert.equals(proxy(), 42);
});
```

Зручно, ми можемо запитувати фейки щодо їхньої `callCount`, отриманих аргументів тощо.

### **"Фейковий" сервер**

Попередній приклад показує, наскільки гнучким є цей API. Якщо це виглядає надто трудомістким, можливо, вам до вподоби буде **** фейковий сервер:

{% code lineNumbers="true" %}
```javascript
var server;

before(function () {
  server = sinon.fakeServer.create();
});
after(function () {
  server.restore();
});

it("calls callback with deserialized data", function () {
  var callback = sinon.fake();
  getTodos(42, callback);

  // This is part of the FakeXMLHttpRequest API
  server.requests[0].respond(
    200,
    { "Content-Type": "application/json" },
    JSON.stringify([{ id: 1, text: "Provide examples", done: true }])
  );

  assert(callback.calledOnce);
});
```
{% endcode %}

Інтеграція тестового фреймворку, як правило, може ще більше зменшити шаблонність.

### **Sinon для Todos**

Перевіримо кількість викликів для методів `add/list` і дані які утворюються в результаті**:**

{% code lineNumbers="true" %}
```javascript
describe('sinon test ', () => {

   it("calls the original function", function () {
       let spyAdd = sinon.spy(todos, "add");
       let spyList = sinon.spy(todos, "list");
       todos.add('apple pie')
       assert.equal(spyAdd.calledOnce, true);
       assert.equal(todos.list()[0].id, 4);
       assert.equal(todos.list()[0].status, 'active');
       assert.equal(todos.list()[0].title, 'apple pie');
       assert.equal(spyList.callCount, 3);

   });

   it("todos test add/list function", () => {

       const fake = sinon.fake.returns({id: 5, title: 'apple pie', status: 'active'});
       todos.add('apple pie')

       assert.equal(todos.list()[0].id, fake().id);
       assert.equal(todos.list()[0].status, fake().status);
       assert.equal(todos.list()[0].title, fake().title);
   });

})
```
{% endcode %}

Результат роботи програми**:**

<figure><img src="https://lh5.googleusercontent.com/k009Li4g746wO3lsuzY6uawwT5ceT2QZWYTqcxYbuUz2T-dXvi7H1EAOZ2vQ1IC7f71EK82R9ZTTT_8XYB2UELpE1KFnoCViBpzOJKqoqGdArgRsqMyrqldYEfZtuCkzVHnoBNqFm6WWTbIELGmnYeUmqMjbhgHzD7EzKWc9DmY2Ib2NM5IDF2RFtA" alt=""><figcaption></figcaption></figure>

Sinon у тестуванні дає нам спосіб відстеження дзвінків, зроблених у методі, щоб ми могли перевірити, що він працює, як очікувалося. Ми використовуємо Sinon , щоб перевірити, чи назвав метод або не викликаний, скільки разів його викликали, з якими аргументами і значення, яке він повертається при виклику.
