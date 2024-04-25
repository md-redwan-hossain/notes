```bash
npm install -g browser-sync
browser-sync start --proxy "localhost:80" --files "**/*.php"
```
In php.ini,
`display_errors=On`

### debugging

`echo` can take n number of params.
`print_r` is for arrays.
`var_dump` gives more data.


### string interpolation

```php
<?php
    $msg = "Hello";
    echo "{$msg} User";
?>
```

### const

```php
<?php
    define(HOST,"localhost");
    echo(HOST);
?>
```

### array

Simple:

```php
<?php
    $arr_1 = [1,2,3];
    $arr_2 array(1,2,3);

    echo ($arr_1[0]);
?>
```

Associative:

```php
<?php
    $arr = [
        "name" => "Redwan",
        "age"  => 26,
    ];

    echo ($arr["age"]);
    $json_val = json_encode($arr);
    json_decode($json_val);
?>
```
`empty()` checks if an array is empty or not.