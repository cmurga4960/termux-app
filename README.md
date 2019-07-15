[![Travis build status](https://travis-ci.org/termux/termux-app.svg?branch=master)](https://travis-ci.org/termux/termux-app)
[![Join the chat at https://gitter.im/termux/termux](https://badges.gitter.im/termux/termux.svg)](https://gitter.im/termux/termux)


Termux CORE
==========
This project allows for developers to utalize Termux functionality while developing a new application.

Steps:

Clone https://github.com/cmurga4960/termux-app-core
Delete .git in termux-app-core
Move repo into desired location (e.g. new repo).
Open termux-app-core in android studio
Right click app/java/com.termux and select refactor - rename package
Choose a name with same length as termux
Click do refactor
(optional) Edit androidmanifest shareduserid value ???? maybe not...
(optional) Edit res/values/strings application_name value
(optional) change build.gradle values and sync
Clean and rebuild project
Switch file view to Project (instead of Android).  This will avoid confusion.
Edit the file TermuxService.java in app/src/main/java/com.ohoney/app/
Replace “com.termux” with your new name
Edit the file TermuxInstaller.java in the same dir
Add the following code to the method determineZipUrl()

        if (!TermuxService.FILES_PATH .contains("com.termux"))
        {
            url = Build.VERSION.SDK_INT >= Build.VERSION_CODES.N
                ? "http://mydomain.com/bootstrap/bootstrap1?arch=" + archName
                : "http://mydomain.com/bootstrap/bootstrap2?arch=" + archName;
        }
        Log.i(“url49",url);
Edit terminal-emulator/cpp/termux.c
Replace “com_termux” with “com_”+your name
Rebuild bootstrap
Download:
    https://termux.org/bootstrap-aarch64.zip
    https://termux.org/bootstrap-arm.zip
    https://termux.org/bootstrap-i686.zip
    https://termux.org/bootstrap-x86_64.zip
    https://termux.net/bootstrap/bootstrap-aarch64.zip
    https://termux.net/bootstrap/bootstrap-arm.zip
    https://termux.net/bootstrap/bootstrap-i686.zip
    https://termux.net/bootstrap/bootstrap-x86_64.zip
Unzip and replace “com.termux” with your name in every file (including binaries)
Zip folders and upload to a webserver the Android device can reach
Build and pray
If you get “Unable to install” for bootstrap - verify the zip can be reached 

