# Mac setup

Mostly up-to-date notes for setting up a Mac running macOS Catalina.

- [Local machine name](#local-machine-name)
- [Finder](#finder)
- [iCloud](#icloud)
- [Xcode](#xcode)
- [Wipr](#wipr)
- [iTerm2](#iterm2)
- [Prezto](#prezto)
- [Vim](#vim)
- [Sublime Text](#sublime-text)
- [Visual Studio Code](#visual-studio-code)
- [Git and GitHub](#git-and-github)
- [Homebrew](#homebrew)
- [aria2](#aria2)
- [LaTeX](#latex)
- [Miniconda](#miniconda)
- [Photos](#photos)
- [AppCleaner](#appcleaner)
- [Jekyll](#jekyll)

## Local machine name

Go to System Preferences -> Sharing and set the computer name.

## Finder

Go to Finder -> Preferences and configure preferences.

## iCloud

If the new Mac is replacing an older Mac, then sign out of iCloud on the old Mac.

Sign in to iCloud on the new Mac to sync bookmarks, email, etc.

Disable FaceTime by opening the app and signing out.

## Xcode

Install Xcode from the App Store which will also install Git.

Open Xcode to make sure developer tools and components are installed.

## Wipr

Install Wipr from the App Store then open Wipr to enable it in Safari.

## iTerm2

Download from [iterm2.com](https://iterm2.com)

Snazzy theme available at [github.com/sindresorhus/iterm2-snazzy](https://github.com/sindresorhus/iterm2-snazzy)

## Prezto

See installation instructions at [github.com/sorin-ionescu/prezto](https://github.com/sorin-ionescu/prezto)

Add the git module to `.zpreztorc`

## Vim

Place the following settings in the `~/.vimrc` file:

```bash
" Use Vim settings, which are much better than Vi settings. Vi is for grandpas.
" This must be first, because it changes other options as a side effect.
set nocompatible

" Enable file type detection and do language-dependent indenting
filetype plugin indent on

" Turn on syntax highlighting
syntax on

" Make backspace behave in a sane manner
set backspace=indent,eol,start

" Use the system clipboard
set clipboard=unnamed

" Allow switching buffers without saving currently modified file
set hidden

" Highlight search results
set hlsearch

" Enable mouse support
set mouse=a

" Show line numbers
set number

" Disable swap file creation
set noswapfile

" Always display status line
set laststatus=2

" Press jj to exit from insert mode
imap jj <Esc>

" change cursor to vertical bar in insert mode when using iTerm on Mac
if $TERM_PROGRAM =~ "iTerm"
  let &t_SI = "\<Esc>]50;CursorShape=1\x7" " vertical bar in insert mode
  let &t_EI = "\<Esc>]50;CursorShape=0\x7" " block in normal mode
endif
```

## Sublime Text

Download from [sublimetext.com](https://www.sublimetext.com) then use license key to register the application.

To open Sublime Text from the command line add the following alias to `~/.zshrc`:

```bash
# Open Sublime Text from command line
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
```

Preferences for Sublime Text are given below. Go to Sublime Text -> Preferences -> Settings. The empty ignored packages setting enables Vim mode in Sublime Text.

```json
{
    "color_scheme": "Packages/Color Scheme - Default/Mariana.sublime-color-scheme",
    "folder_exclude_patterns":
    [
        "*.egg-info",
        ".git",
        "__pycache__"
    ],
    "font_size": 13,
    "hot_exit": false,
    "ignored_packages":
    [
    ],
    "theme": "Adaptive.sublime-theme",
    "translate_tabs_to_spaces": true,
    "trim_trailing_white_space_on_save": true
}
```

Install package control with `Command-Shift-P`.

Install SublimeLinter package, see instructions at [sublimelinter.com](http://sublimelinter.com/)

Install SublimeLinter-flake8 for Python, see [github.com/SublimeLinter/SublimeLinter-flake8](https://github.com/SublimeLinter/SublimeLinter-flake8)

Make sure flake8 is installed otherwise the flake8 linter will not work.

```bash
conda install flake8
```

In Sublime Text, go to `Preferences -> Package Settings -> SublimeLinter -> Settings` and add the following linter options:

```json
{
    "gutter_theme": "Default",
    "linters": {
        "flake8": {
            "args": ["--ignore=E501,W605"]
        }
    }
}
```

Vim key bindings shown below are for exiting Vim insert mode in Sublime Text. These settings are accessed from the menu `Sublime Text -> Preferences -> Key Bindings`.

```json
[
    {
        "keys": ["j", "j"],
        "command": "exit_insert_mode",
        "context": [
            { "key": "setting.command_mode", "operand": false },
            { "key": "setting.is_widget", "operand": false}
        ]
    },
]
```

These settings are for the SideBarEnhancements plugin. The settings are available in the menu at `Sublime Text -> Preferences -> Package Settings -> Side Bar - > Settings`.

```json
{
    "close_affected_buffers_when_deleting_even_if_dirty": true,
}
```

Install LaTeXTools package, see instructions at [latextools.readthedocs.io](https://latextools.readthedocs.io/en/latest/).

In `Sublime Text -> Preferences -> Package Settings -> LaTeXTools -> Settings - User` make the Preview app the viewer for the PDF.

```json
"viewer": "preview",
```

## Visual Studio Code

Extensions and theme. For the Rewrap extension, word wrapping can be automatically enabled with `Cmd+Shift+P` then select `Rewrap: Toggle Auto-Wrap`.

- LaTeX
- One Dark Pro
- Python
- reStructuredText
- Rewrap
- Vim

User settings are in the `settings.json` file. This file can be edited with `Cmd+Shift+P` then select `Preferences: Open Settings (JSON)`.

```json
{
    "editor.fontFamily": "Menlo",
    "editor.fontSize": 13,
    "editor.fontWeight": "bold",
    "editor.hover.enabled": false,
    "editor.lineHeight": 17,
    "editor.links": false,
    "editor.minimap.enabled": false,
    "editor.parameterHints.enabled": false,
    "editor.scrollBeyondLastLine": true,
    "files.exclude": {
        "**/.ipynb_checkpoints": true,
        "**/__pycache__": true,
        "**/.pytest_cache": true
    },
    "latex-workshop.latex.clean.enabled": true,
    "latex-workshop.view.pdf.viewer": "tab",
    "python.jediEnabled": false,
    "python.linting.enabled": true,
    "python.linting.flake8Enabled": true,
    "python.linting.flake8Args": ["--ignore=E302,E501,W605"],
    "python.linting.pylintEnabled": false,
    "restructuredtext.linter.extraArgs": ["--ignore D001"],
    "telemetry.enableCrashReporter": false,
    "telemetry.enableTelemetry": false,
    "terminal.explorerKind": "external",
    "terminal.external.osxExec": "iTerm.app",
    "terminal.integrated.fontSize": 13,
    "vim.insertModeKeyBindings": [
        {
            "before": ["j", "j"],
            "after": ["<Esc>"]
        }
    ],
    "workbench.colorTheme": "One Dark Pro",
    "workbench.iconTheme": "vs-minimal"
}
```

Key bindings (keyboard shortcuts) go in the `keybindings.json` file.

```json
[
    {
        "key": "ctrl+tab",
        "command": "workbench.action.nextEditor"
    },
    {
        "key": "ctrl+`",
        "command": "workbench.action.focusActiveEditorGroup",
        "when": "terminalFocus"
    },
    {
        "key": "ctrl+`",
        "command": "workbench.action.terminal.focus",
        "when": "!terminalFocus"
    },
]
```

## Git and GitHub

Configure Git in the terminal using the following commands (change name and email accordingly):

```bash
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"
```

Use [gitignore.io](https://www.gitignore.io) to create a Git ignore file at `~/.gitignore` and set it as the global file with:

```bash
git config --global core.excludesfile ~/.gitignore
```

Use a personal access token as the GitHub password for the command line. See [here](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) for more details.

## Homebrew

Installation instructions are provided at [brew.sh](https://brew.sh) and don't forget to disable analytics via link provided after installation.

## aria2

Installation instructions provided at [aria2.github.io](https://aria2.github.io)

## LaTeX

Download from [www.tug.org/mactex/](http://www.tug.org/mactex/)

## Miniconda

Installer available at [docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)

Copy the contents of `.bash_profile` into the `.zshrc` file.

To disable auto activate use:

```bash
conda config --set auto_activate_base false
```

To permanently enable Miniconda Python use the following in `~/.zshrc`:

```bash
# Set Python PATH to Miniconda3
export PATH="$HOME/miniconda3/bin:$PATH"
```

## Photos

Move the photos library `~/Pictures/Photos Library.photoslibrary` from the old Mac to the new Mac.

## AppCleaner

Download from [freemacsoft.net/appcleaner](https://freemacsoft.net/appcleaner/)

## Jekyll

Instructions for installing Jekyll for use with GitHub Pages are detailed in the [README](https://github.com/wigging/wigging.github.io) for my personal website.
