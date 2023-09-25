<!doctype html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Shop</title>
</head>
<body>
    <div id="main">
        <h1>Онлайн магазин</h1>
        <img src="/Shop_online.jpg">
        <p>Lorem ispum dolor sit amet</p>
        <button id="buy">Купить</button>
    </div>
    <form id="form">
        <h1>Оформление покупки</h1>
        <input type="text" placeholder="Имя" id="user_name">
        <input type="text" placeholder="Email" id="user_email">
        <input type="text" placeholder="Телефон" id="user_phone">
        <div id="error"></div>
        <button id="order">Оформить</button>
    </form>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <script>
        let tg = window.Telegram.WebApp;
        let buy = document.getElementById("buy");
        let order = document.getElementById("order");
        tg.expand();
        buy.addEventListener('click', () => {
            document.getElementById("main").style.display = "none";
            document.getElementById("form").style.display = "block";
            document.getElementById("user_name").value = tg.initDataUnsafe.user.first_name  +  " " + tg.initDataUnsafe.user.last_name;
        });
        order.addEventListener("click", () => {
            document.getElementById("error").innerText = '';
            let name = document.getElementById("user_name").value;
            let email = document.getElementById("user_email").value;
            let phone = document.getElementById("user_phone").value;
            if(name.length  < 5) {
                document.getElementById("error").innerText = 'Ошибка в имени';
                return;
            }
            if(email.length  < 5) {
                document.getElementById("error").innerText = 'Ошибка в email';
                return;
            }
            if(phone.length  < 5) {
                document.getElementById("error").innerText = 'Ошибка в phone';
                return;
            }
            let data = {
                name: name,
                email: email,
                phone: phone
            }
            tg.sendData(JSON.stringify(data));

            tg.close();
        });
    </script>
</body>
</html>
