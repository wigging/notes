# Zsh

Some notes on using Zsh (also called Z shell) on a Mac.

## Pure

The first thing to do on a new Mac is install Pure to improve the Zsh prompt. Use the suggested theme in the Pure documentation.

https://github.com/sindresorhus/pure

## .zshrc

This is the contents of my Zsh profile which is located at `~/.zshrc`. It assumes Pure, Xcode, and Miniconda have been installed. The section at the bottom is from the Miniconda installation of Python.

```
# Pure prompt configuration
# https://github.com/sindresorhus/pure
# ----------------------------------------------------------------------------

fpath+=$HOME/.zsh/pure

autoload -U promptinit; promptinit
prompt pure

PURE_GIT_DOWN_ARROW=⬇︎

PURE_GIT_UP_ARROW=⬆︎

# Zsh configuration
# ----------------------------------------------------------------------------

# Enable completion system
autoload -Uz compinit && compinit

# Enable color for `ls` output
export CLICOLOR=1

# Set VIM as the default terminal editor
export VISUAL=vim
export EDITOR=vim

# Use ipdb debugger as the Python breakpoint() debugger
export PYTHONBREAKPOINT=ipdb.set_trace

# Start terminal in ~/Desktop directory and list files
cd ~/Desktop

# Open Sublime Text from command line
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"

# List line-by-line including hidden files
alias la="ls -aoh"

# List line-by-line
alias ll="ls -oh"

# Change directory without using `cd`
setopt AUTO_CD

# List files after changing directory
function chpwd() {
    emulate -L zsh
    ls
}

# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/Users/gavinw/miniconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
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
