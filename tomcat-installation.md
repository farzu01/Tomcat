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
     PAHT=$PATH:$JAVA_HOME
  
     Open ~/.bash_profile 
     add above lines in '.bash.profile'

```
Once Java installtion Completed

#### Install Tomcat
```sh
     #Install Tomcat 
     http://apachemirror.wuchna.com/tomcat/tomcat-8/v8.5.49/bin/apache-tomcat-8.5.49.tar.gz (Download tomcat packges from 'https://tomcat.apache.org/download-90.cgi')
     
     once download untar it.
     `tar -zvxf apache-tomcat-*`
     
     After that move in to some folder.
     mv apache-tomcat-*/* /opt/tomcat
     cd tomcat
     
     Change permissions to start and stop files.
     cd /opt/tomcat/bin
     chmod +x startup.sh
     chmod +x shutdown.sh
```

Tomcat Port Selection
```sh
     cd tomcat/conf/
     vi server.xm (in this file change the port if you want other wise its working on 8080 port)
                  (in this file we have connector port section in that section you can change)
``` 

In this step set the permissions.
```sh
     find / -name context.xml
     vi /opt/tomcat/webapps/host-manager/META-INF/context.xml (comment the value section)
     vi /opt/tomcat/webapps/manager/META-INF/context.xml (comment the value section)
```

In this step set the users
```sh
     <role rolename="manager-gui"/>
     <role rolename="manager-script"/>
     <role rolename="manager-jmx"/> 
     <role rolename="manager-status"/>
     <user username="tomcat" password="tomcat" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
```
Now start the Tomcat using bewlow commands.

```sh
   go to the `/opt/tomcat/bin`
   run startup.sh file
```


