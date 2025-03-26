# 1
code html et css eid said
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عيد مبارك</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to right, #ffcc00, #ff6699);
            font-family: 'Arial', sans-serif;
        }
        .container {
            text-align: center;
            color: white;
        }
        h1 {
            font-size: 50px;
            animation: fadeIn 2s ease-in-out;
        }
        p {
            font-size: 20px;
            animation: slideUp 2s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        .button {
            display: inline-block;
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 18px;
            color: white;
            background: #ff3366;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }
        .button:hover {
            background: #cc0033;
        }
        .message-box {
            margin-top: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        textarea {
            width: 80%;
            height: 100px;
            padding: 10px;
            border-radius: 5px;
            border: none;
            font-size: 16px;
            resize: none;
        }
        .private-messages {
            margin-top: 20px;
            padding: 10px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 5px;
            color: white;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>تمنى لصفوة عيد سعيد</h1>
        <p>كل عام وأنتم بخير</p>
        <div class="message-box">
            <textarea id="greetingMessage" placeholder="اكتب تهنئتك هنا..."></textarea>
            <button class="button" onclick="saveMessage()">إرسال التهنئة</button>
        </div>
        <div class="private-messages" id="messages"></div>
    </div>
    <script>
        function saveMessage() {
            const message = document.getElementById("greetingMessage").value;
            if (message.trim() !== "") {
                let messages = JSON.parse(localStorage.getItem("eidMessages")) || [];
                messages.push(message);
                localStorage.setItem("eidMessages", JSON.stringify(messages));
                document.getElementById("greetingMessage").value = "";
                alert("تم إرسال التهنئة!");
                displayMessages();
            }
        }

        function displayMessages() {
            const messagesDiv = document.getElementById("messages");
            let messages = JSON.parse(localStorage.getItem("eidMessages")) || [];
            if (messages.length > 0) {
                messagesDiv.innerHTML = "<h3>تهاني خاصة:</h3>" + messages.map(msg => `<p>${msg}</p>`).join(" ");
                messagesDiv.style.display = "block";
            }
        }

        window.onload = displayMessages;
    </script>
</body>
</html>
