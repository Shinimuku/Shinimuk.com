<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat App</title>
</head>
<body>
    <ul id="messages"></ul>
    <form id="form" action="">
        <input id="input" autocomplete="off" /><button>Send</button>
    </form>
    <script src="/socket.io/socket.io.js"></script>
    <script>
        const socket = io();

        const form = document.getElementById('form');
        const input = document.getElementById('input');
        const messagesList = document.getElementById('messages');

        form.addEventListener('submit', function(e) {
            e.preventDefault();
            if (input.value) {
                socket.emit('chat message', input.value);
                input.value = '';
            }
        });

        socket.on('chat message', function(msg) {
            const item = document.createElement('li');
            item.textContent = msg.text;
            messagesList.appendChild(item);
        });

        socket.on('allMessages', function(messages) {
            messages.forEach(function(msg) {
                const item = document.createElement('li');
                item.textContent = msg.text;
                messagesList.appendChild(item);
            });
        });
    </script>
</body>
</html>
