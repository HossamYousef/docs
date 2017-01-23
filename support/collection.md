##Collection

The Collection class extends the (SPL) <a target="_blank" href="http://php.net/manual/en/class.arrayiterator.php">ArrayIterator</a>.  
This iterator allows to unset and modify values and keys while iterating over Arrays and Objects.

##Contents

<div id="contents" markdown="1">

[Instantiate](#instantiate)
[set()](#set)
[get()](#get)
[has()](#has)
[all()](#all)
[first()](#first)
[last()](#last)
[keys()](#keys)
[count()](#count)
[remove()](#remove)
[replace()](#replace)
[clear()](#clear)
[isEmpty()](#is-empty)
[each()](#each)
[filter()](#filter)
[map()](#map)
[merge()](#merge)
[toJson()](#to-json)
[__toString()](#to-string)

</div>

###Instantiate {#instantiate}

Creates a new `Collection` instance.

    new Avoxx\Support\Collection([array $data = []]);

**Parameters**  
`$data` = The collection data.

**Return Values**  
No value is returned.

####Examples

    //@todo: Include example

###set() {#set}

Sets a new collection item.
    
    $collection->set(string $key, mixed $value);

**Parameters**  
`$key` = The collection item key.  
`$value` = The collection item value.

**Return Values**  
No value is returned.

####Examples

    //@todo: Include example

###get() {#get}

Gets an item from the collection.

    $collection->get(string $key [, mixed $default = null]);

**Parameters**  
`$key` = The collection item key.  
`$default` = The default value.

**Return Values**  
The collection item data or the value of `$default`, if the collection item does not exists.

####Examples

    //@todo: Include example

###has() {#has}

Checks whether the collection has a specific item defined or not.

    $collection->has(string $key);

**Parameters**  
`$key` = Name of the collection key being checked for.

**Return Values**  
`true` if the key exists, otherwise `false`.

####Examples

    //@todo: Include example

###all() {#all}

Returns all collection data.

    $collection->all();

**Parameters**  
This method has no parameters.

**Return Values**  
All collection data, or an empty array.

####Examples

    //@todo: Include example

###first() {#first}

Returns the first collection item.

    $collection->first([mixed $default = null]);

**Parameters**  
`$default` = The default value.

**Return Values**  
The first collection item data or the value of `$default`, if the collection item does not exists.

####Examples

    //@todo: Include example

###last() {#last}

Returns the last collection item.

    $collection->last([mixed $default = null]);

**Parameters**  
`$default` = The default value.

**Return Values**
The last collection item data or the value of `$default`, if the collection item does not exists.

####Examples

    //@todo: Include example

###keys() {#keys}

Returns all collection data keys.

    $collection->keys();

To obtain an array output, simply use the `all()` method.

    $collection->keys()->all();
    
**Parameters**  
This method has no parameters.

**Return Values**  
A new instance of `Collection` with all data keys.

####Examples

    //@todo: Include example

###count() {#count}

Counts all data in the collection.

    $collection->count();

**Parameters**  
This method has no parameters.

**Return Values**  
Returns the number of data in the collection.

####Examples

    //@todo: Include example

###remove() {#remove}

Removes an item from the collection.

    $collection->remove(string $key);

**Parameters**  
`$key` = The key of the item.

**Return Values**  
No value is returned.

####Examples

    //@todo: Include example

###replace() {#replace}

Replaces collection data. 

    $collection->replace(array $data);

>**NOTE**  
The data array will be added, if it does not exists in collection. 

**Parameters**  
`$data` = The data array.

**Return Values**  
No value is returned.

####Examples

    //@todo: Include example

###clear() {#clear}

Removes all items from the collection.

    $collection->clear();
    
 **Parameters**  
 This method has no parameters.   

**Return Values**  
No value is returned.

####Examples

    //@todo: Include example

###isEmpty() {#is-empty}

Checks whether the collection is empty or not.

    $collection->isEmpty();

 **Parameters**  
 This method has no parameters.
 
 **Return Values**  
 `true` if the collection is empty, otherwise `false`.

####Examples

    //@todo: Include example

###each() {#each}

Executes a callback over each collection item.

    $collection->each(callable $callback);

**Parameters**  
`$callback` = The callback function to use.

**Return Values**  
The `Collection` instance with the result of the `each` callback function.

####Examples

    //@todo: Include example

###filter() {#filter}

Runs a filter over each collection item using a callback function.

    $collection->filter([callable $callback = null]);

**Parameters**  
`$callback` = The callback function to use.

**Return Values**  
A new instance of `Collection` with the result of the `filter` callback function.

####Examples

    //@todo: Include example

###map() {#map}

Runs a map over each collection items using a callback function.

    $collection->map(callable $callback);

**Parameters**  
`$callback` = The callback function to use.

**Return Values**  
A new instance of `Collection` with the result of the `map` callback function.

####Examples

    //@todo: Include example

###merge() {#merge}

Merges the data of one or more collections together.

    $collection->merge(mixed $data);

**Parameters**  
`$data` = Variable list of collections to merge.

**Return Values**  
A new instance of `Collection` with all data collections.

####Examples

    //@todo: Include example

###toJson() {#to-json}

Returns the collection containing the `JSON` representation of data.

    $collection->toJson([int $options = 0[, int $depth = 512]]);

**Parameters**  
`$options` = Bitmask consisting of <a target="_blank)" href="http://php.net/manual/en/json.constants.php">JSON constants</a>.  
`$depth` = Set the maximum depth. Must be greater than zero.

**Return Values**  
Returns a `JSON` encoded string on success or `FALSE` on failure.

####Examples

    //@todo: Include example

###__toString() {#to-string}

Returns the collection as a string.

    (string) $collection;

**Parameters**  
This method has no parameters.

**Return Values**  
Returns a `JSON` encoded string on success or `FALSE` on failure.

####Examples

    //@todo: Include example
