---
layout: post
title:  "PHP Callable Type"
---

PHP supports [callbacks/callables](https://www.php.net/manual/en/language.types.callable.php). Normally callbacks are implemented as references to functions. In PHP it is possible to do callbacks from a string variable also.

For example:
```php
function my_hello_function(){
    echo 'Hello';
}

$my_function_name = 'my_hello_function';
```

Value in `$my_function_name` can be used for a function call. For this PHP provides `call_user_func()` built-in function.

```php
// Calls my_hello_function()
call_user_func($my_function_name);
```

Any arguments passed after the first argument to `call_user_func`, will be passed as arguments to callable function.

To call a method in an object:
```php
$obj = new MyClass();
call_user_func([$obj, 'myCallbackMethod'], arg1, arg2,...);
```

`call_user_func` can also be used to call built-in functions.

```php
$arr = ['1', '2', '3'];

echo $arr[rand(0, 2)];
// is the same as
echo $arr[call_user_func('rand', 0, 2)];
```

This gives possibilities to alter the flow of the program, to provide dynamic flow based on data. This feature is also used by many PHP libraries to add hooks and dynamic functionality.

[Read the docs for more examples](https://www.php.net/manual/en/function.call-user-func.php).
