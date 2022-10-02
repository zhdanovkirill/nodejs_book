# Home Work 1

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


{% swagger src="../.gitbook/assets/swaggerHW1.yaml" path="/user" method="get" %}
[swaggerHW1.yaml](../.gitbook/assets/swaggerHW1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/swaggerHW1.yaml" path="/user" method="post" %}
[swaggerHW1.yaml](../.gitbook/assets/swaggerHW1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/swaggerHW1.yaml" path="/user/createWithArray" method="post" %}
[swaggerHW1.yaml](../.gitbook/assets/swaggerHW1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/swaggerHW1.yaml" path="/user/{username}" method="get" %}
[swaggerHW1.yaml](../.gitbook/assets/swaggerHW1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/swaggerHW1.yaml" path="/user/{username}" method="put" %}
[swaggerHW1.yaml](../.gitbook/assets/swaggerHW1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/swaggerHW1.yaml" path="/user/{username}" method="delete" %}
[swaggerHW1.yaml](../.gitbook/assets/swaggerHW1.yaml)
{% endswagger %}
