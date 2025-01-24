# Работа с Синхронным и Асинхронным кодом в JavaScript

![image](https://github.com/user-attachments/assets/3c2643ad-8f4a-4e76-903b-def22f25cbe8)

## Введение
JavaScript — это язык, основанный на модели событий и обладающий асинхронной природой. В данном файле рассмотрены следующие концепции:
- Синхронный и асинхронный код.
- Работа с `Promise`.
- Использование `async/await`.
- Обработка ошибок с помощью `try/catch`.
- Работа с запросами: `fetch` и `request`.

---

## Синхронный код
Синхронный код выполняется последовательно, строка за строкой. Пока текущая задача не завершена, последующий код не начнет выполнение.

### Пример синхронного кода:
```javascript
console.log('Начало');
console.log('Процесс...');
console.log('Конец');
```
**Результат вывода:**
```
Начало
Процесс...
Конец
```

### Недостатки:
- Если операция занимает много времени, это может заблокировать выполнение программы.

---

## Асинхронный код
Асинхронный код позволяет программе выполнять другие задачи, пока ожидаются долгие операции, такие как запросы к серверу.

### Пример асинхронного кода:
```javascript
console.log('Начало');

setTimeout(() => {
  console.log('Процесс...');
}, 2000);

console.log('Конец');
```
**Результат вывода:**
```
Начало
Конец
Процесс... (через 2 секунды)
```

Асинхронные функции выполняются через **event loop**, позволяя избежать блокировок.

---


![image](https://github.com/user-attachments/assets/0c5834b2-fce1-4742-98da-07f0d214eafb)


## Promise (Обещание)
Объект `Promise` представляет значение, которое будет доступно в будущем. Он используется для обработки асинхронных операций.

![image](https://github.com/user-attachments/assets/e2938fbd-e1d8-4345-b95c-6861b39beb2b)

### Создание Promise:
```javascript
const myPromise = new Promise((resolve, reject) => {
  const success = true; // Условие выполнения

  if (success) {
    resolve('Операция выполнена успешно!');
  } else {
    reject('Ошибка выполнения.');
  }
});
```

### Работа с Promise:
```javascript
myPromise
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

---

![image](https://github.com/user-attachments/assets/5e417ab5-9a5d-44f9-900f-b05e4dcbf44f)

## Async/Await
`async` и `await` делают асинхронный код более читабельным и похожим на синхронный.

### Пример использования:
```javascript
async function fetchData() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Ошибка:', error);
  }
}

fetchData();
```

### Объяснение:
1. `async` делает функцию асинхронной.
2. `await` приостанавливает выполнение кода, пока Promise не выполнится.

---

![image](https://github.com/user-attachments/assets/2a58648d-6d3a-48e0-b9e0-a051422875f2)

## Try/Catch
`try/catch` используется для обработки ошибок в JavaScript. Он особенно полезен при работе с асинхронным кодом.

### Пример обработки ошибок:
```javascript
try {
  const result = riskyFunction();
  console.log(result);
} catch (error) {
  console.error('Произошла ошибка:', error);
} finally {
  console.log('Блок finally выполнен.');
}
```

---

![image](https://github.com/user-attachments/assets/b5ea84e0-930a-4fe3-abbc-08b9a6dc1e1c)

## Fetch и Request
Методы `fetch` и `request` используются для выполнения HTTP-запросов.

### Fetch API:
```javascript
fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'GET',
})
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error('Ошибка запроса:', error));
```

![image](https://github.com/user-attachments/assets/ed9c3946-3f06-4f9a-8823-bd2c5f2f3426)

### Request (Node.js):
Для работы с запросами в Node.js используется модуль `request` (устарел, рекомендуется использовать `axios`).


![image](https://github.com/user-attachments/assets/8fc8c459-2866-404b-a22c-80f20ff6a70c)


#### Пример с Axios:
```javascript
const axios = require('axios');

axios.get('https://jsonplaceholder.typicode.com/posts')
  .then((response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error('Ошибка запроса:', error);
  });
```

---

## Заключение
В этом файле рассмотрены основные концепции работы с синхронным и асинхронным кодом в JavaScript. Эти знания помогут эффективно работать с асинхронными операциями, обрабатывать ошибки и взаимодействовать с веб-сервисами.

