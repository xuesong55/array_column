# array_column() for PHP

This simple library provides functionality for [`array_column()`](http://php.net/array_column)
to versions of PHP earlier than 5.5. It mimics the functionality of the built-in
function in every way.

PHP数组值循环处理成下标，并且可以指定一维取值

## 例子

```
array array_column(array $input, mixed $columnKey[, mixed $indexKey])
```

Given a multi-dimensional array of data, `array_column()` returns the values
from a single column of the input array, identified by the `$columnKey`.
Optionally, you may provide an `$indexKey` to index the values in the returned
array by the values from the `$indexKey` column in the input array.

For example, using the following array of data, we tell `array_column()` to
return an array of just the last names, indexed by their record IDs.

``` php
<?php
$records = array(
    array(
        'id' => 2135,
        'first_name' => 'John',
        'last_name' => 'Doe'
    ),
    array(
        'id' => 3245,
        'first_name' => 'Sally',
        'last_name' => 'Smith'
    ),
    array(
        'id' => 5342,
        'first_name' => 'Jane',
        'last_name' => 'Jones'
    ),
    array(
        'id' => 5623,
        'first_name' => 'Peter',
        'last_name' => 'Doe'
    )
);

$lastNames = array_column( $records, 'last_name', 'id' );
```

If we call `print_r()` on `$lastNames`, you'll see a resulting array that looks
a bit like this:

``` text
Array
(
    [2135] => Doe
    [3245] => Smith
    [5342] => Jones
    [5623] => Doe
)
```


## 安装

The easiest way to install this library is to use [Composer](https://getcomposer.org/):

```
php composer.phar require ramsey/array_column
```

Then, when you run `composer install`, everything will fall magically into place,
and the `array_column()` function will be available to your project, as long as
you are including Composer's autoloader.

_However, you do not need Composer to use this library._

This library has no dependencies and should work on older versions of PHP.
Download the code and include `src/array_column.php` in your project, and all
should work fine.

When you are ready to run your project on PHP 5.5, everything should
continue to run well without conflicts, even if this library remains included
in your project.
