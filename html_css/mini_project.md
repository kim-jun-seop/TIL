```html
<!doctype html>
<html>

<head>
    <meta chasrset="utf-8">
    <title>로그인</title>
    <style>
        *{
            margin: 0px;
            padding: 0px;
        }

        body{
            font-family: "돋움";
            font-size: 12px;
            color:#444444;
        }

        ul{
            list-style-type: none;
        }
     
        #login_title{
            width: 585px;
            padding: 10px;
            margin: 50px;
            font-size: 20px;
            border: solid 5px #e6e2d7;
        }


        #login_box{
            width: 610px;
            height: 283px;
            margin: 20px 0 0 50px;
            border: solid 2px #cccccc;
            border-radius: 20px;
        }

        #member_login{
            margin: 30px 0 0 50px;
        }

        #login{
            margin: 20px 10 0 50px;
        }

        #left{
            display: inline-block;
            margin-left: 30px;
        }

        #right{
            display: inline-block;
            margin-left: 50px;
        }

        #id_pass, #login_btn{
            display: inline-block;
            vertical-align: top;
        }

        #id_pass span{
            display: inline-block;
            width: 50px;
        }

        #id_pass input{
            width: 130px;
            height: 20px;
        }

        #pass{
            margin-top: 3px;
        }

        #auto_login{
            margin: 15px 0 0 25px;
        }

        #join_find{
            margin: 25px 0 0 20px;
        }
        
        #join_find li{
            padding: 2px;
            list-style-type: disc;
        }
    </style>
</head>

<body>
<h2 id="login_title">로그인</h2>
<div id="login_box">
    <img id="member_login" src="img/login_img.gif">
    <ul id="login">
        <li id="left">
            <img id="key" src="img/login_img02.gif">
        </li>

        <li id="right">
            <ul id="input_button">
                <li id="id_pass">
                    <ul>
                        <li>
                            <span>아이디</span>
                            <input type="text">
                        </li>
                        <li id="pass">
                            <span>비밀번호</span>
                            <input type="password">
                        </li>
                    </ul>
                </li>
                <li id="login_btn">
                    <img src="img/btn_login.gif">
                </li>
            </ul>

            <div id="auto_login">
                <input type="checkbox">자동로그인
            </div>

            <ul id="join_find">
                <li>아직 회원이 아니세요?</li>
                <li>아이디 또는 비밀번호를 잊으셨나요?</li>
            </ul>
        </li>
    </ul>
</div>
</body>

</html>
