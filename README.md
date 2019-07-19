# Configuration files for MAC-OS Terminal

These are some configuration files that I use for MAC-OS.

## vim

For vim, I found [The ultimate vimrc](https://github.com/amix/vimrc). In this repo there is the basic version as of 10/07/2019, but you can install the ultimate version by following the guide.

How to install:
1. Copy "[.vimrc](https://github.com/dobretony/vimsetup/blob/mac-os/.vimrc)" into your home directory

## bash

### .bash_profile vs .bashrc
    In general, you have two files to take care of `.bash_profile` and `.bashrc`. `.bash_profile` is executed for login shells, while `.bashrc` is used for interactive non-login shells. What this means is that when you login into a terminal via the console or a ssh connection, `.bash_profile` is called. For all the other cases, like when you open an xterm, `.bashrc` is called.
    In MAC-OS, `.bash_profile` is configured to be executed by default on all terminals, including if you are using iTerm2. To bypass this and not have different configuration files, we call our `.bashrc` file in our `.bash_profile`:
```
if [ -f $HOME/.bashrc ]; then
    source $HOME/.bashrc
fi
```
## Bash Completion

Bash completion is a bash function that allows you to auto complete commands or arguments by typing partially commands or arguments, then pressing the [Tab] key. This will help you when writing the bash command in terminal.

### Instalation

> $ brew install bash-completion

Bash completion will be installed in /usr/local/etc/bash_completion.d .

For it to work, add this to your ~/.bashrc:
```
[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion
```

Or simply type:

> $ echo "[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion" >> ~/.bashrc

Restart your bash session:

> $ source ~/.bashrc

It has already been added to the `.bashrc` file of this repo.

## Fortune

A small mini game from Linux to color up the terminal a bit:

> brew install fortune

then add in .bashrc:

```
echo -e "${BCyan}This is BASH ${BRed}${BASH_VERSION%.*}${BCyan}"
 date
 if [ -x /usr/local/bin/fortune ]; then
     /usr/local/bin/fortune -s     # Makes our day a bit more fun.... :-)
 fi
```
