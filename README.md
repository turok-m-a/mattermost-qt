![Build status](https://github.com/nuclear868/mattermost-qt/actions/workflows/build.yaml/badge.svg)

# mattermost-qt
Mattermost native desktop client, using the QT framework

fork from abandoned [mattermost-qt](https://github.com/turok-m-a/mattermost-qt/tree/master) by nuclear868
# Motivation
* The official Mattermost desktop client is actually a javascript / typescript web application, running inside a dedicated web browser. This makes it veeery slow, it creates at least 10 processes and consumes a lot of RAM, some users also complain about high CPU usage, which makes laptop fan make excessive noise.
* A personal idea to make native client, which consumes as small resources as possible, preserving all needed features.
* Web application user interface does not provide flexibility of native GUI - i.e. you cannot open thread in a separate window (I think its possible, but its not implemented in most Electron/JS clients - MS Teams, Slack, MM), no context menus (possible, but Electron/JS developers somehow forgot about its existence).

# What does work
* threads
* viewing all available channels
* Sending and receiving messages
* visual notifications for new messages
* message editing and deleting
* Receiving attached files. Image files can be viewed in a simple viewer and other files can be downloaded or opened with default application
* Sending messages with attachments is supported too
* ~~If a reconnect occurs, the chat history is synchronized with the server, so that no messages are lost.~~ to be fixed
* Cache is used for faster image loading.
* update, when a new team is added and you are added to it
* Preview of team members, channel members, users, etc. There are more items to be added, but the basic functionality is supported
* Properly handing adding / deleting users / channels / teams. However, it has to be tested more

* loading channel history when scrolling to the beginning of a channel. (minor problem exists, workaround button for loading posts was added, until i find a way for proper fix).
* emoticons, reactions - partially broken, to be fixed.
# What is planned to be implemented (near future)
* Fix reconnect and chat history synchonization
* Hidden/archived chats - do not receive notifications from them, do not load and receive messages until selected from list.
* "TODO answer list" - mark messages as unread (or some other way), and put them on special list.
* ~~Find a better way to handle thread widnows.~~ done
* Make main window fully resizable, auto/manual option to hide chat list.
* Settings for notifications. At least option to notify only on PM and username mentioned.
* Fix new reactions not working, support for custom reactions. At least - display :reaction name: on button if icon cannot be displayed.
* Load avatars only for users that are members of channel you are connected to, plus PM list users.
* Load avatars only for posts that are currently displayed. If not possible, implement background avatar loading, so user does not need to wait for too long on first client launch.
* Try to optimize RAM usage even more (just as a challenge)
# What is planned to be implemented (at some distant future)
* pinning posts to a channel and displaying pinned posts
* adding additional settings... I want this application to be fully customizable

# What does not work, not planned to be implemented
* notifications when someone is typing and sending a notification when you are typing
* voice calls
* LAN file transfer between 2 QT Mattermost clients
* Auto-detect if you are working from home and setting it as a status. This can be achieved by looking for an active VPN connection. It will be fully configurable from the settings

# Installation
The application is developed and tested on Linux Mint. Windows support is not tested.

## Required packages (Linux)
### Ubuntu/Linux MInt
* QT5 libraries (qtbase5-dev)
* QT5 websockets library (libqt5websockets5-dev)
### Fedora
* QT5 libraries (qt5-qtbase-devel)
* QT5 websockets library (qt5-qtwebsockets-devel)

## Build instructions (Linux)
It is recommended to build in a separate directory:

```
mkdir build
cd build
cmake ..
make -j8
```

## How to build on Windows

Releases since 1.1 includes pre-built client for windows, which is expected to work on any windows installation.

If you want to build it yourself, just for fun or for any othre reason, you need the following packages
minGW - https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/installer/mingw-w64-install.exe/download
Qt5 - https://doc.qt.io/qt-5/gettingstarted.html
openSSL - https://slproweb.com/products/Win32OpenSSL.html
CMake for windows

    
## Running
from the build directory just start ./qmattermost
A login form will appear and after a successful login all teams and channels should appear
The credentials are saved (if using linux) in ~/.config/mattermost-native/Mattermost.conf (yes, they are not encrypted, I will find a cross-platform way to encrypt them. At least, since release 1.1 a login token is used instead of the password) and are
not requested again on next start (if the login is successful)

## Contribution
I am making this as a side project, mostly for fun / additional experience, so any contributions like bugfixes or any issues from the 'What is planned to be implemented' list are welcome

