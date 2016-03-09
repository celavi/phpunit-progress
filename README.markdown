Progress results printer for PHPUnit
====================================

    Note: This was forked from the original repo to fix a long standing
    typo. Original author no longer appears to be maintaining this code.

    The exact error (fixed here) was: 
    `Fatal error: Call to undefined method PHPUnit_Framework_TestResult::allCompletlyImplemented() in /vagrant_www/phpunit-progress/PHPUnit/Extensions/Progress/ResultPrinter.php on line 250`

This PHPUnit extention makes the printed tests results look similar to
Rspec's default formatter called "progress".

The progress printer tries to focus on the tests results only; That's why
a lot of the info printed by the default PHPUnit printer was removed.

Test results have the same colors and spacing as the Rspec's results.
If you want to see how results look, check out the screenshot below!

Usage
-----

There is more than one way to use this printer with PHPUnit. Probably
the easiest way is to pass the the printer (with it's location) as 
arguments to the `phpunit` command.

So clone this repo to someplace on your machine. Then copy the following
command and paste it to your terminal
(**Don't** forget to replace the things inside brackets)

    phpunit --include-path [Path to your clone of this repo] \
    --printer PHPUnit_Extensions_Progress_ResultPrinter   \
    --colors [Tests Path]

If you want to see a the skipped and incomplete tests too in the results,
you can add the `--verbose` argument the the command above.

Another way is to use a `phpunit.xml` file and pass its location as an argument.
If you are intrested in this way, I would recommend that you read [PHPUnit's
docs][docs].


Composer Install
======================================================
Add package to your composer.json file
By Repo:
```
    "repositories": [
    {
        "type": "vcs",
        "url": "https://github.com/michaelachrisco/phpunit-progress"
    }
```
By Development ENV:
```
"require-dev":{
  "michaelachrisco/phpunit-progress": "dev-master"
}
```
Install via composer:
`composer install`

Recommendation: Edit your ~/.bashrc or ~/.bash_profile to include an alias
```
alias phptest="phpunit --include-path vendor/michaelachrisco/phpunit-progress/ --printer PHPUnit_Extensions_Progress_ResultPrinter --color"
```

Use:
```bash
$ phptest
...............................................................  63 / 121 ( 52%)
..........................................................

Finished in 50.17 seconds
1121 tests, 2111 assertions
```
Screenshot
----------

Here is how the results of this extention look using the progress printer:
![Progress printer results in the terminal][shot]

[docs]:http://www.phpunit.de/manual/current/en/index.html
[shot]:https://github.com/Maher4Ever/phpunit-progress/raw/master/screenshot.png
