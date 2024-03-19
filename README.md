# Shinimuk.com
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сайт для переговоров</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }
        #chat-box {
            width: 80%;
            margin: 20px auto;
            border: 1px solid #ccc;
            padding: 10px;
            background-color: #fff;
            overflow-y: scroll;
            height: 300px;
        }
        #input-box {
            width: 80%;
            margin: 0 auto;
            text-align: center;
        }
        #message-input {
            width: 70%;
            padding: 5px;
        }
        #send-button {
            width: 20%;
            padding: 5px;
            background-color: #333;
            color: #fff;
            border: none;
            cursor: pointer;
        }
        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 20px;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Переговоры</h1>
    </header>
    <div id="chat-box"></div>
    <div id="input-box">
        <input type="text" id="message-input" placeholder="Введите сообщение...">
        <button id="send-button">Отправить</button>
    </div>
    <footer>
        <p>&copy; 2024 Сайт для переговоров. Все права защищены.</p>
    </footer>
    <script>
        const chatBox = document.getElementById('chat-box');
        const messageInput = document.getElementById('message-input');
        const sendButton = document.getElementById('send-button');

        function sendMessage() {
            const message = messageInput.value.trim();
            if (message !== '') {
                const messageElement = document.createElement('div');
                messageElement.textContent = message;
                chatBox.appendChild(messageElement);
                chatBox.scrollTop = chatBox.scrollHeight;
                messageInput.value = '';
            }
        }

        sendButton.addEventListener('click', sendMessage);
        messageInput.addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        });
    </script>
</body>
</html>
