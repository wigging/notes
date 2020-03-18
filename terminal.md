# Terminal

Useful commands for working in the terminal. Some of the commands are specific to macOS.

## Keyboard shortcuts

Various keyboard shortcuts for working with the command line prompt.

`Ctrl + a` - go to beginning of the line

`Ctrl + c` - cancel the command

`Ctrl + e` - go to end of the line

`Ctrl + u` - clear up to the beginning

## General commands

My preferred permissions for folders and files.

```bash
chmod 755   # folder permissions
chmod 644   # file permissions
```

Copy all the files in a folder into another folder.

```bash
cp -R folderA/. folderB
```

List the contents of a folder or of a specified folder.

```bash
ls
ls folderA/
```

Rename a file or folder.

```bash
mv oldname.txt newname.txt
mv oldfolder/ newfolder/
```

Remove a folder that already contains files.

```bash
rm -rf folderA/
```

Move all files from one folder to another folder. Example below demonstrates moving all the files from the Downloads folder to the Videos folder.

```bash
mv ~/Downloads/* ~/Videos
```

## Commands specific to macOS

Open a file from the macOS terminal.

```bash
open fileA.txt            # open a file in its default application
open -a safari fileA.txt  # opens with the specified application
open -R fileA.txt         # selects the file in a Finder window
```

Mount and unmount a volume on a Mac.

```bash
hdiutil attach Secure.dmg       # mount a dmg volume named "Secure.dmg"
hdiutil detach /Volumes/Secure  # unmount a volume named "Secure"
```
