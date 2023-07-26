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

> ```$ sudo xcode-select --install```

> ```$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"```

>```echo 'PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile```
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

Preferences -> Profiles -> Text - set ***Source Code Pro*** font; size 13; blinking cursor\
Preferences -> Profiles -> Window - set transparency and blur\
Preferences -> Profiles -> Colors - set colors

12. tree

>```brew install tree```

13. Git

>```brew install git```\
>```git config --global user.name "Your Name Here"```\
>```git config --global user.email "your_email@youremail.com"```

14. MidnightCommander

>```brew install mc```

15. Bash Completion

>```brew install bash-completion```

>```echo "[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion" >> ~/.bash_profile```

>```source ~/.bash_profile```

16. Karabiner Elements

https://karabiner-elements.pqrs.org/

Make sure to select correct version based on MacOS

Security & Privacy -> General:\
Allow - System software froim application...

Security & Privacy -> Privacy -> Input Monitoring:\
[X] Karabiner_grabber\
[X] Karabiner_observer

Set:
- left_control <-> left_command
- left_command <-> left_control
- right_command <-> right option
- right option <-> right_command

Menu ***Misc*** - uncheck [ ] Check for updates on startup

17. Sublime Text

>```brew install --cask sublime-text```

18. Visual Studio Code

>```brew install --cask visual-studio-code```

19. Python

Download installer from main website

https://www.python.org/downloads/

install PIP:

>```curl https://bootstrap.pypa.io/get-pip.py > get-pip.py```

>```sudo python get-pip.py```

20 Anaconda

https://www.anaconda.com/download

21. LaTex

https://tug.org/mactex/

22. VisualStudio Code extensions:

- PlatformIO
- LaTeX-Workshop
- C/C++
- CodeRunner
- IntelliCode
- Pretier
- Pylance
- Python

23. Serial 2

This is highly recommended terminal app to work with UART-USB dongles

https://www.decisivetactics.com/

24. Opera

>```brew install --cask opera```

25. Folx - torrent client

https://www.mac-downloader.com/

26. LibreOffice

https://www.libreoffice.org/download/download-libreoffice/

27. GIMP

https://www.gimp.org/downloads/

28. AVR development 

* install Arduino IDE 2.x - https://www.arduino.cc/en/software and run\
create blank project for any standard arduino board - software will offer to install AVR Boards Core - accept it\
this will install: 
  - AVR-GCC
  - avrdude
  
* Install ***Eclipse IDE for C/C++ Developers*** https://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/2023-06/R/eclipse-cpp-2023-06-R-macosx-cocoa-x86_64.dmg

* Install ***Darkest Dark Theme with DevStyle*** - it adds few nice functions ex. better workspace 

* Install ***AVR Eclipse Plugin***

* Make some adjustments if Eclipse will be used only for AVR development:
  - LAUNCHBAR - disable
  - SPELLING - disable
  - AUTO SAVE - enable ***Save Automatically before manual build***

* Set ***paths*** in AVR Plugin:
  - AVR-GCC			-> /Users/**user**/Library/Arduino15/packages/arduino/tools/avr-gcc/7.3.0-atmel3.6.1-arduino7/bin
  - GNU make 	 	-> \usr\bin
  - AVR Header Files 	-> /Users/**user**/Library/Arduino15/packages/arduino/tools/avr-gcc/7.3.0-atmel3.6.1-arduino7/avr/include
  - AVRDude			-> /Users/**user**/Library/Arduino15/packages/arduino/tools/avrdude/6.3.0-arduino17/bin
  - AVRDude config file -> /Users/**user**/Library/Arduino15/packages/arduino/tools/avrdude/6.3.0-arduino17/etc/avrdude.conf

9. CubicSDR

>```brew install cubicsdr```

