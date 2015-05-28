# Start a New Project

The following 2 sections will guide you on how to quickly create a new
project with [maven](http://maven.apache.org/) and
[m2e](http://eclipse.org/m2e/), an eclipse plugin for maven and run the
project with jetty. For those readers who don't use Maven, please refer
to [ZK Installation Guide/Quick
Start](http://books.zkoss.org/wiki/ZK_Installation_Guide/Quick_Start). If you want to
know how to build the application with ZK first, please skip these two
sections and start from [ Declaring Domain
Class](../declaring_domain_class/README.md).

## Maven

Create a new project with maven command is quick and doesn't need any
IDE. We assume readers have basic understandings for maven, so we won't
cover maven concepts here. If you are unfamiliar with maven, please take
some time to read tutorials, like [Maven
Tutorial](http://www.tutorialspoint.com/maven/) or [Maven in 5
Minutes](http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
before commencing.

The [archetype](http://maven.apache.org/archetype/index.html) is a maven
project template tool. It can help you quickly create a project with
predefined configurations and dependencies. You can use the command
below to generate a project with ZK provided archetypes:

`mvn archetype:generate -DarchetypeCatalog=`[`http://mavensync.zkoss.org/maven2/`](http://mavensync.zkoss.org/maven2/)

Then follow the instructions described in [Use the command line version of Maven to create a
project](http://books.zkoss.org/wiki/ZK_Installation_Guide/Quick_Start/Create_and_Run_Your_First_ZK_Application_with_Eclipse_and_Maven#Use_the_command_line_version_of_Maven_to_create_a_project)
to complete the creation and run the application.


## Eclipse M2E Plugin

You need to install Eclipse and m2e plugin and setup the maven catalog,
please follow the instructions described here [ZK Installation
Guide/Quick Start/Create and Run Your First ZK Application with Eclipse
and Maven\#Prepare
Eclipse](ZK Installation Guide/Quick Start/Create and Run Your First ZK Application with Eclipse and Maven#Prepare_Eclipse "wikilink").

Then you can create a new project with ZK archetype and run it in
eclipse, please refer to [ Create a Hello World Application with ZK
Maven
Archetype](http://books.zkoss.org/wiki/ZK_Installation_Guide/Quick_Start/Create_and_Run_Your_First_ZK_Application_with_Eclipse_and_Maven#Create_a_.22Hello_World.22_application_with_ZK_Maven_Archetype).
