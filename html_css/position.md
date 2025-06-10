```html

<!doctype html>
<html>

<head>
    <meta chasrset="utf-8">
    <title>position</title>
    <style>
        * {
            margin : 0;
            padding : 0;
        }

        #parent{
            position: relative;
            width: 500px;
            height: 300px;
            border: solid 8px black;
            margin : 50px 0 0 50px;
        }

        #box1 ,#box2, #box3{
            width: 80px;
            height: 80px;
        }

        #box1{
            background-color: red;
        }

        #box2{
            background-color: green;
            position: absolute;
            top: 20px;
            left: 30px;
        }

        #box3{
            background-color: yellow;
        }
    </style>
</head>

<body>
    <div id="parent">
        <div id="box1">A</div>
        <div id="box2">B</B></div>
        <div id="box3">C</div>

    </div>

</body>

</html>
