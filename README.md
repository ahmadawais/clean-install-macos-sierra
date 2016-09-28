# Clean Install macOS Sierra

If you like to follow these instructions keep in mind that you need to use your own information (like username and folder locations).


---

## Install macOS Sierra :

#### On Old Mac :

- [Download macOS Sierra](https://itunes.apple.com/tr/app/macos-sierra/id1127487414?mt=12)
- Format USB (min 8GB):
    - Open **Disk Utility**
    - Click **Erase**
    - Select **OS X Extended (Journaled)**
    - Rename USB to **Untitled**
- To Create a OS X bootable USB disk enter this command to your terminal:

```
sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ macOS\ Sierra.app --nointeraction
```   

#### Backup
Backup Your files to Dropbox  
Dont' forget to backup your ssh keys  :  
e.g.

```
cp -R ~/.ssh ~/Dropbox/
```


#### On New Mac :

> ***YOU ARE GOING TO DELETE EVERYTHING ON YOUR MAC IN THE NEXT STEP !!!***  
> Write down the next 4 steps. You won't be able to to open your Mac untill OSX is installed.

1. Restart & hold down the Option **⌥ alt** key
2. Choose **Install OS X Sierra**
3. Select **Disk Utility** from the menu and **erase** you main HDD
4. Go back to the main menu; select **Install OS X** and choose your HDD when prompted

Continue installation with your credentials

---
## Personal Environment & Apps  
---


Change the default Gatekeeper behavior to run apps downloaded from anywhere

    sudo spctl --master-disable

### 1. Install [Homebrew](http://brew.sh/) :

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    # Homebrew asks for xcode tools

    # check for errors
    brew doctor

---

### 2. Install vital Brew Packages

    brew install git coreutils bash-completion tree readline wget python openssl jpeg libpng mysql nvm npm stormssh homebrew/completions/stormssh-completion

---

### 3. Install Bower & Gulp

    npm install -g bower
    npm install --save gulp-install


### 4. Install [Homebrew Cask](http://caskroom.io/) :

    brew tap caskroom/cask

#### add to `.bashrc` :

    export HOMEBREW_CASK_OPTS="--appdir=/Applications"

#### Install Dropbox to restore backups and symlinks
A full list of Apps to install will follow. 

    brew cask install dropbox

---
### 5. Restore your files from Dropbox  
[Copy files manually](https://www.dropbox.com/en/help/1941)
- The application will create a Dropbox folder and begin downloading files from your account. Stop the download immediately by clicking the Dropbox icon in your menu bar, clicking the gear icon, and selecting ***Pause Syncing*** from the menu.
- Copy the files from your portable drive into the Dropbox folder. The default location of the folder on your Mac is /Users/yourUserName/Dropbox (such as /Users/Robert/Dropbox).
- Resume syncing by clicking the Dropbox icon in your menu bar, clicking the gear icon, and selecting ***Resume Syncing*** from the menu.

---
### 6. Install [Dotfiles](https://github.com/tarikkavaz/dotfiles-universal#installation) :

#### Clone the Repo :

    cd
    git clone https://github.com/tarikkavaz/dotfiles-universal.git Dotfiles

#### Symlink files :

    ln -s $HOME/Dotfiles/profile ~/.profile
    ln -s $HOME/Dotfiles/rc/bashrc ~/.bashrc
    ln -s $HOME/Dotfiles/rc/inputrc ~/.inputrc

    # for custom functions, env, aliases etc...
    ln -s ~/Dropbox/Dotfiles/private $HOME/Dotfiles/private     

restart terminal.

---

### 7. Install Python Environment :

    cd
    pip install virtualenv
    pip install virtualenvwrapper

---

### 8. Install Ruby :

    cd
    git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
    git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

        restart terminal.

#### set ruby 2.2.2 :

    CONFIGURE_OPTS="--with-readline-dir=$(brew --prefix readline)" rbenv install 2.2.2
    rbenv global 2.2.2
    rbenv rehash

---

### 9. Install pry & bundler :

    gem install pry pry-doc bundler

---

### 10. Backup SSH

backup your ssh folder from dropbox  

    mkdir ~/.ssh
then  

    ln -s ~/Dropbox/Dotfiles/configs/ssh_config ~/.ssh/config


---

### 11. git aliases & settings :

    ln -s ~/Dropbox/Dotfiles/configs/gitconfig ~/.gitconfig
    ln -s ~/Dropbox/Dotfiles/configs/gitignore_global ~/.gitignore_global

    # example config options
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.st status
    git config --global user.name "Tarik Kavaz"
    git config --global user.email tarikkavaz@gmail.com

---

### 12. Install Apps :


#### From Web / Brew Cask
    brew cask install atom appcleaner bartender blisk clipmenu google-chrome codekit commander-one goofy iterm2 padbury-clock phoneclean qlmarkdown screens-connect skype spotify textmate transmit tripmode vlc virtualbox whatsapp zenmate-vpn

- [Atom](https://atom.io/download/mac)
- [Appcleaner](https://freemacsoft.net/appcleaner/)
- [Bartender 2](https://www.macbartender.com/) *
- [Blisk](https://blisk.io/)
- [Chrome](https://www.google.com/chrome/browser/desktop/)
- [ClipMenu](http://www.clipmenu.com/)
- [CodeKit](https://incident57.com/codekit/) *
- [Commander One](http://mac.eltima.com/file-manager.html) *
- [Dropbox](https://www.dropbox.com/downloading?os=mac) 
- [Goofy Facebook Messenger](http://www.goofyapp.com/)
- [iTerm2](https://www.iterm2.com/downloads.html)
- [Padbury Clock](http://padbury.me/clock/)
- [PhoneClean](http://www.imobie.com/phoneclean/)
- [QuickLook Markdown](https://github.com/toland/qlmarkdown/)
- [Screens Connect](http://edovia.com/screensconnect/download/)
- [Skype](http://www.skype.com/en/download-skype/skype-for-mac/downloading/)
- [Spotify](https://www.spotify.com/us/download/)
- [TextMate](https://macromates.com/download) *
- [Transmit](https://panic.com/transmit/) *
- [TripMode](https://www.tripmode.ch) *
- [VLC](http://www.videolan.org/vlc/index.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Virtual Machines](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/mac/)
- [WhatsApp Messenger](https://www.whatsapp.com/download/)
- [ZenMate](https://secure.zenmate.com/)

`* needs Registration`  

#### From App Store
- [1Password](https://1password.com/)
- [Airmail 3](http://airmailapp.com/)
- [Keynote](http://www.apple.com/mac/keynote/)
- [Moom](https://manytricks.com/moom/)
- [Numbers](http://www.apple.com/mac/numbers/)
- [Pages](http://www.apple.com/mac/pages/)
- [Pixelmator](http://www.pixelmator.com/mac/)
- [Screens](http://edovia.com/screens/)
- [Sip](http://sipapp.io/)
- [Slack](https://slack.com/)
- [Telegram](https://telegram.org/)
- [TweetDeck](https://tweetdeck.twitter.com/)
- [The Unarchiver](http://unarchiver.c3.cx/unarchiver)
- [Unclutter](http://unclutterapp.com/)
- [Wunderlist](https://www.wunderlist.com/)

#### Themes

- [Solarized color palette](http://ethanschoonover.com/solarized)  
- [iTerm themes](http://iterm2colorschemes.com/)


