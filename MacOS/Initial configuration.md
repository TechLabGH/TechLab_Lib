1. Hide all Applications from dock

2. Adjust Dock size and magnification

3. Dock Preferences -> [ ] Show recent applicztions in Dock

4. Users and Groups -> Login Options -> set automatic login for main user

5. Security & Privacy -> General -> [ ] Require password ...

6. iCloud: 
    [X] iCloud Drive -> Options -> [X] Desktop & Documents Folders\
    [X] Find My Mac\
    disable sync for all other Applicztions and folders

7. TrackPpad -> [X] Tap to click

8. Finder:
   - list view
   - Command + Shitf + . - displays hidden files
   - View -> Show Path Bar
   - Preferences -> General -> [X] Hard disks\
     Preferences -> General -> [X] Connected servers\
     Preferences -> General -> New Finder windows show -> Home folder\
     Preferences -> Sidebar -> Enable all but Recent Tags\
     Preferences -> Advanced -> [X] Show all filename extensions\

   - Show View Options in Home folder:\
     [X] Calculate all sizes\
     [X] Show Library folder\
     [X] Always open in list view

     [Use as Default]

9. Install from AppStore:
- Commander One
- LanScan
- PortX
- ImageOne
- Smart ISO Burner Pro
- VOX (Dont allow notifications)
- SyncFolder Pro
- Microsoft Remote Desktop

10. Install HomeBrew\

> ```$ sudo xcode-select --install```\

> ```$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"```\

>```echo 'PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile```\
---
#### HomeBrew

To install a package (or Formula in Homebrew vocabulary) simply type:

>```brew install <formula>```

To update Homebrew's directory of formulae, run:

>```brew update```

Note: If that command fails you can manually download the directory of formulas like this:

>```cd /usr/local/Homebrew/```\
>```git fetch origin```\
>```git reset --hard origin/master```

To see if any of your formulas need to be updated:

>```brew outdated```

To update a formula:

>```brew upgrade <formula>```

Homebrew keeps older versions of formulas installed on your system, in case you want to roll back to an older version. That is rarely necessary, so you can do some cleanup to get rid of those old versions:

>```brew cleanup```

If you want to see what formulae Homebrew would delete without actually deleting them, you can run:

>```brew cleanup --dry-run```

To see what you have installed (with their version numbers):

>```brew list --versions```

To search for formulas you run:

>```brew search <formula>```

To get more information about a formula you run:

>```brew info <formula>```

To uninstall a formula you can run:

>```brew uninstall <formula>```

---

11. iTerm2

>```brew install --cask iterm2```

>```brew tap homebrew/cask-fonts```\
>```brew install --cask font-source-code-pro```

12. tree

>```brew install tree```

13. Git

>```brew install git```\
>```git config --global user.name "Your Name Here"```\
>```git config --global user.email "your_email@youremail.com"```

