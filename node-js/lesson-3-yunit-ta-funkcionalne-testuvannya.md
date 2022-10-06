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

Дивись [тут](https://www.digitalocean.com/community/tutorials/how-to-test-a-node-js-module-with-mocha-and-assert-ru).
