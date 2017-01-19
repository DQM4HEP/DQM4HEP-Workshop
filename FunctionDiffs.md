# Functionnalities that will differs from the actual version


## Application configuration

- Importance : 5/10
- Difficulty : 8/10
- Time scale : long
- Idea : Review configuration of module application and other applications to have something centralized.
- Why ? : Improve flexibitlity for user, better maintenance, easier for deployement over multiple servers (large number of XML files spreaded).
- In details : Change all TiXmlHandle arguments in all functions with a common interface (i.e Configuration class ???) to get the settings from any data source i.e Json, XML, database. This changes will also provides a way to convert from different from one to another one and to pull configuration from the database to different file formats.
- Breaks backward compatibility ? : YES
- Status : Not started


## Remove ROOT from the framework

- Importance : 7/10
- Difficulty : 8/10
- Time scale : medium
- Idea : remove the histogram handling by ROOT and replace it by something standalone.
- Why ? To improve on serialization buffer size thus on memory/speed performances. Need to have different shifter GUI interfaces that doesn't depends on ROOT. Will allows to remove a big package dependency.
- In details : Change the DQMMonitorElement::m_pObject (actually TObject* type) with something standalone (i.e dqm4hep::MonitorObject ???). This will change the user interface for histogram/graph/etc filling. After this (big !) change, the vizualisation will be replace by a pure Qt GUI interface with an external package as drawing frontend. This change will also trigger a refactoring of the viz interface to have a generic backend (multiple collector connections managment, monitor element storage, generic widget backend) and different front end (Qt , Web interface using Wt, something else ?). By doing so, the monitor element streaming can controlled and will the possiblity to serialize and send only what was updated after the last sending. This will again reduce the buffer size of the streamed monitor element and improve performances.
- Breaks backward compatibility ? : YES
- Status : Not started


## Cycle structure refactoring

- Importance : 6/10
- Difficulty : 3/10
- Time scale : medium
- Idea : refactor the cycle structure in module applications allowing to use multiple cycles within a module
- In details : For the moment : one cycle per module. At the end this cycle all monitor elements are sent to collector. Forseen feature : multiple cycle per module. Each monitor element refeer to a cycle. Each cycle runs independently. At the end of a cycle, the assigned monitor elements are sent to the collector.
- Why ? : By doing so, some of the monitor elements can sent more frequently than other, allowing more flexibility for the user. Possiblity to keep only one cycle for a module by defining a default cycle .
- Breaks backward compatibility ? : YES
- Status : not started yet


## Add a GUI application to monitor the framework performances

- Importance : 9/10
- Difficulty : 5/10
- Time scale : short
- Idea : Build a GUI application (whether GUI desktop or Web page) to monitor the different DQM4HEP application performances.
- Why ? : Need for a shifter to understand what's going on in the framework for a given experiment deployement.
- In details : Needs to add a service for each application we want to monitor. Exmple : A service implemented in the event collector that provides statistics on the collected event rate, event size, etc ...
- Breaks backward compatibility ? : NO
- Status : Not started yet


## Refactoring of the networking layer

- Importance : 8/10
- Difficulty : 2/10
- Time scale : very short
- Idea : put all specific networking stuff in a dedicated package.
- Why ? : improve flexibility
- Breaks backward compatibility ? : NO
- Status : Almost finished. Needs integration in all packages


## Refactor the run control part

- Importance : 8/10
- Difficulty : 2/10
- Time scale : short
- Idea : build a run control server with the following features :
  - Standalone application (as the current one)
  - A unique and fixed service interface to provide run control signal and information (to do)
  - A flexible client interface (using plugins) to receive the external (DAQ) run control signals and information. Can imagine : a http client interface, a built-in (dqm4hep-net) interface, a EUDAQ interface, etc ...
- Why ? : Allow more flexibility to real experiment deployement to couple to their own DAQ run control. This improves the flexibility and maintenance of DQM4HEP
- Breaks backward compatibility ? : YES (I suppose ?)
- Status : not started yet


## Changing job control software

- Importance : 9/10
- Difficulty : 7/10
- Time scale : medium
- Idea : Change the job control software
- In details : The current job control software is not secured. Any user can start a dangerous process from a client interface. Need to add a login feature to handle different users within the same deployement. This will secure a bit more the system. The new software will by procctrl (https://github.com/rete/procctrl) which is under developpment.
- Breaks backward compatibility ? : YES (I suppose ?)
- Status : started


## Externalize plugin system

- Importance : 7/10
- Difficulty : 5/10
- Time scale : short
- Idea : Remove the DQM4HEP plugin system and replace it by an external package
- In details : the DQM4HEP plugin system is generic enough to be pushed in an external standalone package. A project as been started (plugee : https://github.com/rete/plugee) to implement this. We will try to provide a debian package for an easy and fast installation.
- Breaks backward compatibility ? : YES, if user uses the plugin system himself in his code
- Status : started


## Package refactoring

- Importance : 7/10
- Difficulty : 2/10
- Time scale : continus ...
- Idea : split existing packages in more partitioned packages
- In details : split and rename DQMCore (-> dqm4hep-core). Split to have only basic interfaces in dqm4hep-core, network inmplementation in dqm4hep-net, core applications in dqm4hep-core-application (not sure about this ... should maybe stay in dqm4hep-core). Rename all clases from DQMClass to Class. Add a new packages dqm4hep-analysis-tools with helper classes dedicated for analysis modules. DQMViz split into many packages, each for a specific application (dqm4hep-monitoring-backend, dqm4hep-monitoring-qt, dqm4hep-monitoring-web, etc ...). DQM4ILC split into dqm4hep-lcio-streamer (only the lcio streamer), dqm4hep-ilc-tools for lcio specific analysis, dqm4hep-marlin-tools for Marlin specific tools only
- Why ? : Most of these packages depends on external dependencies. By spliting these packages into many, user can decide, depending on which software is available on his computer, to install some of them.
- Breaks backward compatibility ? : YES
- Status : started


## Online event display (additional feature)

- Importance : 2/10
- Difficulty : 8/10
- Time scale : very long
- Idea : Use the DQM4HEP feature to display raw data using an external event display like DD4Hep event display, ROOT TEve dispaly, VTK tools, etc ... Add support for different front end display, different geometry format (gdml, dd4hep, gear, etc ...). Provide a common interface to convert raw data to intepretable event display (Hit, Track, Markers, Text, etc ...) and perform conversions internally to fit the choosen front display.
- Breaks backward compatibility ? : NO
- Status : Not started yet


## Write documentation

- Importance : 9/10
- Difficulty : 5/10
- Time scale : medium (We expect ...)
- Idea : Write developper, user and shifter documentation. Can be achived after all important steps done
- Status : started
