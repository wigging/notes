# Zsh

Some notes on using Zsh (also called Z shell) on a Mac.

## Prezto

The first thing to do on a new Mac is install Prezto. It is a configuration framework for Zsh. Visit the GitHub repo linked below for installation instructions and more information.

https://github.com/sorin-ionescu/prezto

## `.zshrc`

This is the contents of my Zsh profile which is located at `~/.zshrc`. It assumes Prezto has been installed. The section at the bottom is from the Anaconda installation of Python.

```
#
# Executes commands at the start of an interactive session.
#
# Authors:
#   Sorin Ionescu <sorin.ionescu@gmail.com>
#

# Source Prezto.
if [[ -s "${ZDOTDIR:-$HOME}/.zprezto/init.zsh" ]]; then
  source "${ZDOTDIR:-$HOME}/.zprezto/init.zsh"
fi

# Customize to your needs...

# Set VIM as the default terminal editor
export VISUAL=vim
export EDITOR=vim

# Use ipdb debugger for Python breakpoint()
export PYTHONBREAKPOINT=ipdb.set_trace

# Start terminal in desktop directory
cd ~/Desktop

# Open Sublime Text from command line
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"

# Automatically list files when changing directory
function chpwd() {
    emulate -L zsh
    ll
}

# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/Users/gavinw/miniconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/Users/gavinw/miniconda3/etc/profile.d/conda.sh" ]; then
        . "/Users/gavinw/miniconda3/etc/profile.d/conda.sh"
    else
        export PATH="/Users/gavinw/miniconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```
