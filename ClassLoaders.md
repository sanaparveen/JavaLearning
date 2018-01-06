# Java Class Loading


**JVM** is responsible for loading and executing code on java platform. **ClassLoader** is a part of JVM that loads classes into memory. It is an abstract class which is in java.lang package.

There are three types of built-in ClassLoader in Java:

1. **Bootstrap Class Loader/Primordial class loader:**  
  * It loads JDK internal classes that are part of  java runtime environment
  * It also typically loads rt.jar
  * All core java API class like String class, StringBuilder class, StringBuffer class, java.lang package, java.util package etc are available on rt.jar
  * rt.jar path is
   `jdk/jre/lib/rt.jar`  which is by default class path of bootstrap.

2. **Extensions Class Loader:**
   * `Jdk/jre/lib/ext/*.jar ` contains jar package that are Extensions of standard core java classes.
   * It loads classes from **_ext_** folder
   * The extension class loader is the child of bootstrap class loader.
   * jar files to be loaded can be added to extensions class folder by setting system environment to java.ext.dirs
   * The class name of extension class loader is
   'sun.misc.Launcher$ExtClassLoader.class'

3. **System Class Loader/Application class loader:**
   * Application class loader is the child of Extension class loader
   * Java classes that are avilable in the application classpath are loaded by application class Loader
   * Application class path is Environment variable class path.
   * The class name of application class loader is
   'sun.misc.Launcher$AppClassLoader.class'

ClassLoader are hierarchial. First level is bootstrap class loader, second level is extensions class loader and third level is system class loader.

___
### How ClassLoader works?

 * On JVM request for a class, loadClass function of ClassLoader is invoked by passing fully classified name of the class

 * Function loadClass calls for findLoadedClass() method to check whether the requesting class has been loaded or not. This avoid loading of class multiple times

* If the class is not loaded already then it will delegate request to parent ClassLoader to load the class. In case parent ClassLoader could not find the class then it will invoke findClass method to find classes in the file system.

#### Example java program

Main.java
```
public class Main {

    public static void main(String[] args) {

      System.out.println("ClassLoader for String: "
              + java.lang.String.class.getClassLoader());
      System.out.println("ClassLoader for DNSNameServiceDescriptor: "
              + sun.net.spi.nameservice.dns.DNSNameServiceDescriptor.class
              .getClassLoader());
      System.out.println("ClassLoader for sql Driver: "+ com.mysql.jdbc.Driver.class.getClassLoader());
    }
}

```
output

```
ClassLoader for String->null
ClassLoader for DNSNameServiceDescriptor: sun.misc.Launcher$ExtClassLoader@45ee12a7
ClassLoader for sql Driver:sun.misc.Launcher$AppClassLoader@18b4aac2
```
* On loading java.lang.String, the System ClassLoader delegates it to the Extension ClassLoader, which in turn delegates to Bootstrap ClassLoader that found the class and load it in JVM

* The same process is followed in case of DNSNameServiceDescriptor class but Bootstrap ClassLoader is not able to locate it because it's present in `jdk/jre/lib/ext/dnsns.jar` and hence it's loaded by Extensions ClassLoader

* MySQL is in system path i.e mysql jar file is included in build path of the project before execution. It gets loaded by System ClassLoader.

The classes loaded by a child ClassLoader have visibility into classes loaded by its parent class loaders. So classes loaded by Application/System ClassLoader have visibility into classes loaded by Extensions ClassLoader and Bootstrap ClassLoader.
___
### Advantage of Custom ClassLoader

1. HotDeployment(ability of making changes to a running application without causing any downtime or restarting the server) in Application Server.

2. Custom classloader in browser to check for security certification before execution of untrusted code, expecting a class at the runtime or from FTP server or via third party web sevice at the time of loading the class then existing ClassLoader need to be extended(e.g. AppletViewers load classes from remote web server), etc.,
