##Translator

The Translator allows you to support multiple languages within your applicaltion.  
If you use the included [FileLoader](/docs/master/localization/file-loader)
you can use `INI`, `PHP`, `XML`, `JSON` and `YAML` as language source files.

##Contents
<div id="contents" markdown="1">

[Instantiate](#instantiate)
[get()](#get)
[choice()](#choice)
[getLoadedTranslations()](#get-loaded-translations)
[setLocale()](#set-locale)
[getLocale()](#get-locale)
[setFallbackLocale()](#set-fallback-locale)
[getFallbackLocale()](#get-fallback-locale)


</div>

###Instantiate {#instantiate}

Creates a new `Translator` instance.

    new Avoxx\Localization\Translator(Avoxx\Localization\FileLoaderInterface $loader, string $locale [,string|null $fallbackLocale = 'en'])

**Parameters**  
`$loader` = The file loader instance.  
`$locale` =  The language locale.  
`$fallbackLocale` = The language fallback locale.

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
    
    // file structure (resources/lang/en/messages.php):
    return [
        'user' => [
            'greet' => 'Hello {name}, welcome back!',
        ],
    ];
           
    $locale = 'en';
    $directory ='resources/lang';
    $config = new Avoxx\Config\Config;
    $loader = new Avoxx\Localization\FileLoader($config, $directory);

    $translator =  new Avoxx\Localization\Translator($loader, $locale);

###get() {#get}

Returns the translation from a given key.

    $translator->get(string $key [, array $parameters = [] [, string $locale = null]]);

>**NOTE**  
If the `$fallbackLocale` is set to `null` or `false` in the `__construct()` method and the language value is not available, the `get()` method returns the language key.
	

**Parameters**  
`$key` = The translation key.  
`$parameters` = Optional array of (placeholder) parameters for the translation.  
`$locale` = The language locale.

**Return Values**  
The translated string or the language key if the translation does not exist and no fallback language is available.

####Examples

	// resources/lang/en/messages.php:
   	return [,
   		'hello' => 'Hello World',
        'user' => [
            'greet' => 'Hello {name}, welcome back!',
        ],
    ];
     
    // Returns a simple language value
    $translator->get('hello'); // 'Hello World'
    
    // Returns a language value with a placehoder
	$translator->get('user.greet', ['name' => 'Merlin'); // 'Hello Merlin, welcome back!'
	
	// Returns the key if language is not available
	$translator->get('user.greet', ['username' => 'John', 'de'); // 'user.greet'

###choice() {#choice}

Returns a translation according to an integer value.

    $translator->choice(string $key, int $number [, array $parameters = [] [, string $locale = null]]);

**Parameters**  
`$key` = The translation key.  
`$number` =  The number to use to find the indice of the translation.  
`$parameters` = Optional array of (placeholder) parameters for the translation.    
`$locale` = The language locale.

**Return Values**  
The translated string or the language key if the translation does not exist and no fallback language is available.

####Examples

	// resources/lang/en/messages.php:
   	return [,
   		'items' => 'There is {count} item|There are {count} items',
    ];
    
    
	// Returns a singular translation
	$translator->choice('items', 1); // 'There is 1 item'
	
	// Returns a plural translation
	$translator->choice('items', 20); // 'There are 20 items'
    
###getLoadedTranslations() {#get-loaded-translations}

Returns all loaded translations.

    $translator->getLoadedTranslations([string $locale = null]);

**Parameters**  
`$locale` = The language locale.

**Return Values**  
If the `$locale` string is set, this method returns the translations of the defined language as an array.  
Otherwise this method returns the translation values of all available languages.

####Examples
	
	// resources/lang/en/messages.php:
   	return [,
   		'hello' => 'Hello World!',
    ];
    
    // resources/lang/de/messages.php:
   	return [,
   		'hello' => 'Hallo Welt!',
    ];
    
    // Returns all available translations
    $translator->getLoadedTranslations();
    // [
    //		'en' => ['hello' => 'Hello World!'],
    //		'de' => ['hello' => 'Hallo Welt!'],
    // ];
    
    // Returns only the translations of the defined language
    $translator->getLoadedTranslations('en');
    // ['hello' => 'Hello World!']
    
###setLocale() {#set-locale}

Sets the default locale.

    $translator->setLocale(string $locale);

**Parameters**  
`$locale` = The language locale.

**Return Values**  
No value is returned.

####Examples

	$translator->setLocale('en');
	
###getLocale() {#get-locale}

Returns the current locale.

    $translator->getLocale();

**Parameters**  
This method has no parameters.

**Return Values**  
Returns the current locale string.

####Examples
	
	$translator->setLocale('de');
	$translator->getLocale(); // 'de'
	
###setFallbackLocale() {#set-fallback-locale}

Sets the fallback locale.

    $translator->setFallbackLocale(string $fallbackLocale);

**Parameters**  
`$fallbackLocale` = The fallback locale string or `null`.

**Return Values**   
No value is returned.

####Examples

	$translator->setFallbackLocale('en');
	
###getFallbackLocale() {#get-fallback-locale}

Returns the fallback locale.

    $translator->getFallbackLocale();

**Parameters**  
This method has no parameters.

**Return Values**  
Returns the current fallback locale string or `null`.

####Examples

	// Returns the fallback locale string
	$translator->setFallbackLocale('en');
	$translator->getFallbackLocale(); // 'en'
	
	// Returns null
	$translator->setFallbackLocale(null);
	$translator->getFallbackLocale() // null
	
