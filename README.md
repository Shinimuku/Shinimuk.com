<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat Room</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="chat-container">
        <ul id="messages"></ul>
        <form id="form" action="">
            <input id="input" autocomplete="off" /><button>Send</button>
        </form>
    </div>

    <script src="/socket.io/socket.io.js"></script>
    <script src="script.js"></script>
</body>
</html>
body, html {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f0f0f0;
}

.chat-container {
    max-width: 800px;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #fff;
}

#messages {
    list-style-type: none;
    padding: 0;
}

#messages li {
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 5px;
    background-color: #f2f2f2;
}

#messages li:nth-child(odd) {
    background-color: #e6e6e6;
}

form {
    margin-top: 20px;
}

form input {
    padding: 10px;
    width: calc(100% - 70px);
}

form button {
    padding: 10px 20px;
    background-color: #333;
    color: #fff;
    border: none;
    cursor: pointer;
}
const socket = io();

const form = document.querySelector('form');
const input = document.querySelector('#input');
const messages = document.querySelector('#messages');

form.addEventListener('submit', function(event) {
    event.preventDefault();
    if (input.value) {
        socket.emit('chat message', input.value);
        input.value = '';
    }
});

socket.on('chat message', function(msg) {
    const item = document.createElement('li');
    item.textContent = msg;
    messages.appendChild(item);
});
const express = require('express');
const app = express();
const http = require('http').Server(app);
const io = require('socket.io')(http);

app.use(express.static('public'));

io.on('connection', function(socket) {
    console.log('a user connected');

    socket.on('disconnect', function() {
        console.log('user disconnected');
    });

    socket.on('chat message', function(msg) {
        io.emit('chat message', msg);
    });
});

const PORT = process.env.PORT || 3000;
http.listen(PORT, function() {
    console.log(`listening on *:${PORT}`);
});
