ExtUnit
=============

You should forgot the old `run-tests.php` script. This saves your life!

![Screenshot](http://images.plurk.com/yjqO-46eQ3xA2IgA69F3hcuMVOc.jpg)

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

e.g., To load the compiled extension and run specific php script:

```sh
$ extunit php_script.php
```

To load the compiled extension and run the php script with gdb:

```sh
$ extunit --gdb php_script.php
```

The above command generates the `.gdbinit` file, which setup the executable path and the arguments 
for you. so you don't need to write the php option arguments by yourself.

note that `extunit` won't override the `.gdbinit` for you, so if you want to run other test files with gdb
you should remove the generated `.gdbinit` file before you run another test file.

To load the compiled extension and run gdn with phpunit:

```sh
$ extunit --phpunit --gdb tests/APCExtensionTest.php
```

To use the extension testcase please see `PHPUnit_Framework_ExtensionTestCase` class.


