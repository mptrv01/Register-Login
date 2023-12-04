Описание на "myform"

1 Предварително добавени:
  -- express: Популярен за Node.js,улеснява създаването на уеб приложения.
  -- mysql: Библиотека за взаимодействие с MySQL база данни от Node.js
  -- express-session: Middleware за сесии в Express, която позволява запазването на данни на сесията между HTTP заявките.
  -- package.json: JSON файл, който се използва в Node.js проекти и съдържа метаданни относно проекта. Този файл играе ключова роля в управлението на зависимостите, настройките на средата, изпълнимите скриптове и други настройки.
  -- node_modules: тук  се съхраняват всички файлове на зависимостите, включително техните изходни кодове, конфигурационни файлове и други ресурси..

2 Структура: 
  --node_modules
  --login.html
  --failLog.html
  --register.html
  --failReg.html
  --server.js
  --package-lock.json
  --package.json
  --REDME.md
 
      2.1 failLog.html и failReg.html:
        1. Целта на тези две html страници е да информират потребителя, че неговият опит да се регистрира или да влезе във вече съществуващият си акунт е неуспешен. Важно е да орбележим че и двата файла имат идентична стуктура.
        2.Добавени са стилове от Bootstrap чрез:
         <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"> 

      2.2 regiter.html и login.html
         1.Тук използваме елементът <form> който създава форма, която ще използваме  за събиране на информация от потребителите
         2.Добавяме и атрибута action, който  указва URL, към който ще бъде изпратена информацията от формата, когато тя бъде изпратена. 
         3.Използваме и атрибута method, за да зададем  HTTP метода, използван за изпращане на информацията от формата към указания URL

      2.3 server.js
 1. Импоръираме модулите: 

 const express = require('express');                            
 const cookieParser = require("cookie-parser");
 const sessions = require('express-session');
 const http = require('http');
 var parseUrl = require('body-parser');
 const app = express();

 express: Фреймуърк за уеб разработка за Node.js.
 cookie-parser: Модул за обработка на HTTP бисквитки (cookies).
 express-session: Модул за сесии в Express.js.
 http: Вграден модул за работа с HTTP протокола.
 body-parser: Модул за обработка на тяло на заявката.
 mysql: MySQL драйвер за Node.js.

 2. Създава се връзка с MySQL база данни, като се използват хост, потребителско име, парола и име на базата данни.
 var con = mysql.createConnection({
    host: "localhost",
    user: "root", 
    password: "123456789", 
    database: "myform"
});
3. Пътят '/' е за основната страница и изпраща HTML формата за регистрация (register.html).
app.get('/', (req, res) => {
    res.sendFile(__dirname + '/register.html');
});
4. Пътят '/register' обработва POST заявките за регистрация. Проверява дали вече съществува потребител със същите данни и ако не, извършва регистрация и установява сесия за потребителя.

app.post('/register', encodeUrl, (req, res) => {
    // ...
});
5. Пътят '/login' връща HTML формата за вход.

app.get("/login", (req, res)=>{
    res.sendFile(__dirname + "/login.html");
});
6. Пътят '/dashboard' обработва POST заявките за вход и проверява дали потребителят съществува в базата данни.

app.post("/dashboard", encodeUrl, (req, res)=>{
    // ...
});

 7. Създаване на сървър и слушане на определен порт:
 app.listen(4000, ()=>{
    console.log("Server running on port 4000");
});
