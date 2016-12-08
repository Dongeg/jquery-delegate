# jquery-delegate
jquery-delegate不兼容iso
解决方法，给委托对象添加css属性

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
