picketlink-authentication-http-basic: PicketLink Multi-Tennancy Example
===============================
Author: Pedro Igor
Level: Beginner
Technologies: CDI, PicketLink, JSF
Summary: Basic example that demonstrates how to use Multi-Tennancy Example using Time-based One-Time Passwords(TOTP) with a JSF view layer
Target Product: EAP
Source: <https://github.com/jboss-jdf/jboss-as-quickstart/>


What is it?
-----------

This example demonstrates the use of *CDI 1.0* and *PicketLink* in *JBoss Enterprise Application Platform 6* or *JBoss AS 7*.

This application provides a multi-tennancy architecture and security model for accessing different companies and their resources.
Each company maps to a single realm, from where resources and identity data are located and isolated from each other.
Realms have their own resources and security policies, not accessible for users of another realms.

The application provides a login page from where you can sign in to different companies. Each company has its own
directory, where its resources are located.

    src/
        main/
            webapp/
                companies/
                    acme/
                    umbrella/
                    wayne/

Users from one company/realm can not have access to the directory from another company(and their resources). This authorization
logic is provided by the org.jboss.as.quickstarts.picketlink.idm.totp.jsf.RealmProtectionFilter, which is a
simple @WebFilter.

The latest PicketLink documentation is available [here](http://docs.jboss.org/picketlink/2/latest/).


System requirements
-------------------

All you need to build this project is Java 6.0 (Java SDK 1.6) or better, Maven 3.0 or better.

The application this project produces is designed to be run on JBoss Enterprise Application Platform 6 or JBoss AS 7. 

 
Configure Maven
---------------

If you have not yet done so, you must [Configure Maven](../README.md#mavenconfiguration) before testing the quickstarts.


Start JBoss Enterprise Application Platform 6 or JBoss AS 7 with the Web Profile
-------------------------

1. Open a command line and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server with the web profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat

 
Build and Deploy the Quickstart
-------------------------

_NOTE: The following build command assumes you have configured your Maven user settings. If you have not, you must include Maven setting arguments on the command line. See [Build and Deploy the Quickstarts](../README.md#buildanddeploy) for complete instructions and additional options._

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        mvn clean package jboss-as:deploy

4. This will deploy `target/jboss-as-picketlink-authentication-http-basic.war` to the running instance of the server.


Access the application 
---------------------

The application will be running at the following URL: <http://localhost:8080/jboss-as-picketlink-authentication-http-basic>. 


Undeploy the Archive
--------------------

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn jboss-as:undeploy


Run the Quickstart in JBoss Developer Studio or Eclipse
-------------------------------------
You can also start the server and deploy the quickstarts from Eclipse using JBoss tools. For more information, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](../README.md#useeclipse) 


Debug the Application
------------------------------------

If you want to debug the source code or look at the Javadocs of any library in the project, run either of the following commands to pull them into your local repository. The IDE should then detect them.

        mvn dependency:sources
        mvn dependency:resolve -Dclassifier=javadoc
