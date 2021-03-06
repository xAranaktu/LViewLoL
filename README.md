# LViewLoL

### What is this
LView is a python based scripting platform for League of Legends. The engine is external that means it is not injected into leagues process. The engine is running in a separate process and reads the games state using ReadProcessMemory.

Key features of LView:
  1. Ability to create overlays and automatize gameplay using python scripts
  2. Performant ingame overlays/menus using a combination of directx, direct composition and dear imgui 
  3. Static game data available at runtime. Data is unpacked directly from the game files. Taken from https://www.communitydragon.org/ .
  4. Undetectability. Since LView reads the game state externally the ban probability is close to 0. Currently since the start of the development there is no recorded case of a ban.
  5. A rich set of premade scripts. There are a lot of already implemented and tested gameplay scripts by default in LView and more are to come. Some of these scripts: orbwalker, spell tracker, champion tracker, map awareness, minimap drawings, skillshot drawings... etc 
 

### Building

You need Visual Studio 2017 to compile this.
Dependencies:
  1. python39: dlls and includes are already in project. You need to install python 3.9 for 32bits (Make sure you check the Add to PATH checkbox in the installer: https://www.python.org/ftp/python/3.9.0/python-3.9.0.exe)
  3. aws-lambda: dlls and includes are already in project (was used for authentication)
  3. directx 11: Must install directx end user runtimes: https://www.microsoft.com/en-us/download/details.aspx?id=35 .Extract this and run dxsetup
  4. boost::python. Due to the size of the boost libraries you must compile boost::python yourself:
      1. Download boost 1.75.0 
      2. Unarchive it in LView/boost
      3. Go into LView/boost
      4. Run `bootstrap.bat`
      5. Run `b2 --with-python link=shared toolset=msvc-14.1 address-model=32 variant=release`
  5. You are done now compile the app on Release x86 (you need to compile boost::python on debug to compile on debug, which I didn't).
 ### Setup
 All LView & LView python scripts configurations reside in config.ini file. First you must set the path to the scripts folder with the following config (you can find the config.ini in LView folder):
 
  `::scriptsFolder=\<folder\>`
