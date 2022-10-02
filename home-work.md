# Home Work

1\) Оформіть цей код у вигляді CommonJS. Експортуйте всі функції, крім допоміжних.

{% code lineNumbers="true" %}
```javascript
function square(num) {
	return num ** 2;
}

function cube(num) {
	return num ** 3;
}

function avg(arr) {
	return sum(arr, 1) / arr.length;
}

function digitsSum(num) {
	return sum(String(num).split(''));
}

// допоміжних функція
function sum(arr) {
	let res = 0;
	for (let elem of arr) {
		res += +elem;
	}
	return res;
}
```
{% endcode %}

2\) За допомогою модуля з попереднього завдання знайдіть суму квадрата та куба числа 3. Імпортуйте для цього лише необхідні функції.

3\) Створити запити для створення/оновлення/видалення.читання (GET, POST, PUT, DELETE )\
структура \
Наприклаc

{% tabs %}
{% tab title="indnex.js" %}
```
// Some code
```
{% endtab %}

{% tab title="user.js" %}
```
// Some code
```
{% endtab %}
{% endtabs %}

```javascript
const requestListener = function (req, res) {
    res.setHeader("Content-Type", "application/json");
    switch (req.url) {
        case "/books":
            res.writeHead(200);
            res.end(books);
            break
        case "/authors":
            res.writeHead(200);
            res.end(authors);
            break
        default:
            res.writeHead(404);
            res.end(JSON.stringify({error:"Resource not found"}));
    }
}
```
