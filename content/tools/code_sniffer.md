# Code Sniffer

Code Sniffer (`phpcs`) is a comamnd line tool which validates php source code files against specified coding stanadard.

* Main Repo for Code Sniffer (phpcs) - https://github.com/squizlabs/PHP_CodeSniffer
* WordPress PHP Coding Standard -  https://make.wordpress.org/core/handbook/coding-standards/php/
* For WordPress, we use this repo - https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards. (*Code Sniffer doesn't provide built-in support for WordPress coding standard.*)

## Installation

### Mac

1. Install code sniffer - `brew install php-code-sniffer`
2. Install WordPress coding standard - `git clone -b master https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards.git /usr/local/etc/php-code-sniffer/Standards`
3. Set WordPress coding standard as default for phpcs `phpcs --config-set default_standard WordPress`

### Linux

TODO: Instructions for Ubuntu

## IDE Intergation

### Atom editor

You can use https://atom.io/packages/linter-phpcs . There are few more options.

1. Install atom package - `apm install linter-phpcs`
2. Open atom config file - `atom ~/.atom/config.cson`
3. Paste following code config in it (or update if there is a block for `"linter-phpcs"`.

```json
  "linter-phpcs":
    phpcsExecutablePath: "/usr/local/bin/phpcs"
    standard: "WordPress"
    enableWarning: 1
```

In above confif `/usr/local/bin/phpcs` is path to `phpcs` binary. Please verify if path is correct by running `which phpcs` command on your machine.

## Usage

* `phpcs -i` - show coding standards installed
* `phpcs <filename>` - run phpcs on specified file
* `phpcs .` - run phpcs recursively in current dir

### Automatic Fixing

`phpcs` has a companion script `phpcbf`. It automatically fixes codes based on `phpcs` recommendation.

All you need to do is - just run `phpcbf` instead of `phpcs`.

Please note that all `phpcs` recommendation can not be fixed by `phpcbf` so once you run `phpcbf`, check again with `phpcs`.
