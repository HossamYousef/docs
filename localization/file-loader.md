##FileLoader

The FileLoader class loads the language files of all different languages for the application.  
This class is a wrapper of the [Avoxx\Config](/docs/master/config/config) package, therefore you can use `INI`, `PHP`, `XML`, `JSON` and `YAML` as language source files.


##Contents

<div id="contents" markdown="1">

[Instantiate](#instantiate)
[load()](#load)

</div>


###Instantiate {#instantiate}

Creates a new `FileLoader` instance.

    new Avoxx\Localization\FileLoader(Avoxx\Config\Config $config, string $directory);

**Parameters**  
`$config` =  The `Avoxx\Config\Config` instance.  
`directory` = The language directory.

**Return Values**  
No value is returned.

####Examples
	
	// directory structure:
    resouces/
    |-- lang/
    |     |-- de/
    |     |    |-- messages.php
    |     |-- en/
    |     |    |-- messages.php
    
    $directory ='resources/lang';
    $config = new Avoxx\Config\Config;
    
    $loader = new Avoxx\Localization\FileLoader($config, $directory);
    
    
###load() {#load}

Loads the files from the given locale directory and returns them as an array.

	$fileLoader->load(string $localeDir);

**Parameters**  
`$localeDir` = The locale source directory name.

**Return Values**  
Returns the content of the loaded language file(s) or an empty array if the language directory is not available or empty.

####Examples

	// Loads all files from 'resources/lang/en' directory
    $loader->load('en');

