# debian-firefox-dev-updater
Install Firefox Developer Edition alongside the default firefox ESR on Debian and update it with a simple bash script coupled with a bash alias.

## Instalation
Make sure the *wget* dependencie is installed on your machine. Log yourself using your root password first.
```
$ su -
$ apt update && apt install wget
```

Clone or download this repo.

Copy the ffdeved-updater to the local sbin folder as root
```
$ su - -c "cp /path/to/ffdeved-updater /usr/local/sbin"
```
Make an alias into your user .bash_aliases file
```
touch .bash_aliases
echo 'alias ffdevupdate="su - -c ffdeved-updater"' >> .bashrc_aliases
```
If you use something else like zsh put it in your .zshrc or whatever alias file you use. I have setup mine to be called .aliases and shared beetween bash, zsh & others.

Restart your terminal or source the file for immediate effect.
```
$ source ~/.bashrc
```
Replace with .zshrc if you use zsh.

Run the program to download and install firefox.
```
$ ffdevupdate
```
Firefox Developer Edition is now installed on your machine.

Make a symbolic link of the Firefox Developer Edition binary into the `/usr/local/bin` directory.
```
$ ln -s /usr/local/src/firefox/firefox /usr/local/bin/firefox-dev
```
You should now be able to start Firefox Developer Edition from the command line using the command `firefox-dev`.

Add Firefox Dev Edition to your desktop environement (use root).
```
$ su - -c "cp /path/to/firefox-dev-edition.desktop /usr/share/applications/firefox-dev-edition.desktop"
```
Verify that Firefox Developer Edition is now installed and listed in your Desktop Environement alongside the default Firefox ESR.

## Usage
Whenever Firefox Developer Edition warns you about an update use your alias command as a regular user to update. Don't forget your root password !
```
$ ffdevupdate
```
Bonus trick: type `ff` press tab and enter to update Firefox like the hackerman you are.

## How it works
Go into the `/usr/local/src` directory by default to Download the [latest Firefox Dev Edition build](https://download.mozilla.org/?product=firefox-devedition-latest-ssl&os=linux64&lang=en-US) with *wget* and name it *firefoxdev-latest.tar.bz2*. Finally Decompress the archive with tar in a folder called firefox.

## Update this updater
Git pull and move the file again to the local sbin folder again. If you download the repo without git check here from times to times if this code as been updated

```
$ su - && cp /path/to/ffdeved-updater /usr/local/sbin
```
