# GSoC 2017 final report:
## appleseed: Python scripting feature
### Original proposal
[Python scripting feature for appleseed.studio](Proposal.md)
### Brief results
* All goals have been met
* Over 30 pull requests were merged
* Got experience with
  * Contributing to open-source product
  * Remote work
  * Development of C++ project with large codebase
  * Frameworks: Qt and PyQt, Boost and Boost.Python in particular
### Pre-GSoC work:
https://github.com/appleseedhq/appleseed/wiki/List-of-Project-Ideas-for-GSoC-2017#project-3-single-file-zip-based-project-archives

After first contact with appleseed I fixed some bugs and implemented a small project to get familiar with people, codebase and workflow in organization. Project was to implement packaging appleseed projects to zip-based containers with _appleseedz_ format.

appleseed project is consisted of main _appleseed_ file and dependencies like textures. In _appleseed_ file all paths to dependencies are listed. Previously you would need to keep original project structure or manually change paths in _appleseed_ file to be able to open projet shared by another user. With _applessedz_ projects users can easily share their scenes because all files are stored in the archive and project structure will always be the same.

During this project I designed and implemented zip-based project format called _appleseedz_ and added ability to natively read and write _appleseedz_ format in all appleseed components.

#### List of merged pull requests (key pull requests are in bold):
* [#1283 Explicitly set C default library locale](https://github.com/appleseedhq/appleseed/pull/1283)
* [**#1300 Open packed project**](https://github.com/appleseedhq/appleseed/pull/1300)
* [#1306 FIX: bug when valid packed project doesn't open](https://github.com/appleseedhq/appleseed/pull/1306)
* [#1311 Add tests for unzipper and packed project](https://github.com/appleseedhq/appleseed/pull/1311)
* [#1316 Packed project minor issues](https://github.com/appleseedhq/appleseed/pull/1316)
* [#1320 Restore accidentally deleted parentheses](https://github.com/appleseedhq/appleseed/pull/1320)
* [#1336 Implemented ability to open packed projects in studio](https://github.com/appleseedhq/appleseed/pull/1336)
* [#1343 Usability changes for opening packed projects](https://github.com/appleseedhq/appleseed/pull/1343)
* [**#1345 Save packed project feature**](https://github.com/appleseedhq/appleseed/pull/1345)
* [#1353 Enhancements for packed projects](https://github.com/appleseedhq/appleseed/pull/1353)
* [#1357 Add "Pack Project As..." button to menu](https://github.com/appleseedhq/appleseed/pull/1357)
* [#1373 FIX: Change delimiter ';' on ' ' in QT file dialog filters](https://github.com/appleseedhq/appleseed/pull/1373)
* [**#1396 Implement using of packed projects as archive projects**](https://github.com/appleseedhq/appleseed/pull/1396)
* [#1404 FIX: Changed "Pack as..." button behavior](https://github.com/appleseedhq/appleseed/pull/1404)
* [#1425 Change relative search path on absolute one](https://github.com/appleseedhq/appleseed/pull/1425)

### GSoC work
https://github.com/appleseedhq/appleseed/wiki/List-of-Project-Ideas-for-GSoC-2017#project-14-python-scripting

My summer project was to implement and explore possible use cases of Python scripting for appleseed.studio. appleseed.studio is a GUI for appleseed renderer that allows to inspect, modify and render scenes. Python scripting is a useful feature for applications like appleseed.studio as it allows to automate repetetive actions, speed up development and expand functionality with user plugins.

As appleseed is written in C++ it was necessary to provide Python bindings for its functionality. There already were bindings for core functionality and my goal was to add bindings for studio-specific functionality like GUI project management and direct acces to GUI Qt classes. To provide bindings I implemented new Python module containing studio-specific functions using Boost.Python library. To keep the code clean this part required quite a lot of refactoring.

To use Python binding we should be able execute code inside appleseed.studio. To achieve this I integrated Python interpreter inside appleseed.studio. This part also required to change cmake configuration.

Python console widget was implemented to provide ability to write and modify Python scripts. With all its features: code highlighting, autoindentation, file management and others - I wrote a decent amount of new code to appleseed.studio and intensively used Qt framework.

With all this done, it become possible to make use of appleseed functionality exposed to Python. Next step was to let users expand functionality. It was achieved with plugins. Plugin is just a Python module with _register_ function placed in a specific directory. To give an example of how plugins can be written, I created a plugin that converts all textures in project to _tx_ format that is more effective than simple _png_ or _jpeg_ for rendering purposes. This plugin basically sums up all the work: it retrieves Qt classes to add menu to main window of applessed.studio, uses studio-specific and core appleseed bindings to replace old textures with converted ones and registers automatically with implemented plugin system.

During all development we with mentors discussed project daily. It had a huge influence on the process because they could guide me during implementation of every feature what made development process very productive. Also code was merged to master often giving whole community an ability to try new features, so I was receiving priceless feedback often and early. Thanks to many disucssions prior to GSoC and thoroughful planning of timeline all goals were met and new functionality is ready to use.

### Screenshots
![Studio Gaffer Browser](studio_gaffer_browser.png)

#### List of merged pull requests (key pull requests are in bold):
* [**#1440 Python console**](https://github.com/appleseedhq/appleseed/pull/1440)
* [**#1454 Console adjustments**](https://github.com/appleseedhq/appleseed/pull/1454)
* [**#1464 Studio python module**](https://github.com/appleseedhq/appleseed/pull/1464)
* [#1493 Python console refactoring](https://github.com/appleseedhq/appleseed/pull/1493)
* [#1498 Fix regression](https://github.com/appleseedhq/appleseed/pull/1498)
* [#1509 Python console issues](https://github.com/appleseedhq/appleseed/pull/1509)
* [#1513 Python console minor issues](https://github.com/appleseedhq/appleseed/pull/1513)
* [#1537 Python console usability work](https://github.com/appleseedhq/appleseed/pull/1537)
* [#1546 Add appleseed.studio to Travis build](https://github.com/appleseedhq/appleseed/pull/1546)
* [#1554 Studio python bugfixes](https://github.com/appleseedhq/appleseed/pull/1554)
* [#1558 appleseed.studio module enhancements](https://github.com/appleseedhq/appleseed/pull/1558)
* [**#1569 Implemented studio.add_dock function**](https://github.com/appleseedhq/appleseed/pull/1569)
* [#1572 Python modules improvements](https://github.com/appleseedhq/appleseed/pull/1572)
* [#1578 appleseed.studio python module improvements](https://github.com/appleseedhq/appleseed/pull/1578)
* [**#1582 General texture converter implementation and function to use it in appleseed.studio**](https://github.com/appleseedhq/appleseed/pull/1582)
* [#1587 New UI helper and fixes for Python interpreter](https://github.com/appleseedhq/appleseed/pull/1587)
* [**#1599 Studio python plugins**](https://github.com/appleseedhq/appleseed/pull/1599)
* [#1606 Different fixes](https://github.com/appleseedhq/appleseed/pull/1606)
