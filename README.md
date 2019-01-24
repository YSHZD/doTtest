# doTtest
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <title></title>
</head>
<script id="nametmpl" type="text/x-dot-template">
    <h1>
        {{=it.name}} 2019
    </h1>
    <ul>
        {{~it.arr:value:index}}
        <li>{{=index}}------{{=value}}</li>
        {{~}}
    </ul>
    <ol>
        {{for( var key in it.objs){}}
        <li>{{=key}}-----{{=it.objs[key]}}</li>
        {{}}}
    </ol>
    <ol>
        {{~it.arr2:value:index}}
        <li>
            {{? value<60}}不及格 
            {{?? value<=80}}良好 
            {{??}}优秀{{?}} 
        </li>
        {{~}}
    </ol>
    <div>{{!it.html}}</div>
</script>

<body>
    <div id="name"></div>
</body>
<script src="doT.js"></script>
<script>
    var data = {
        name: 'YSH',
        arr: ['a', 'b', 'c'],
        objs: {
            "name": "Jake",
            "age": 31,
            "interests": ["basketball", "hockey", "photography"],
            "contact": {
                "email": "jake@xyz.com",
                "phone": "999999999"
            }
        },
        arr2: [58, 60, 80, 90, 50],
        "html": "<div style='background: #f00; height: 30px; line-height: 30px;'>html元素</div>"
    };
    var nameIn = doT.template(document.getElementById("nametmpl").text);
    document.getElementById("name").innerHTML = nameIn(data);
</script>

</html>
