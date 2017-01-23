##ArrayHelper

The ArrayHelper class contains useful array helpers.

##Contents

<div id="contents" markdown="1">

[accessible()](#accessible)
[exists()](#exists)
[get()](#get)
[first()](#first)
[last()](#last)
[has()](#has)
[where()](#where)
[only()](#only)
[forget()](#forget)

</div>

###accessible() {#accessible}

Checks whether a value is an array or object
that implements the <a href="http://php.net/manual/en/class.arrayaccess.php" target="_blank">ArrayAccess</a> interface.

    ArrayHelper::accessible(array|\ArrayAccess $value);

**Parameters**  
`$value` = An array or object that implements the ArrayAccess interface.

**Return Values**  
If the `$value` is an array or object that implements the ArrayAccess interface, this method returns `true` and `false` otherwise.

####Examples

    // With associative array
    $user = ['name' => 'Merlin'];
    
    ArrayHelper::accessible($user); // true
    
    // With ArrayObject instance
    $user = new ArrayObject(['name' => 'Merlin']);
    
    ArrayHelper::accessible($user); // true

###exists() {#exists}

Checks whether a key is present in an array.

    ArrayHelper::exists(array|\ArrayAccess $array, string|int $key);

**Parameters**  
`$array` = The array to be checked.  
`$key` = The key, according to which the array is to be searched.

**Return Values**  
Returns `true` if the key is present and `false` otherwise.

####Examples

    $user = ['name' => 'Merlin'];
    
    ArrayHelper::exists($user, 'name'); // true

###get() {#get}

Retrieves a value from a deeply nested array.

    ArrayHelper::get(array|\ArrayAccess $array, string|int $key [, mixed $default = null]);

**Parameters**  
`$array` = The array to be checked.  
`$key`= The key, according to which the array is to be searched.  
`$default` = The default value, which will be returned if the specific key is not found.

**Return Values**  
Returns the array value, if it exists in the array, or the default value.

####Examples

    $user = [
        'name' => 'Merlin',
        'country' => [
            'name' => 'DE',
        ],
    ];
    
    // Return a value from an array
    ArrayHelper::get($user, 'name')) // 'Merlin'
    
    // Return a nested array value
    ArrayHelper::get($countries, 'country.name') // 'DE'

    // Return the default value, if the specific key is not found
    ArrayHelper::get($countries, 'country.flag', 'Not available')) // 'Not available'

###first() {#first}

Returns the first element of an array passing a given truth test.

    ArrayHelper::first(array|\ArrayAccess $array [, callable|null  $callback = null [, mixed $default = null]]);
 
**Parameters**  
`$array` = The array to be checked.  
`$callback` = The callback function to use.  
`default` = The default value, which will be returned if no value passes the truth test.

**Return Values**  
Returns the first array element that passed the truth test, or the default value.

####Examples

    $values = [100, 200, 300];
    
    // Return the first array element
    ArrayHelper::first($values); // 100

    // Return the first array element, passing a given truth test
    ArrayHelper::first($values, function ($item) {
        return $item >= 200;
    }); // 200

    // Return the default value, if the truth test fails
    ArrayHelper::first($values, function ($item) {
        return $item > 500;
    }, 'Failed'); // 'Failed'

###last() {#last}

Returns the last element of an array passing a given truth test.

    ArrayHelper::last(array|\ArrayAccess $array [, callable|null  $callback = null [, mixed $default = null]]);

**Parameters**  
`$array` = The array to be checked.  
`$callback` = The callback function to use.  
`default` = The default value, which will be returned if no value passes the truth test.

**Return Values**  
Returns the last array element that passed the truth test, or the default value.

####Examples

    $values = [100, 200, 300];
    
    // Return the last array element
    ArrayHelper::last($values); // 300

    // Return the last array element, passing a given truth test
    $last = ArrayHelper::last($values, function ($item) {
        return $item < 300;
    }); // 200

###has() {#has}

Checks whether a given element or elements exists in an array.

    ArrayHelper::has(array|\ArrayAccess $array, string|array $key);

**Parameters**  
`$array` = The array to be checked.  
`$key` = The key, according to which the array is to be searched.

**Return Values**  
Returns `true`, if the array element(s) exists and `false` otherwise.

####Examples

    $user = ['name' => 'Merlin'];
    
    ArrayHelper::has($user, 'name'); // true
    ArrayHelper::has($user, 'country.name'); // false

###where() {#where}

Filters the array using the given Closure.

    ArrayHelper:where(array|\ArrayAccess $array, callable $callback);

**Parameters**  
`$array` = The array to be checked.  
`$callback` = The callback function to use.

**Return Values**  
Returns the result of the callback function.

####Examples

    $array = ['first' => 100, 2 => 200, 3 => 300];
    
    ArrayHelper::where($array, function ($value, $key) {
        return is_numeric($key);
    }); // [2 => 200, 3 => 300]
    
###only() {#only}

Returns only the specified key/value pairs from the given array.

    ArrayHelper::only(array|\ArrayAccess $array, array|string $key);

**Parameters**  
`$array` = The array to be checked.  
`$key` = The key(s) to return from the array.

**Return Values**  
Returns the specified key/value pairs from the given array.

####Examples

    $user = [
        'user' => 'Merlin',
        'email' => 'my@email.com',
        'country' => [
            'name' => 'DE',
        ],
    ];
    
    // Return the filtered array by a single array key
    ArrayHelper::only($user, 'user'); // [user => 'Merlin']

    // Return the filtered array by multiple array keys
    ArrayHelper::only($user, ['user', 'country']); // [user => 'Merlin', country => [name => 'DE']]

###forget() {#forget}

Removes a given key/value pair from a deeply nested array.

    ArrayHelper::forget(array|\ArrayAccess &$array, array|string $keys);

**Parameters**  
`$array` = The array to be checked.  
`$key` = The key(s) to be removed from the array.

**Return Values**  
Returns the array without the defined key/value pair.

####Examples

    $user = [
            'user' => 'Merlin',
            'email' => 'my@email.com',
            'country' => [
                'name' => 'DE',
            ],
        ];
    
    // Remove a single array element
    ArrayHelper::forget($user, 'country'); // [user => 'Merlin', email => '']
    
    // Remove multiple array elements
    ArrayHelper::forget($user, ['email', 'country']); // [user => 'Merlin']
