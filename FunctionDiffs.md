## Functionnalities that will differs from the actual version :

# Application configuration

- Idea : Review configuration of module application and other applications to have something centralized.
- Why ? : Improve flexibitlity for user, better maintenance, easier for deployement over multiple servers (large number of XML files spreaded).
- In details : Change all TiXmlHandle arguments in all functions with a common interface (i.e Configuration class ???) to get the settings from any data source i.e Json, XML, database. This changes will also provides a way to convert from different from one to another one and to pull configuration from the database to different file formats.
- Breaks backward compatibility ? : YES

# Remove ROOT from the framework

- Idea : remove the histogram handling by ROOT and replace it by something standalone.
- Why ? To improve on serialization buffer size thus on memory/speed performances. Need to have different shifter GUI interfaces that doesn't depends on ROOT. Will allows to remove a big package dependency.
- In details : Change the DQMMonitorElement::m_pObject (actually TObject* type) with something standalone (i.e dqm4hep::MonitorObject ???). This will change the user interface for histogram/graph/etc filling. After this (big !) change, the vizualisation will be replace by a pure Qt GUI interface with an external package as drawing frontend. This change will also trigger a refactoring of the viz interface to have a generic backend (multiple collector connections managment, monitor element storage, generic widget backend) and different front end (Qt , Web interface using Wt, something else ?).
- Breaks backward compatibility ? : YES

# Add a GUI application to monitor the framework performances   
- Idea : Build a GUI application (whether GUI desktop or Web page) to monitor the different DQM4HEP application performances.
- Why ? : Need for a shifter to understand what's going on in the framework for a given experiment deployement.
- In details : Needs to add a service for each application we want to monitor. Exmple : A service implemented in the event collector that provides statistics on the collected event rate, event size, etc ...
- Breaks backward compatibility ? : NO

<!-- # Refactoring of the networking layer

- Idea : put all specific networking stuff in a dedicated package.
- Why ?  -->
