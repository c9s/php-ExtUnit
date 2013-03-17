ExtUnit
=============
[![Build Status](https://travis-ci.org/c9s/php-ExtUnit.png)](https://travis-ci.org/c9s/php-ExtUnit)

You should forgot the old `run-tests.php` script. This saves your life!

![Screenshot](http://images.plurk.com/yjqO-46eQ3xA2IgA69F3hcuMVOc.jpg)

extunit with gdb: <http://img.im/i/src-13116-pvtr66/8000.jpg>


Merit:

- Always re-compile you source code before you test it.
- Autoload your compiled extension `.so` file before you run the tests.
- Run phpunit tests without installing your extension everytime.
- Run unit tests with your PHP extension or with your pure PHP implementation.
- Support GDB, automatically write `.gdbinit` to bootstrap the GDB environment.

Installation
------------

```sh
$ pear channel-discover pear.corneltek.com
$ pear install corneltek/ExtUnit
```

Usage
------

The extunit runner helps you debug and test your extension, it 
compiles your extension and load your extension `.so` file from the `modules` directory before 
you run the tests or script.

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


