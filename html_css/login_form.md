
```html
<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <title>로그인 폼</title>
    <style>
        ul{
            list-style-type: none;
        }

        *{
            padding:0;
            margin:0;
        }

        body{
            font-family: "맑은 고딕","돋움";
            font-size: 12px;
            color:#444444;
        }

        #login_box{
            width:220px;
            height:120px;
            border:solid 1px #bbbbbb;
            border-radius: 15px;
            margin:10px 0 0 10px;
            padding:10px 0 0 15px;
        }

        h2{
            font-family: "Arial";
            margin-bottom: 10px;
        }

        #login_box input{
            width:100px;
            height:18px;
        }

        #id_pass, #login_btn{
            display:inline-block;
            vertical-align: top;
        }

        #id_pass span{
            display: inline-block;
            width: 20px;
        }

        #pass{
            margin-top: 3px;
        }

        #login_btn button{
            margin-left: 5px;
            padding: 12px;
            border-radius: 5px;
        }

        #btns{
            margin: 12px 0 0 0;
            text-decoration: underline;
        }

        #btns li{
            margin-left: 10px;
            display: inline;
        }
    </style>
</head>

<body>
    <form action="">
        <div id="login_box">
            <h2>Member Login</h2>
            <ul id="input_button">
                <li id="id_pass">
                    <ul>
                        <li>
                            <span>ID</span>
                            <input type="text">
                        </li>
                        <li id="pass">
                            <span>PW</span>
                            <input type="password">
                        </li>
                    </ul>
                </li>
                <li id="login_btn">
                    <button>로그인</button>
                </li>
            </ul>
            <ul id="btns">
                <li>회원가입</li>
                <li>아이디/비밀번호 찾기</li>
            </ul>
        </div>
    </form>
</body>

</html>
