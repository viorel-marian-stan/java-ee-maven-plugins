# Maven plugins testing app

This is a sample Java EE app to test 3 maven plugin options that might solve some atypical issues like class loading:

* maven-ear-plugin
  * unpack war module
* maven-dependency-plugin
  * unpack a jar module from the app, and an external library jar
  * exclude files (e.g. class files)  
* maven-war-plugin
  * exclude artifacts from the build
  
### Note:

In order to not get a `deleted outdated resource` message in the log file coming from the `maven-war-plugin`, a version of the plugin prior to `3.3.1` should be used.
The logic has been changed starting with version `3.3.1` to check `WEB-INF/lib/` for outdated resource by default:
```
    AbstractWarMojo.class
    (...)
    
    /**
     * Path prefix for resources that will be checked against outdated content.
     *
     * @since 3.3.1
     */
    @Parameter( defaultValue = "WEB-INF/lib/" )
    private String outdatedCheckPath;
    
    (...)
```