# Python scripting feature for appleseed.studio

## Deliverables
* Python interpreter integrated into appleseed.studio
* C++ functions to operate on opened project
* Python bindings for above functions and related types
* Simple script editor inside appleseed.studio with ability to write, execute and see results of python scripts
* Several functions as examples of exposing appleseed.studio functionality to Python

## Community bonding period
* Learn Boost.Python and Python C bindings. Read documentation and articles, experiment with code
* Learn Qt. Try to add something related to Qt to appleseed.studio
* Investigate how to ship applessed on different platform. In particular, should Python interpreter be shipped with appleseed or already installed interpreter can be used

## Coding period timeline
This week-by-week timeline provides a rough guideline of how the project will be done
* 30 May -- 2 June  
**Integrate a Python interpreter inside appleseed.studio**  
It should be done at the very begginning as a basis for further work. Only basic integration that allows 
to run Python sripts from C++ application is needed at this stage. Important point is that this interpreter 
should have appleseed Python bindings imported from the start.  
* 5 -- 9 June   
**Implement console widget for Python interpreter**  
Console widget is where all scripts will be launched. So it's important to implement it early.   
* 12 -- 16 June  
**Implement deeper integration of Python interpreter to appleseed.studio**  
Integration made on first week only allows to execute scripts, but doesn't have ability to access data from
inside the applesee.studio (i.e. data of current project). On this stage deeper integration will be provided 
which will allow to access application data from Python scripts  
* 19 -- 23 June  
**Make sure that updated application launches on Windows, Linux and OSX**  
* 26 -- 30 June  
**Phase 1 evaluation. Finishing touches on implemented part**  
Time to update build instructions, and thoroughly test new functionality  
By the end of phase 1 two things should work:  
  1. Python integration ...  
  2. Console widget with ability to execute python scripts  
* 3 -- 7 July  
**Write C++ functions and Python bindigs to operate on current project**  
In particular, on this stage function to retrieve currently opened project should be implemented  
* 10 -- 14 July  
**Add simple script editor**  
Editor should have functionality to load, write, save and execute python scripts. Results of script 
execution should be passed to console widget implemented on 2'nd week.  
* 17 -- 21 July  
**Tests and documentation**  
 Time to write documentation on appleseed.studio-specific API and thoroughly test these API and script editor  
* 24 -- 28 July  
**Phase 2 evaluation. Finishing touches on implemented part**  
By the end of phase 2 two things should work:  
  1. appleseed.studio-specific API that allows to retrieve current project so it can be used by existing appleseed Python API  
  2. Script editor with functionality to load, write, save and execute python scripts  
* 31 July - 4 August  
**Investigate how appleseed.studio functionality can be expanded with Python**  
Understand how these expansion can be made and how flexible can it be  
* 7 -- 11 August  
**Expose a few appleseed.studio functions to Python script**  
In particular, expose ability to open project and create new project  
* 14 -- 18 August  
**Thorough testing and documenting of the whole project**  
* 21 -- 29 August  
**Pencils down. Final work product submition and evaluation**  
All results stated in deliverables part should be achieved    
Changes are made only in case of backlog or critical bugfixing  
