# Home work 3

1\) Створити класс калькулятор який буде обраховівати базові операції додавання/віднімання/ділення/множення/відсоток

```javascript
class Calculator {
    result
    constructor() {
        
    }
    calculation(num1, num2, op){
        
     //   ...
        return result
    }
}
```

2\) Додайте до попередньої задачі тести, які перевірятимуть:

* [ ] складання двох чисел з операціею 'sum';
* [ ] віднімання двох чисел з операціею 'minus'
* [ ] множення двох чисел з операціею 'multiple'
* [ ] множення двох чисел з операціею 'division'

тести повинні працювати для вводу будь яких символив та чисел (текст/дробні числа/0/ символи !"№;%:?\*())б перевіряти назви операцій.

3\) Розробити тесты на функцію maskify, яка змінює всі символи, крім останніх чотирьох, на '#'.

<pre data-title="Приклад робот функції" data-line-numbers><code><strong>"4556364607935616" --> "############5616"
</strong>     "64607935616" -->      "#######5616"
               "1" -->                "1"
                "" -->                 ""

// "What was the name of your first pet?"
"Skippy" --> "##ippy"

"Nananananananananananananananana Batman!"
-->
"####################################man!"</code></pre>

```javascript
// return masked string
const symbolQuantity = 4

function maskify(cc) {
  const arrCC = cc.split("");
  
  return arrCC.length>symbolQuantity?
    arrCC.map((el,i, arr)=> ((arr.length-symbolQuantity)>i)?el='#':el).join("")
  :cc;
}

```

4\)  Розробити тесты на алгоритм [Нарцистичне](https://en.wikipedia.org/wiki/Narcissistic\_number) число — це додатне число, яке є сумою власних цифр, кожна з яких зведена до ступеня кількості цифр у даній основі.

Наприклад, візьмемо 153 (3 цифри), що є нарцистичним:

```
 1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153
```

і 1652 (4 цифри), що не є:

```
 1^4 + 6^4 + 5^4 + 2^4 = 1 + 1296 + 625 + 16 = 1938
```

#### Умови:

Ваш код має повертати true або false залежно від того, чи є дане число нарцисичним числом за основою 10.

Перевірка помилок на текстові рядки чи інші недійсні вхідні дані не потрібна, лише дійсні позитивні цілі числа, відмінні від нуля, будуть передані у функцію.

#### Приклад алгоритму.

```javascript
export function narcissistic(value) {
  const nums = Array.from(String(value), Number);
    const narcissisticVal = nums
    .reduce((accumulator, currentValue, index, array) => accumulator + Math.pow(+currentValue, array.length) ,0)
  return narcissisticVal===value;
  }
```

5\) Напишіть функцію, яка приймає рядок дужок і визначає, чи правильний порядок дужок. Він має повернути true, якщо рядок дійсний, і false, якщо він недійсний.

Усі вхідні рядки будуть непорожніми та складатимуться лише з дужок, дужок і фігурних дужок: ()\[]{}.

Що вважається дійсним? Рядок фігурних дужок вважається дійсним, якщо всі дужки відповідають правильній дужці.

#### Приклад <a href="#examples" id="examples"></a>

```
"(){}[]"   =>  True
"([{}])"   =>  True
"(}"       =>  False
"[(])"     =>  False
"[({})](]" =>  False
```

#### Тести

```javascript
import * as assert from 'assert';

function doTest (braces, expected) {
    const actual = validBraces(braces);
    assert.strictEqual(actual, expected, `for braces:\n"${braces}"\n`);
}

describe("Tests suite", function() {
    it("sample tests", function() {
        doTest("()))", false);
        doTest("()", true);
        doTest("[]", true);
        doTest("{}", true);
        doTest("(){}[]", true);
        doTest("([{}])", true);
        doTest("(}", false);
        doTest("[(])", false);
        doTest("({})[({})]", true);
        doTest("(})", false);
        doTest("(({{[[]]}}))", true);
        doTest("{}({})[]", true);
        doTest(")(}{][", false);
        doTest("())({}}{()][][", false);
        doTest("(((({{", false);
        doTest("}}]]))}])", false);
    });
});

```
