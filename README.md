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
        }
        .chat-container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #f9f9f9;
        }
        #message-list {
            list-style-type: none;
            padding: 0;
            margin: 0;
            overflow-y: auto;
            max-height: 300px;
        }
        #message-list li {
            margin-bottom: 10px;
            padding: 10px;
            border-radius: 5px;
            background-color: #fff;
        }
        #message-list li:nth-child(odd) {
            background-color: #f2f2f2;
        }
        #message-input {
            width: calc(100% - 20px);
            margin-top: 10px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        #submit-button {
            width: 100%;
            margin-top: 10px;
            padding: 10px;
            background-color: #333;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <ul id="message-list">
            <!-- Здесь будут отображаться сообщения -->
        </ul>
        <input type="text" id="message-input" placeholder="Введите ваше сообщение...">
        <button id="submit-button">Отправить</button>
    </div>

    <script>
        // JavaScript код для отправки и отображения сообщений
    </script>
</body>
</html>
