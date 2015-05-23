# PHP-SASS-WATCHER

*This was meant as an experiment and resulted in [Laravel SASS](https://github.com/panique/laravel-sass),
a better compiler for SASS in pure PHP. There are also better scripts for doing this job, like all the JavaScript build 
tools. Please keep this in mind :) !*

## What does this tool do ?

The php-sass-watcher is not a standalone compiler, it's just a little method that uses the excellent
[scssphp compiler](http://leafo.net/scssphp/) written by [Leaf Corcoran](https://twitter.com/moonscript) and adds
automatic interval-compiling to it.

The php-sass-watcher is one simple php file that runs an unlimited time (!) and compiles all .scss files in your scss
folder to .css files in your css folder automatically in a configurable interval (which is 1 second by default).
That's it. No configuration (outside of the file itself) needs to be done, you can install it within 60 seconds.
It does not mess up your development environment, it's just a tiny file.

To keep things as minimal as possible, this tool compiles every X seconds, regardless of changes within the files.
This seems weird, but makes sense as checking for changes in the files is more CPU-extensive than simply
re-compiling them. SassWatcher uses scssphp, the best SASS compiler in PHP available.

## Which SASS/SCSS version is supported ?

The currently supported version of **SCSS syntax is 3.2.12**, which is the latest one.
To avoid confusion: SASS is the name of the language itself, and also the "name" of the "first" version of the
syntax (which was quite different than CSS). Then SASS's syntax was changed to "SCSS", which is more like CSS, but
with awesome additional possibilities and features.
The compiler uses the SCSS syntax, which is recommended and mostly used. The old SASS syntax is not supported.

## How the tool works:

 * Every X seconds ALL files in the scss folder will be compiled to same-name .css files in the css folder.
 * The tool does not stop when a .scss file is broken, has syntax error or similar.
 * The tool does not compile when .scss file is broken, has syntax error or similar.
   It will only compile next time when there's a valid scss file.

## How to install & use this tool

1. Download scssphp from http://leafo.net/scssphp and put it somewhere.
2. Edit $sass_watcher->watch( ... ); in the last line of php-sass-watcher.php and put the path of your scss folder,
   your css folder and the location of the scssphp file in. See the parameter list below.
2. Make sure PHP can write into your CSS folder.
3. Run the script: Simple way, from browser, just enter the URL to scss-compiler.php:
   http://127.0.0.1/folder/php-sass-watcher.php
   The script will run forever, even if you close the browser window.
   PHPStorm users can run the script by right-clicking the file and selecting "Run php-sass-watcher.php".
4. To stop the script, stop/restart your Apache/Nginx/etc. or press the red "stop process button in PHPStorm.

*Please note: Some IDEs / code editors don't show new/updated files instantly. Refresh/reload the files/folders to see
the changes.*

## The parameters:

```php
$sass_watcher = new SassWatcher();
$sass_watcher->watch("path/to/scss/", "path/to/css/", 1, "vendor/leafo/scssphp/scss.inc.php");
```

1. relative path to your SCSS folder
2. relative path to your CSS folder (make sure PHP has write-rights here)
3. the compiling interval (in seconds)
4. relative path to the scss.inc.php file, which is the main file of the SASS compiler used here.
   Download the script manually from http://leafo.net/scssphp/ or "require" it via Composer: `"leafo/scssphp": "0.0.9"`
5. optional: how the .css output should look like. See http://leafo.net/scssphp/docs/#output_formatting for more.

## How to work with mixins

Currently your mixin files need to be in exactly the same folder like your other .scss, then the @import will work
perfectly. Custom mixing folders are on my todo-list.

## Links

- [Official SASS homepage](http://sass-lang.com/)
- [scssphp SASS compiler homepage](http://leafo.net/scssphp/)
- [SASS at Wikipedia](http://en.wikipedia.org/wiki/Sass_%28stylesheet_language%29)

## Connected projects

If you like, check my other projects:

#### MINI and MINI2

A super-reduced and naked bare-bone application, just a little application skeleton.

http://php-mini.com

#### php-login / HUGE

A collection of 4 login scripts for PHP, from a super-simple one-file script with a SQLite one-file to a quite 
professional MVC frameworks solution (that has been used in large projects). All scripts use the most advanced
hashing algorithms possible in PHP, exactly like the PHP core developers want you to use them.

http://www.php-login.net

https://github.com/panique/huge (full framework)

https://github.com/panique/php-login-minimal (minimal)

https://github.com/panique/php-login-advanced (advanced)

https://github.com/panique/php-login-one-file (one-file)

#### My blog

http://www.dev-metal.com

## License

This project is licensed under the MIT License.
This means you can use and modify it for free in private or commercial projects.

## Contribute

Feel free to contribute (it's okay to push to master branch as this project is really small).

## Support

If you think this script is useful and saves you a lot of work, then think about supporting the project by renting a
server at [HOST1PLUS](https://affiliates.host1plus.com/ref/devmetal/36f4d828.html).