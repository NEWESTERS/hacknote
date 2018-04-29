# Socket.io
[Socket.io](https://socket.io) - библиотека для обеспечения двунаправленной связи между клиентами в реальном времени по протоколу **Websocket**.

Установка библиотеки **Socket.io**:
```
$ npm i --save socket.io
```
## Пример
В данном примере будет реализован простой онлайн-чат. Для реализации будет также задействована библиотека [Express](Express.md).

Создадим два файла: *index.js* (backend) и *index.html* (frontend).
### Backend
Сначала подключим необходимые библиотеки:
```javascript
const app = require('express')()
const http = require('http').Server(app)
// Инициализируем модуль Socket.io на основе http сервера
const io = require('socket.io')(http)
```
Заставим модуль `io` слушать входящие сокеты:
```javascript
// Установка соединения по протоколу Websocket
io.on('connection', function(socket){
	// Обработчик получения сокетом сообщения
	socket.on('chat message', function(msg){
		// Рассылка сообщения подключенным клиентам
    	io.emit('chat message', msg)
  	})
})
```
Добавим обработчик **get**-запроса для отправки страницы с чатом:
```javascript
app.get('/', function(req, res){
	// Отправляем клиенту страницу с чатом
	res.sendFile(__dirname + '/index.html')
})
```
Заставим сервер слушать порт 3000:
```javascript
http.listen(3000, function(){
  console.log('Сервер запущен на порте 3000')
})
```
### Frontend
На странице реализуем список для сообщений и форму для отправки сообщения:
```html
<ul id="messages"></ul>
<form action="">
  <input id="m" autocomplete="off" /><button>Send</button>
</form>
```
Подключим **Socket.io** и реализуем чат:
```html
<script src="/socket.io/socket.io.js"></script>
<script src="https://code.jquery.com/jquery-1.11.1.js"></script>
<script>
  	$(function () {
  		// Инициализация Socket.io
        var socket = io();

        $('form').submit(function(){
        	// Рассылка сообщения подключенным клиентам при отправке формы
          	socket.emit('chat message', $('#m').val(), 'Я');
         	$('#m').val('');
          	return false;
        });
		// Обработчик получения сокетом сообщения
        socket.on('chat message', function(msg, sender){
          	$('#messages').append($('<li>').text(sender + ': ' + msg));
        });
    });
</script>
```

