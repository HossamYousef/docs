##Config

The Config class is a file configuration loader. Supported file types are
`INI`, `PHP`, `XML`, `JSON` and `YAML`.

##Contents

<div id="contents" markdown="1">

[Instantiate & load()](#instantiate-and-load)
[set()](#set)
[get()](#get)
[has()](#has)
[all()](#all)

</div>

###Instantiate & load() {#instantiate-and-load}

Creates a new `Config` instance and loads configuration files.

    new Avoxx\Config\Config([string|array $file = null]);

>**NOTE**  
If you load multiple files with the same configuration key,
the value of the last loaded file is used.  
When loading a directory, the files are loaded in by name alphabetically.

**Parameters**  
`$file` = The configuration file, array or directory.

**Return Values**  
No value is returned.

####Examples

    // Load a single configuration file
    $config = new Avoxx\Config\Config('./config/database.yaml');
    
    // Load a configuration file array
    $config = new Config([
        './config/app.json',
        './config/database.yml',
    ]);

    // Load a configuration file directory)
    $config = new Avoxx\Config\Config('./config');

    // Load a configuration file with load() meethod
    $config->load('./config/app.ini');

###set() {#set}

Sets a new configuration value.

    $config->set(string $key, string|array $value);

>**NOTE**  
Any changes made this way are not reflected back to the source files.

**Parameters**  
`$key` = The configuration key.  
`$value` = The configuration string or array.

**Return Values**  
No value is returned.

####Examples

    // Set a configuration array
    $config->set('database', [
        'driver' => 'mysql',
        'host' => '127.0.0.1',
        'user' => 'root',
        'pass' => 'secret',
    ]);

    // Add a configuration value to an existing array    
    $config->set('database.port', 3306);


    // Overwrite an existing configuration value
    $config->set('database.driver', 'pgsql');

###get() {#get}

Returns a configuration value.

    $config->get(string $key [, string|array $default = null]);

**Parameters**  
`$key` = The configuration key.  
`$default` = The default fallback value.

**Return Values**  
The configuration value or the `$default` fallback value,
if the configuration value does not exists.

####Examples

    $config->set('name', 'Merlin');

    // Return a configuration value
    $config->get('name'); // Merlin

    // Return a default fallback value, if a configuration value does not exists
    $config->get('username', 'Not available'); // 'Not available'

###has() {#has}

Checks whether a configuration value is available.

    $config->has(string $key);

**Parameters**  
`$key` = Name of the configuration key being checked for.

**Return Values**  
Returns `true` if the value exists and `false` otherwise.

####Examples

    $config->set('database.driver', 'pgsql');
    $config->has('database.driver'); // true

###all() {#all}

Returns all available configuration values.

    $config->all();

**Parameters**  
This method has no parameters.  
    
**Return Values**  
All configuration values, or an empty array.

####Examples

    $config->set('database', [
        'driver' => 'mysql',
        'host' => '127.0.0.1',
        'user' => 'root',
        'pass' => 'secret',
    ]);
        
    $config->all();
    
    // database [
    //    driver => mysql
    //    host => 127.0.0.1
    //    user => root
    //    pass => secret
    // ]
