# GSoC 2017 final report:
## Appleseed: Python scripting feature
### Original proposal
[Python scripting feature for appleseed.studio](Proposal.md)
### Pre-GSoC work:
https://github.com/appleseedhq/appleseed/wiki/List-of-Project-Ideas-for-GSoC-2017#project-3-single-file-zip-based-project-archives

After first contact with appleseed I fixed some bugs and implemented a small project to get familiar with people, codebase and workflow in organization. Project was to implement packaging appleseed projects to zip-based containers with _appleseedz_ format.

Appleseed project is consisted of main _appleseed_ file and dependencies like textures. In _appleseed_ file all paths to dependencies are listed. Previously you would need to keep original project structure or manually change paths in _appleseed_ file to be able to open projet shared by another user. With _applessedz_ projects users can easily share their scenes because all files are stored in the archive and project structure will always be the same.

During this project I designed and implemented zip-based project format called _appleseedz_ and added ability to natively read and write _appleseedz_ format in all appleseed components.

#### List of merged pull requests:
* https://github.com/appleseedhq/appleseed/pull/1283
* https://github.com/appleseedhq/appleseed/pull/1300
* https://github.com/appleseedhq/appleseed/pull/1306
* https://github.com/appleseedhq/appleseed/pull/1311
* https://github.com/appleseedhq/appleseed/pull/1316
* https://github.com/appleseedhq/appleseed/pull/1320
* https://github.com/appleseedhq/appleseed/pull/1336
* https://github.com/appleseedhq/appleseed/pull/1343
* https://github.com/appleseedhq/appleseed/pull/1345
* https://github.com/appleseedhq/appleseed/pull/1353
* https://github.com/appleseedhq/appleseed/pull/1357
* https://github.com/appleseedhq/appleseed/pull/1373
* https://github.com/appleseedhq/appleseed/pull/1396
* https://github.com/appleseedhq/appleseed/pull/1404
* https://github.com/appleseedhq/appleseed/pull/1425

### GSoC work
https://github.com/appleseedhq/appleseed/wiki/List-of-Project-Ideas-for-GSoC-2017#project-14-python-scripting

My summer project was to implement and explore possible use cases of Python scripting for appleseed.studio. Appleseed.studio is a GUI for appleseed renderer that allows to inspect, modify and render scenes. Python scripting is a useful feature for applications like appleseed.studio as it allows to automate repetetive actions, speed up development and expand functionality with user plugins.

As Appleseed is written in C++ it was necessary to provide Python bindings for its functionality. There already were bindings for core functionality and my goal was to add bindings for studio-specific functionality like GUI project management and direct acces to GUI Qt classes. To provide bindings I implemented new Python module containing studio-specific functions using Boost.Python library. To keep the code clean this part required quite a lot of refactoring.

To use Python binding we should be able execute code inside appleseed.studio. To achieve this I integrated Python interpreter inside appleseed.studio. This part also required to change cmake configuration.

Python console widget was implemented to provide ability to write and modify Python scripts. With all its features: code highlighting, autoindentation, file management and others - I wrote a decent amount of new code to appleseed.studio and intensively used Qt framework.

With all this done, it become possible to make use of appleseed functionality exposed to Python. Next step was to let users expand functionality. It was achieved with plugins. Plugin is just a Python module with _register_ function placed in a specific directory. To give an example of how plugins can be written, I created a plugin that converts all textures in project to _tx_ format that is more effective than simple _png_ or _jpeg_ for rendering purposes. This plugin basically sums up all the work: it retrieves Qt classes to add menu to main window of applessed.studio, uses studio-specific and core appleseed bindings to replace old textures with converted ones and registers automatically with implemented plugin system.

During all development we with mentors discussed project daily. It had a huge influence on the process because they could guide me during implementation of every feature what made development process very productive. Also code was merged to master often giving whole community an ability to try new features, so I was receiving priceless feedback often and early. Thanks to many disucssions prior to GSoC and thoroughful planning of timeline all goals were met and new functionality is ready to use.

#### List of merged pull requests:
* https://github.com/appleseedhq/appleseed/pull/1440
* https://github.com/appleseedhq/appleseed/pull/1454
* https://github.com/appleseedhq/appleseed/pull/1464
* https://github.com/appleseedhq/appleseed/pull/1493
* https://github.com/appleseedhq/appleseed/pull/1498
* https://github.com/appleseedhq/appleseed/pull/1509
* https://github.com/appleseedhq/appleseed/pull/1513
* https://github.com/appleseedhq/appleseed/pull/1537
* https://github.com/appleseedhq/appleseed/pull/1546
* https://github.com/appleseedhq/appleseed/pull/1554
* https://github.com/appleseedhq/appleseed/pull/1558
* https://github.com/appleseedhq/appleseed/pull/1569
* https://github.com/appleseedhq/appleseed/pull/1572
* https://github.com/appleseedhq/appleseed/pull/1578
* https://github.com/appleseedhq/appleseed/pull/1582
* https://github.com/appleseedhq/appleseed/pull/1587
* https://github.com/appleseedhq/appleseed/pull/1599
