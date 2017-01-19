# DQM4HEP Hands-On Session

This will be an introduction to using DQM4HEP as an online monitoring tool for testbeams. The session will cover the basic structure of the framework, dependencies and installation, running the framework, writing analysis modules for online monitoring, and upcoming changes by the developers.

## Main Topics

* Basics
  * Introduction to the program, its purpose, and development.
  * DQM4HEP within the AIDA-2020 programme, as part of Common DAQ (WP5).
  * Only on Unix (does not compile on Windows).
* Structure
  * Core (i.e. language, version, compilers, build tool, dependencies, etc.)
  * Names and functions of all major components.
* Installation
  * Downloading sourcecode from Github.
  * Configuring installation.
  * Running installation scripts.
  * Installing "stripped-down" ilcsoft
* Running
  * Setup before running -- setting environment variables, etc.
  * Steering files for naming and running all processes.
  * Manual running -- each command and it's arguments, plus running via bash scripts.
  * Running with the job control using JSON files.
* Analysis modules
  * Blow-by-blow of each member function, it's purpose, and how one would modify it to change the file.
  * Writing steering files for analysis modules
  * With examples -- start with a "template" analysis module, then have each step outlined in a powerpoint to show the additions and why they were made.
* Standalone modules
  * Similar to analysis modules, excpet that data comes from a different source.
  * Uses: slow control, [...]
* Development status and coming changes
  * Current features not represented in tutorial build.
  * Final features.
  * Online monitoring interface with EUDAQ as part of AIDA-2020.
