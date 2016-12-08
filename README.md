# jquery-delegate
jquery-delegate不兼容iso
解决方法，给委托对象添加css属性






delegate() 方法为指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数。

使用 delegate() 方法的事件处理程序适用于当前或未来的元素（比如由脚本创建的新元素）。

```js
$('body').delegate('.cart_select','click',function() {
    var id =  this.id;
    $.post('{:url('user/cancle_select_collection')}' ,'id=' + id, function (data) {
        if(data.id == 'null'){
            $('.cart_select').removeClass('cart_select').addClass('cart_no_select');
        }else {
            $('#'+data.id).removeClass('cart_select').addClass('cart_no_select');
            $('#'+'all').removeClass('cart_select').addClass('cart_no_select');
        }
    }, 'json');
});

```
```css
.cart_select{
cursor: pointer;
}
```
example
```html
<html>
<head>
<script type="text/javascript" src="/jquery/jquery.js"></script>
<script type="text/javascript">
$(document).ready(function(){
  $("div").delegate("p","click",function(){
    $(this).slideToggle();
  });
  $("button").click(function(){
    $("<p>这是一个新段落。</p>").insertAfter("button");
  });
});
</script>
</head>
<body>
<div style="background-color:yellow">
<p>这是一个段落。</p>
<p>请点击任意一个 p 元素，它会消失。包括本段落。</p>
<button>在本按钮后面插入一个新的 p 元素</button>
</div>
<p><b>注释：</b>通过使用 delegate() 方法，而不是 live()，只有 div 元素中的 p 元素会受到影响。</p>
</body>
</html>
```
