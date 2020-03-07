# Safe text files editing as [`root`](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) in [Linux](https://en.wikipedia.org/wiki/Linux)

This topic should interest all [Linux](https://en.wikipedia.org/wiki/Linux) administrators as it is them who do the changes. Be it a home user, or a corporate admin. Without a doubt, no one wants to cripple their system just because power went down, or an [`ssh`](https://linux.die.net/man/1/ssh) session was interrupted by a bad connection, etcetera.

What's more, I enable you by using this script to edit files comfortably even from a [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) editor of your choice.

***

## [POSIX](https://en.wikipedia.org/wiki/POSIX) shells compatibility

This script enables you to edit text files on Linux as [`root`](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) safely through `sudoedit`.

Internal workings are that `sudoedit` copies the file into a temporary file, and overwrites the original file if, and only if, that file has successfuly been changed (saved) and the text editor properly exited.

It is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) shell script, it should work in any [Linux](https://en.wikipedia.org/wiki/Linux) distribution; more precisely, your [shell](https://en.wikipedia.org/wiki/Unix_shell).

***

## Requirements

The only requirement is to have [`sudo`](https://linux.die.net/man/8/sudo) properly installed and configured. If you have that, then `sudoedit` is available automatically as it is directly [`sudo`](https://linux.die.net/man/8/sudo)'s _edit_ feature.

***

## Usage instructions

### Download

Visit the [latest release download page](https://github.com/burianvlastimil/sudoedit-enhanced/releases/latest). Directly download the file named `sudoedit-enhanced` in that release. Note, that there is no need to adjust name or permissions, but you are free to do so if you wish.

### General

Once downloaded, place the script somewhere it can stay for good.

### Before use

Please, customize the editors lists to your preference before actually using this script, by default there are these specified at the beginning of the script:

```
sudoedit__cli_editor_list='nano vi'
sudoedit__gui_editor_list='gedit emacs xed subl code'
```

You don't have to explicitly remove those not present in your system, as the script checks on existence of the editors upon every call (more precisely upon every sourcing to your [shell](https://en.wikipedia.org/wiki/Unix_shell)'s environment).

***

### Integration into your [shell](https://en.wikipedia.org/wiki/Unix_shell)'s environment

The integration will vary greatly on what shell you use. As there are many [shell](https://en.wikipedia.org/wiki/Unix_shell)s in general use, I only provide guidance for [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29).

### [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)

There are multiple ways to source my script to your [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29), of course.

My personal recommendation is to create (if not yet existing) the `~/.bash_aliases` file and source my script from there using the _dot_ (.):

```
. /full/path/to/sudoedit-enhanced
```

Sourcing using the _dot_ (.) is a [POSIX](https://en.wikipedia.org/wiki/POSIX) way of doing so. In [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29), however, there is also the builtin command `source`, you can use it if you want.

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

### `sunano /etc/default/grub`

Disclaimer: There is absolutely no affiliation with [Nano editor](https://www.nano-editor.org/) team, but I _personaly like_ this command-line editor.

![GRUB config file safe editing with Nano CLI editor](https://vlastimilburian.cz/public/github_images/sudoedit-enhanced--nano.png)

***

### `susubl /etc/default/grub`

Disclaimer: There is absolutely no affiliation with [Sublime-Text editor](https://www.sublimetext.com/) team, but I _personaly like_ this graphical-interface editor.

![GRUB config file safe editing with Sublime-Text GUI editor](https://vlastimilburian.cz/public/github_images/sudoedit-enhanced--subl.png)

***

## Reporting bugs and suggestions

Please open a [new issue ticket](https://github.com/burianvlastimil/sudoedit-enhanced/issues/new).
