# Sublime Text

## Installations

#### Mac OS

To install Sublime text on mac, visit [download](https://www.sublimetext.com/3) page and download `.dmg` file. Once its download, double click on it and follow the instructions.

#### Ubuntu

Use following commands to install Sublime Text 3 on Ubuntu

```
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install -y sublime-text-installer
```

## Install Package Control

The simplest method of installation is through the Sublime Text console. The console is accessed via the `````ctrl+``` shortcut or the````View &gt; Show Console\` menu. Once open, paste the appropriate Python code for your version of Sublime Text into the console.

Now once the console is open click on this link [https://packagecontrol.io/installation](https://packagecontrol.io/installation) an copy the python code from there and paste it in sublime console.

It will take some time and it can also happen that we need to restart the sublime 2-3 times

## Installing package

Now, we assume that sublime package controller is being installed. To add package to sublime we need to open command palette. Try below keyboard shortcut to open it.

**Mac OS:**

```
Cmd+Shift+p (⌘+⇧+p)
```

**Linux/Windows:**

```
Ctrl+Shift+p
```

![](/assets/sublime-command-palette.jpg)

You will see that a popup open up then select "Package Control: Install Package" option and hit enter \(it'll take a few seconds\)

Once you have complete the above step a new popup will open up and then you can see list the packages.

![](/assets/sublime-package-list.jpg)

### Package List

Below are the list of most useful sublime package, you can find more useful packages at [https://packagecontrol.io/browse](https://packagecontrol.io/browse).

```
AdvancedNewFile
Alignment
CSS Extended Completions
CSS3
DocBlockr
EditorConfig
Emmet
Git
GitGutter
HTML5
JSCS-Formatter
MarkdownTOC
PHPIntel
Phpcs
SCSS Expander
Sass
SassBeautify
SideBarEnhancements
SublimeGit
SyntaxHighlightTools
WordPress Completions
WordPress Customizer
WordPress Snippets
WordPress
jQuery
```

## Project Setup for Development

Once its installed, you can start with the development on Sublime.

To setup project, use following steps:

* Open project folder in Sublime
* Save the project using `Project > Save Project As...` to your project folder, eg. _PROJECT.sublime-project_
* Now open `PROJECT.sublime-project` file which you saved under your project and replace below code in the same file, and save it.
  ```
  {
      "folders":
      [
          {
              "path": ".",
              "follow_symlinks": true,
              "file_exclude_patterns": [ ".DS_Store", "style-expanded.css", "*.map", "readme*" ],
              "folder_exclude_patterns": [ ".sass-cache", "languages", ".phpintel", "node_modules" ]
          }
      ]
  }
  ```
* You can also add WordPress library for function references, add below code under `[ … ]` brackets,

  ```
  {
      "path": "~/Documents/wordpress",
      "follow_symlinks": true,
      "folder_exclude_patterns": [".sass-cache", "languages", ".phpintel", "node_modules"],
      "file_exclude_patterns": [".DS_Store", "style-expanded.css", "*.map"]
  }
  ```

  _Note: Replace _`~/Documents/wordpress`_ path with your local WordPress folder path._

### Reference Links

* Sublime Installation: [http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3](http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3)
* Sublime Package Control: [https://packagecontrol.io/installation](https://packagecontrol.io/installation)
* Sublime Package List: [https://packagecontrol.io/installation](https://packagecontrol.io/installation)
* Installing WordPress Coding Standard: [https://gist.github.com/lloc/6650222](https://gist.github.com/lloc/6650222)
* Sublime PHPCS Configuration: [http://benmatselby.github.io/sublime-phpcs/](http://benmatselby.github.io/sublime-phpcs/)
* PHPCS Configuration:
  * [https://github.com/benmatselby/sublime-phpcs](https://github.com/benmatselby/sublime-phpcs)
  * [https://github.com/SublimeLinter/SublimeLinter-phpcs](https://github.com/SublimeLinter/SublimeLinter-phpcs)



