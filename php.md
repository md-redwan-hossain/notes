- [env setup](#env-setup)
- [debugging](#debugging)
- [string](#string)
- [const](#const)
- [array](#array)

### env setup

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


### string



```php
<?php
    $msg = "Hello";

    // interpolation
    echo "{$msg} User";

    // concatenation
    echo $msg . "User";
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

array methods:

- `empty()` checks if an array is empty or not.
- `in_array(search, array, type)`: Returns TRUE if the value is found in the array, or FALSE otherwise.
- `array_push(array, value1, value2, ...)`: Returns the new number of elements in the array.
- `array_pop(array)`: Returns the last value of array. If array is empty, or is not an array, NULL will be returned.
- `array_filter(array, callbackfunction, flag)`: Returns the filtered array, key is preserved.
- `array_map(myfunction, array1, array2, array3, ...)`: Returns an array containing the values of array1, after applying the user-made function to each onel.
