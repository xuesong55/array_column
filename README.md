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
		'id' => 1000, 'name' => '百度',  
		'web' => array( 'http://www.baidu.com/','http://baike.baidu.com/' ) 
	),
	array( 'id' => 1001, 'name' => '腾讯', 
		'web' => array( 'http://www.qq.com/' ,'http://v.qq.com/')
	),
	array( 
		'id' => 1002, 'name' => '阿里',  
		'web' => array( 'http://www.taobao.com/'  , 'http://www.tmall.com/')
	)
);

```
测试
``` text
// 输出指定键
print_r(  array_column( $records,  'name'  , 'id' ) )  ;
Array
(
    [1000] => 百度
    [1001] => 腾讯
    [1002] => 阿里
)

//输出所有
print_r(  array_column( $records,  null  , 'id' ) )  ;
Array
(
    [1000] => Array
        (
            [id] => 1000
            [name] => 百度
            [web] => Array
                (
                    [0] => http://www.baidu.com/
                    [1] => http://baike.baidu.com/
                )

        )

    [1001] => Array
        (
            [id] => 1001
            [name] => 腾讯
            [web] => Array
                (
                    [0] => http://www.qq.com/
                    [1] => http://v.qq.com/
                )

        )

    [1002] => Array
        (
            [id] => 1002
            [name] => 阿里
            [web] => Array
                (
                    [0] => http://www.taobao.com/
                    [1] => http://www.tmall.com/
                )

        )

)



```
