```html

<!doctype html>
<html>

<head>
    <meta chasrset="utf-8">
    <title>position</title>
    <style>
        *{
            margin:0;
            padding: 0;
        }
        li{
            list-style-type:none;
        }
        #header{
            width: 800px;
            height: 95px;
            background-color: #2d3a4b;
            position: relative;
        }
        #logo{
            position: absolute;
            top: 30px;
            left: 30px;
        }
        #top_menu{
            position: absolute;
            top: 20px;
            left: 632px;
            font-size: 11px;
            color: white;
        }
        #main_menu{
            position: absolute;
            top: 55px;
            left: 220px;
            font-size: 16px;
            color: white;
        }
        #main_menu li{
            display: inline;
            margin-left: 30px;
        }
        #content ul{
            margin-top: 20px;
        }
        #content li{
            display: inline;
            margin-left: 60px;
        }
        #footer{
            width: 800px;
            height: 90px;
            margin-top: 20px;
            background-color: #f1f1f1;
        }
        #footer img{
            margin: 10px 0 0 60px;
        }
    </style>
</head>
<body>
   <div id = "header">
        <div id="logo"><img src="logo.png" alt=""></div>
        <div id="top_menu">HOME | NOTICE | LOGIN | JOIN</div>
        <ul id="main_menu">
            <li>COMPANY</li>
            <li>PRODUCT</li>
            <li>CUSTOMER</li>
            <li>SERVICE</li>
            <li>RECRUIT</li>
        </ul>
   </div>

   <div id = "content">
    <img src = "main_img.png" alt = "">
    <ul>
        <li><img src="banner1.png" alt=""></li>
        <li><img src="banner2.png" alt=""></li>
    </ul>
   </div>
   <div id="footer">
    <img src="address.png" alt="">
   </div>  
</body>
</html>
