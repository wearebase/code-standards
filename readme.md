# Code Standards

This repository contains a set of code standards and guidelines, along with a few helpful resources.
These standards are part of the [@wearebase](https://github.com/wearebase) code quality assurance process.

Please note: This document is biased towards PHP and JavaScript, which are the most common languages we currently use. Much of it should apply to other languages (such as Objective-C, Java, Python and Ruby) however if an existing industry standard is in widespread use then it should be preferred. Wherever possible we try to follow industry standards.

Content is licensed under the Creative Commons - CC BY 3.0 license.


## Files and formatting

* Save files as UTF-8
* UNIX-style line endings. (`git` should take care of this for you if you use Windows)
* Indent using 4 spaces. This is the standard for PHP. Your editor can make this seamless for you.
* Lowercase filenames, without any punctuation apart from `-` and `.` (except where this contradicts with another standard)


## Comments

* Comment what is not obvious


## Source control (eg `git`)

* Large changes to whitespace should be in their own commit
* Where possible try to name online repositories in the format "[Client name] - [Language / type] - [Project name]"
   * E.g. Base - Android Library - User API
   * The reason for including the language is to avoid conflict of projects due to the vast array of languages that may be used on a single project


## Passwords

* Use industry best practices for storing passwords safely. We currently use [bcrypt](http://en.wikipedia.org/wiki/Bcrypt) to store user passwords in databases (for example, [wp_bcrypt](https://github.com/dxw/wp_bcrypt) for WordPress).
* User login forms should be protected against remote brute force attacks (for example, [Login LockDown](http://wordpress.org/extend/plugins/login-lockdown/) for WordPress).
* Passwords must be "strong", meaning they have an [entropy](http://en.wikipedia.org/wiki/Password_strength#Random_passwords) of at least 56 bits. This is approximately equal to a password with 12 lowercase characters or a password with 9 mixed-case alphanumeric characters.


## Security

* Industry best practices should be followed for security
* Never trust any type of user data
* Remove services such as FTP, which transfer data unencrypted, and instead use secure services such as SFTP.
* Private SSH keys should have pass-phrases


## PHP

* PHP code must have no syntax errors (check with `php -l filename.php`)
* Use [PSR-0](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md) or the framework’s class autoloader when loading classes
* Follow [PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md) to the letter with all new code and when updating legacy code
* Follow [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md), except when working with legacy files
* Naming conventions should follow http://en.wikipedia.org/wiki/Domain-driven_design and http://symfony.com/doc/current/contributing/code/conventions.html#method-names
* Try not to mix PHP with HTML


## SQL

* Use [parameterized queries](http://stackoverflow.com/questions/60174/how-to-prevent-sql-injection-in-php) whenever possible


## JavaScript

* JavaScript code must not show errors on [JSHint](http://www.jshint.com/)
* Formatting
    * 4 spaces, not tabs (to be consistent with PHP)


## SCSS

* Follow scss-lint's guidelines, use a [scss-lint in Sublime](https://sublime.wbond.net/packages/SublimeLinter-contrib-scss-lint)
* Formatting
   * 2 spaces, not tabs
   * A space to the left of `{` and a newline after
   * Rules on new lines, with a space after `:`
   * `}` on its own
   * Single line per selector
   * Where possible, order rules in alphabetical order.
   * Always place prefixed rules above non-prefixed rules.
   * Comma seperated rules go on a new line
* Guidelines
   * Keep to hex codes rather than text, ie `#000` not `black`
   * Keep to shorter hex codes where possible, ie `#000` not `#000000`
   * Use `0` not `0px` and not `none`
* Avoid going [more than 4 levels deep in nesting](http://thesassway.com/beginner/the-inception-rule)
* Sass comments (`//`) instead of CSS comments (`/* ... */`)
* Prefer class selectors (`.`) and avoid id selectors (`#`)
* Comment where styles are used if it is not obvious
* CSS hacks should be avoided and documented if they are ever used (use [conditional classes on the html element](http://paulirish.com/2008/conditional-stylesheets-vs-css-hacks-answer-neither/) instead)
* Follow [SMACSS](https://smacss.com/) where possible


## HTML

* `.class-names-lowercase-with-dashes`
* `#ids-lowercase-with-dashes`
* HTML5 doctype: `<!doctype html>`
* HTML should be mostly valid
* Follow [SMACSS](https://smacss.com/) where possible


## Performance

* Compress images and other assets for the web
* Follow [YSlow rules](http://developer.yahoo.com/performance/rules.html)
* Follow [Google Page speed rules](https://developers.google.com/speed/docs/best-practices/rules_intro)

# Servers

## Web servers

* The web server (eg Nginx or Apache) should serve the project document root from `/var/www/project-name`.
* This path MUST be 1 of:
  * where the project actually lives (if project root == web root and it's basic upload / git deploy, without releases)
  * a symlink to the web root outside of `/var/www`, eg `/home/app-user/project-name/current/web`
