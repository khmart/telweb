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
        <img src="Shop_online.jpg">
        <p>Lorem ispum dolor sit amet</p>
        <button id="buy">Купить</button>
    </div>
    <form id="form">
        <input type="text" placeholder="Имя" id="user_name">
        <input type="text" placeholder="Email" id="user_email">
        <input type="text" placeholder="Телефон" id="user_phone">
        <button id="order">Оформить</button>
    </form>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <script>
        let tg = window.Telegram.WebApp;
        let buy = document.getElementById("buy");
        let order = document.getElementById("order");
        buy.addEventListener('click', () => {
            document.getElementById("main").style.display = "none";
            document.getElementById("form").style.display = "block";
            document.getElementById("user_name").value = tg.initDataUnsafe.user.first_name  +  " " + tg.initDataUnsafe.user.last_name;
        });
        order.addEventListener("click", () => {
            tg.close();
        });
    </script>
</body>
</html>
