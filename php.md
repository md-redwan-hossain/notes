- [env setup](#env-setup)
- [debugging](#debugging)
- [const](#const)
- [loop](#loop)
- [function](#function)
- [string](#string)
- [array](#array)

### env setup

```bash
npm install -g browser-sync
browser-sync start --proxy "localhost:80" --files "**/*.php"
```
In php.ini,
`display_errors=On`

### debugging

- `echo` can take n number of params.
- `print_r` is for arrays.
- `var_dump` gives more data.


### const

```php
<?php
    define(HOST,"localhost");
    echo(HOST);
    const ANOTHER_CONSTANT = 1;
?>
```

### loop

```php
<?php

$arr = ["a","b","c"];

foreach( $arr as $item){
echo($item);
}

// Accessing Index
foreach($arr as $i => $elem){
    echo($i);
    echo($elem);
}

// Associative array
foreach($arr as $key => $value){
    echo($arr[$key]);
    echo($value);
}

?>

### Null
- The null is a special type in PHP. It indicates the absence of a value for a variable.
- To check if a variable is null or not, you use the is_null() function.
- When you use the `unset()` function to unset a variable, the variable is also null. 
```
### type hint
- type hints ensure that PHP will check the type of a value at the call time and throw a TypeError if there is a mismatch.
- Basic types: `bool` `int` `float` `string` `null` `true` `false` `void` `object` `resource` `array` `mixed` `never`
- Union type: `int | string`
- Nullable type: `?string`
- To enable strict typing, you can use the `declare(strict_types=1);` directive at the beginning of the file.
- PHP enables the strict mode on a per-file basis.
- When you include code from another file, PHP uses the mode of the caller.

### function

- To access a global variable inside a function, use `global $var_name;`
- Arrow functions can also capture variables from the surrounding scope, unlike traditional closures, arrow functions do not need to be explicitly defined variables from scope.
- Use the ... operator to define a variadic function. Only the last parameter can be variadic.
```php
<?php

// regular function
function concat_two_string(string $str1, string $str2) : strng
{
    return $str1 . $str2;
}

// Variadic function
function sum(int ...$numbers): int
{
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $total;
}

// Named Arguments
function find(string $needle, string $haystack)
{
    return strpos($haystack, $needle);
}  

find (
    $needle : 'awesome',
    $haystack : 'PHP is awesome!'
);

// Anonymous function/closure
$add = function($a, $b) {
   return $a + $b;
};

// Arrow function
$addArrow = fn($a, $b) => $a + $b;
?>
```


```php
<?php
$factor = 10;

// Closure
$multiplier = function($n) use ($factor) {
   return $n * $factor;
};

// Arrow function
$multiplierArrow = fn($n) => $n * $factor;
?>
```


### string


- `htmlspecialchars(string,flags,character-set,double_encode)`: Convert the predefined characters to HTML entities.




```php
<?php
    $msg = "Hello";

    // interpolation
    echo "{$msg} User";

    // concatenation
    echo $msg . "User";
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

- `in_array(search, array, type)`: Returns TRUE if the value is found in the array, or FALSE otherwise.

- `array_push(array, value1, value2, ...)`: Returns the new number of elements in the array.

- `array_pop(array)`: Returns the last value of array. If array is empty, or is not an array, NULL will be returned.

- `array_filter(array, callbackfunction, flag)`: Returns the filtered array, key is preserved. To re-structure the indices, use `array_values`

- `array_map(myfunction, array1, array2, array3, ...)`: Returns an array containing the values of array1, after applying the user-made function to each onel.

- `count(array, mode)`: returns the number of elements in an array. `mode` is Optional Possible values:
  - 0 - Default. Does not count all elements of multidimensional arrays
  - 1 - Counts the array recursively (counts all the elements of multidimensional arrays)

- `empty()` checks if an array is empty or not.

- `range(low, high, step)`: creates an array containing a range of elements.  `step` is optional. It Specifies the increment used in the range. Default is 1


```php
<?php
    // array_filter
    $arr = array_filter(range(1, 20), fn($item) => $item % 2 == 0);

    // array_map
    $modified_arr = array_map(fn($item) => "Number {$item}", $arr);

    // array_reduce
    $sum = array_reduce($arr, fn($carry, $item) => $carry + $item);
?>
```

## Interface
- Specifies which methods and properties a class must implement.
- It is strongly recommended that developers use the same parameter names as the interface being implemented.
- To implement an interface, the `implements` operator is used.
- Classes may implement more than one interface if desired by separating each interface with a comma.
- Interfaces can be extended like classes using the `extends` operator.
- It's possible for interfaces to have constants. Interface constants work exactly like class constants.

### Enum
```php
<?php
enum Suit
{
    case Hearts;
    case Diamonds;
    case Clubs;
    case Spades;
}
?>
```
