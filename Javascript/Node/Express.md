# Express
[Express](https://www.npmjs.com/package/express) — фреймворк для упрощения запуска web-сервера
Установите библиотеку **Express**:
```
$ npm i --save express
```
Простейшее web-приложение на основе **Express*:
```javascript
const app = require('express')() // скобки в конце нужны для вызова конструктора

// обработчик get-запроса
app.get('/', function (req, res) {
  res.send('Hello World')
})

// прослушивание порта 3000 
app.listen(3000)
```