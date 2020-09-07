# Tomacat Installation On Linux

#### Install Java
```sh
     Install java
     sudo apt update
     sudo apt install openjdk-8-jdk-headless
     sudo apt install openjdk-8-jre-headless
     java -version
 ```
	
Set Up JAVA HOME Path
```sh
     JAVA_HOME=/usr/lib/jvm/java-*
     M2=$M2_HOME/bin
     PAHT=<Existing_PATH>:$JAVA_HOME
  
     Open ~/.bash_profile 
     add above lines in '.bash.profile'

```
Once Java installtion Completed

#### Install Tomcat
```sh
     #Install Tomcat 
     http://apachemirror.wuchna.com/tomcat/tomcat-8/v8.5.49/bin/apache-tomcat-8.5.49.tar.gz (Download tomcat packges from 'https://tomcat.apache.org/download-90.cgi')
     
     once download untar it.
     `tar -zvxf apache-tomcat-8.5.49`
     
     After that move in to some folder.
     mv apache-tomcat-8.5.49 /opt
     cd apache-tomcat-8.5.49
     
     Change permissions to start and stop files.
     chmod x startup.sh
     chmod x shutdown.sh
     
     #Below command use for link files
     ln -s /opt/apache-tomcat-8.5.49/bin/startup.sh /usr/local/bin/tomcatup
     ln -s /opt/apache-tomcat-8.5.49/bin/shutdown.sh /usr/local/bin/tomcatdown
```

Tomcat Port Selection
```sh
     cd apache-tomcat-8.5.49/conf/
     vi server.xm (in this file change the port if you want other wise its working on 8080 port)
                  (in this file we have connector port section in that section you can change)
``` 

In this step set the permissions.
```sh
     find / -name context.xml
     vi /opt/apache-tomcat-8.5.49/webapps/host-manager/META-INF/context.xml (comment the value section)
     vi /opt/apache-tomcat-8.5.49/webapps/manager/META-INF/context.xml (comment the value section)
```

In this step set the users
```sh
     <role rolename="manager-gui"/>
     <role rolename="manager-script"/>
     <role rolename="manager-jmx"/> 
     <role rolename="manager-status"/>
     <user username="tomcat" password="tomcat" roles="manager-gui, manager-script"/>
```
Now start the Tomcat using bewlow commands.

```sh
   tomcatup
   or
   go to the `/opt/apache-tomcat-8.5.49/bin`
   run startup.sh file
```


