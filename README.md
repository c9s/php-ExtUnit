ExtUnit
=============

By using this extension testcase and a phpunit-exttest runner, you 
can easily integrate phpunit tests with your extension.

Installation
------------

    $ pear channel-discover pear.corneltek.com
    $ pear install corneltek/ExtUnit

Usage
------

The extunit runner helps you debug and test your extension, it 
compiles your extension and load your extension so file in the `modules` directory before 
you test it.


Create the extunit config file for your extension:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<extunit>
    <extension>apc</extension>
</extunit>
```

e.g., to load the compiled extension and run specific php script:

```sh
$ extunit php_script.php
```

to load the compiled extension and run the php script with gdb:

```sh
$ extunit --gdb php_script.php
```

to load the compiled extension and run gdn with phpunit:

```sh
$ extunit --phpunit --gdb tests/APCExtensionTest.php
```

To use the extension testcase please see `PHPUnit_Framework_ExtensionTestCase` class.


