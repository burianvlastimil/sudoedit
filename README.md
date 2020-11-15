# Safe text files editing as [`root`](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) (wiki) in [Linux](https://en.wikipedia.org/wiki/Linux) (wiki)

This topic should interest all [Linux](https://en.wikipedia.org/wiki/Linux) (wiki) administrators as it is them who do the changes. Be it a home user, or a corporate admin. Without a doubt, no one wants to cripple their system just because the power went down, or an [`ssh`](https://linux.die.net/man/1/ssh) (man page) session was interrupted by a bad connection, etcetera.

What's more, by using this script I enable you to edit files comfortably even from a [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) (wiki) editor of your choice.

***

## [POSIX](https://en.wikipedia.org/wiki/POSIX) (wiki) shells compatibility

This script enables you to edit text files on Linux as [`root`](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) (wiki) safely through `sudoedit`.

Internal workings are that `sudoedit` copies the file into a temporary file, and overwrites the original file if, and only if, that file has successfuly been changed (saved) and the text editor properly exited.

It is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) (wiki) [shell script](https://en.wikipedia.org/wiki/Shell_script), it should work in any [Linux](https://en.wikipedia.org/wiki/Linux) (wiki) distribution; more precisely, your [shell](https://en.wikipedia.org/wiki/Unix_shell) (wiki).

***

## Requirements

The only requirement is to have [`sudo`](https://linux.die.net/man/8/sudo) properly installed and configured. If you have that, then `sudoedit` is available automatically as it is directly [`sudo`](https://linux.die.net/man/8/sudo)'s _edit_ feature, it can even be invoked as `sudo -e`.

***

## Usage instructions

### Download

Visit the [latest release download page](https://github.com/burianvlastimil/sudoedit-enhanced/releases/latest). Directly download the file named `sudoedit-enhanced` in that release. Note, that there is no need to adjust name or permissions, but you are free to do so if you wish.

### General

Once downloaded, place the script somewhere it can stay for good.

### Before use

Please, customize the editors lists to your preference before actually using this script, by default there are these specified at the beginning of the script:

```
sudoedit__cli_editors='vi nano'
sudoedit__gui_editors='subl atom'
```

You don't have to explicitly remove those not present in your system, as the script checks on existence of the editors upon every call (more precisely upon every sourcing to your [shell](https://en.wikipedia.org/wiki/Unix_shell)'s (wiki) environment).

***

### Integration into your [shell](https://en.wikipedia.org/wiki/Unix_shell)'s environment

The integration will vary greatly on what shell you use. As there are many [shells](https://en.wikipedia.org/wiki/Unix_shell) (wiki) in general use, I only provide guidance for [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki).

### [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki)

There are multiple ways to source my script to your [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki), of course.

My personal recommendation is to create (if not yet existing) the `~/.bash_aliases` file and source my script from there using the _dot_ (`.`):

```
. /full/path/to/sudoedit-enhanced
```

Sourcing using the _dot_ (.) is a [POSIX](https://en.wikipedia.org/wiki/POSIX) (wiki) way of doing so. Although, in [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki), there is also the `source` builtin command, so you can use that, if you want.

Afterward, you need to make sure that these (or similar) lines are present and not commented out in your `~/.bashrc`:

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

***

### Generated `alias`es

On every machine, there will always be different number of `alias`es.

As said before, the script checks on existence of each editor. This is true also for `alias` generators.

These `alias`es begin with `su` + name of the editor.

***

## Examples of an actual use

### `sunano /etc/default/grub` (using the [Nano editor (CLI)](https://www.nano-editor.org/))

Disclaimer: There is **no affiliation** with the [Nano editor](https://www.nano-editor.org/) (home page) team, but I _personaly like_ this command-line editor.

![GRUB config file safe editing with Nano CLI editor](https://vlastimilburian.cz/public/github_images/sudoedit-enhanced--nano.png)

Download: The [Nano editor](https://www.nano-editor.org/) (home page) can be downloaded from [this page](https://www.nano-editor.org/download.php), but note you would have to compile the program yourself, which is what I am doing.

***

### `susubl /etc/default/grub` (using the [Sublime-Text editor (GUI)](https://www.sublimetext.com/))

Disclaimer: There is **no affiliation** with the [Sublime-Text editor](https://www.sublimetext.com/) (home page) team, but I _personaly like_ this graphical-interface editor.

![GRUB config file safe editing with Sublime-Text GUI editor](https://vlastimilburian.cz/public/github_images/sudoedit-enhanced--subl.png)

Download: The [Sublime-Text editor](https://www.sublimetext.com/) (home page) can be downloaded from [this page](https://www.sublimetext.com/3).

***

## Reporting bugs and suggestions

Please open a [new issue ticket](https://github.com/burianvlastimil/sudoedit-enhanced/issues/new) (direct link) or you can also mail me at [info@vlastimilburian.cz](mailto:info@vlastimilburian.cz) (email link).
