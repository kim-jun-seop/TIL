```html
<!doctype html>
<html>

<head>
    <meta chasrset="utf-8">
    <title>회원가입 폼</title>
    <style>
        ul{
           list-style-type: none; 
        }

        *{
            margin:0;
            padding:0;
        }

        h3{
            margin:20px 0 0 50px;
        }

        #mem_form{
            width: 500px;
            margin: 10px 0 0 50px;
            font-family: "돋움";
            font-size: 12px;
            color:#444444;
            padding-top: 5px;
            padding-bottom: 10px;
            border-top: solid 1px #cccccc;
            border-bottom: solid 1px #cccccc;
        }

        .cols li{
            display: inline-block;
            margin-top: 5px;
        }
        
        .cols li.col1{
            width: 100px;
            text-align: right;
        }

        .cols li.col2{
            width: 350px;
        }

        .cols li.col2 input.hp{
            width: 35px;
        }
        
        #intro{
            vertical-align: top;
        }
        
    </style>
</head>

<body>
    <h3>가입 양식</h3>
    <form action="">
        <ul id="mem_form">
            <li>
                <ul class="cols">
                    <li class="col1">아이디 : </li>
                    <li class="col2"><input type="text"></li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">비밀번호 : </li>
                    <li class="col2"><input type="password"></li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">비밀번호 확인 : </li>
                    <li class="col2"><input type="password"></li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">이름 : </li>
                    <li class="col2"><input type="text"></li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">성별 : </li>
                    <li class="col2"><input type="radio" name="sex" checked>여성
                    &nbsp;&nbsp; <input type="radio" name="sex">남성</li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">휴대전화 : </li>
                    <li class="col2">
                        <select name="" id="">
                            <option value="">010</option>
                            <option value="">011</option>
                            <option value="">017</option>
                        </select> - 
                        <input type="text" class="hp"> - <input type="text" class="hp">
                    </li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">이메일 : </li>
                    <li class="col2"><input id="email1" type="text">@
                        <select name="" id="email2">
                            <option value="">선택</option>
                            <option value="">naver.com</option>
                            <option value="">daum.net</option>
                            <option value="">google.com</option>
                        </select>
                    </li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">취미 : </li>
                    <li class="col2">
                        <input type="checkbox" name="hobby1">음악감상
                        <input type="checkbox" name="hobby2">독서
                        <input type="checkbox" name="hobby2">등산
                    </li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1" id="intro">자기소개 : </li>
                    <li class="col2">
                        <textarea cols="35" rows="5"></textarea>
                    </li>
                </ul>
            </li>
            <li>
                <ul class="cols">
                    <li class="col1">파일첨부 : </li>
                    <li class="col2"><input type="file">* 2MB까지 가능</li>
                </ul>
            </li>
        </ul>
    </form>
</body>

</html>
