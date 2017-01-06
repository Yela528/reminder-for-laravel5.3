# reminder-for-laravel5.3

Inspired by [laracasts flash](https://github.com/laracasts/flash)

### 下载

使用 Composer

    composer require g9zz/reminder

在 `config/app.php` 文件里加入

```php
G9zz\Reminder\ReminderServiceProvider::class,
```

也可以在 `config/app.php` 里加入

```php
'Reminder'  => G9zz\Reminder\ReminderFacade::class,
```


> 建议加上面这条,因为这样你可以使用 `reminder()` 方法

### 依赖

jQuery [toast](https://github.com/CodeSeven/toastr), 需要加入`css`文件和`js`文件

- [//cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.js](//cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.js)
- [//cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.css](//cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.css)

### 基本使用

必须在页面里添加 `{!! Reminder::message() !!}` 

以下几种方式都可以使用!

* Reminder::info('foo', 'bar', []);

* Reminder::success('foo', 'bar', []);

* Reminder::warning('foo', 'bar', []);

* Reminder::error('foo', 'bar', []);

* reminder()->info('foo', 'bar', []);

### 如果类似这种`Reminder::error('foo', 'bar', []);` 用不了,可以使用`reminder()->error()`方式


```php
<?php

Route::get('/', function () {
    Reminder::success('Hi! this is Reminder', 'Hello', ["positionClass" => "toast-bottom-right"]);

    return view('welcome');
});
```

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Laravel</title>
        <link rel="stylesheet" href="http://cdn.bootcss.com/toastr.js/latest/css/toastr.min.css">
    </head>
    <body>
        <div class="container">
            <div class="content">
                <div class="title">Laravel 5</div>
            </div>
        </div>

        <script src="http://cdn.bootcss.com/jquery/1.11.3/jquery.min.js"></script>
        <script src="http://cdn.bootcss.com/toastr.js/latest/js/toastr.min.js"></script>
        {!! reminder()->message() !!}
    </body>
</html>
```

![](http://ww3.sinaimg.cn/mw690/baa3278fgw1ey7ky56nbgj20n60fuaav.jpg)

### Options

如果要生成一些配置文件,可以执行以下命令

    php artisan vendor:publish



You can see [toastr's documentation](http://codeseven.github.io/toastr/demo.html) to custom your need.

### MIT
