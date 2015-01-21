Vagrant - Java development enviroment

This vagrant image will kick start your development in a self contained ubuntu 14.04 box with all the packages installed. 

## Pre-requisites
* virtualbox - https://www.virtualbox.org/
* vagrant - http://www.vagrantup.com/
* URL to current apache-tomcat-7.x.x.tar.gz (Ex http://artfiles.org/apache.org/tomcat/tomcat-7/v7.0.57/bin/apache-tomcat-7.0.57.tar.gz"
)
* If the url is out of date, update the `$tomcat_url` definition in `manifests/default.pp` with the current apache-tomcat.

## Vagrant Setup
###Follow these steps:
* $ ```vagrant box add trusty64 http://files.vagrantup.com/trusty64.box```
	* This will download the VM for you
* $ ```git clone https://github.com/davisrixi/vagrant_java.git```
	* clone this repository
* Clone the puppet modules
	* $ ```cd vagrant_java```
	* $ ```git submodule init```
  	* $ ```git submodule update```

* $ ```vagrant up```
	* brings up the VM with mysql, tomcat and java installed.
* $ ```vagrant ssh```
	* Login to your instance.

## Deployment Details
* Tomcat is set at auto-start to false
  * use ```sudo supervisorctl start tomcat``` to start tomcat
* Vagrant is setup to map port 8080 of the VM to port 4880 on your machine
	*  http://localhost:4880/
* JMX support is enabled on the server: Vagrant is setup to map port 1099 of the VM to port 1099 on your machine, allowing for monitoring and remote deployment.
* Tomcat is started in debug mode: Vagrant is setup to map port 8000 of the VM to port 4800 on your machine, allowing for debugging from your IDE.
