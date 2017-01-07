##Debug

The `Avoxx\Utility\Debug`  offers a secure static method that displays structured information about a variable.

##Contents

<div id="contents" markdown="1">

[dump()](#dump)
[setSapi()](#set-sapi)
[getSapi()](#get-sapi)

</div>

###dump() {#dump}
 
Dumps information about a variable.

    Debug::dump(mixed $value [, string $title = null [, boolean $plain = false [, boolean $echo = true]]]);

>**NOTE**  
If you run this method in the `cli` environment, it returns the result as plain text!
 
**Parameters**  
`$value` = The variable to dump.  
`$title`= Optional custom title for the debug output.  
`$plain` =  If `true`, the dump is in plain text. If `false`, the dump is in HTML format.  
`$echo` =  If `true`, the dump is directly displayed.
 
**Return Values**  
If `$echo` is set to `true`, the dump is directly displayed.  
If `$echo` is set to `false`, the dump is returned.

####Examples

    $value = 'AVOXX is awesome';
    
    Debug::dump($value);
    // AVOXX DEBUGGER
    // string: "AVOXX is awesome" (16 chars)

    // Dump value with custom title    
    Debug::dump($value, 'Dump value');
    // Dump value
    // string: "AVOXX is awesome" (16 chars)

    // Dump value as plain text
    Debug::dump($value, null, true); // AVOXX DEBUGGER string: "Hello world!" (12 chars)

    //Prevent a value from appearing)    
    $result = Debug::dump($value, null, true, false);
    echo $result; // AVOXX DEBUGGER string: "Hello world!" (12 chars) 

###setSapi() {#set-sapi}

Sets the debug output environment.

	Debug::setSapi(string $sapi);

**Parameters**  
`$sapi` = The debug output environment (e.g. `cli`, `cli-server`, `cgi`).

**Return Values**  
No value is returned.

####Examples

    Debug::setSapi('cli');
    
    $value = 'Hello world!';
    
    Debug::dump($value); // AVOXX DEBUGGER string: "Hello world!" (12 chars) 

###getSapi() {#get-sapi}

Returns the debug output environment.  
By default, this method returns the result of the PHP constant <a target="_blank" href="http://php.net/manual/en/function.php-sapi-name.php">PHP_SAPI</a>.

	Debug::getSapi();

**Parameters**  
This method has no parameters.

**Return Values**  
Returns the debug output environment string.

####Examples

    if (Debug::getSapi() == 'cli-server') {
        echo 'Development Server';
    }
