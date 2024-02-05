# DEVOPS--Maven-Apache-Tomcat


Maven is a powerful build automation and dependency management tool used primarily for Java projects, although it can be used for projects in other programming languages as well. It provides a comprehensive set of features to help manage the software development lifecycle and simplify the build process.


Here are some common Maven commands:

mvn compile: Compiles the project's source code.
mvn test: Runs unit tests against compiled code.
mvn package: Packages the compiled code into a distributable format.
mvn install: Installs the package into the local repository.
mvn deploy: Deploys the package to a remote repository.
mvn site: Generates project documentation and reports.
mvn site-deploy: Deploys the generated documentation to a remote web server.
mvn clean: Executes the clean phase, deleting any previous build outputs.

Apache Tomcat, often referred to simply as Tomcat, is an open-source web server and servlet container developed by the Apache Software Foundation. It is one of the most popular Java-based web application servers used for deploying and running Java servlets and JavaServer Pages (JSP).

Commands to Setup:

##################----INSTALL TOMCAT----##################
cd /opt
sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz
sudo tar -xvf apache-tomcat-9.0.65.tar.gz

cd /opt/apache-tomcat-9.0.65/conf
sudo vi tomcat-users.xml
# ---add-below-line at the end (2nd-last line)----
# <user username="admin" password="admin1234" roles="admin-gui, manager-gui"/>

sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat

sudo vi /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml

comment:
<!-- Valve className="org.apache.catalina.valves.RemoteAddrValve"
  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

sudo vi /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml

comment:
<!-- Valve className="org.apache.catalina.valves.RemoteAddrValve"
  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

sudo stopTomcat
sudo startTomcat

sudo cp target/*.war /opt/apache-tomcat-9.0.65/webapps/

