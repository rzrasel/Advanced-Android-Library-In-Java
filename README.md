# Advanced Android Library In Java
Advanced Android Library In Java

[ ![Download](https://api.bintray.com/packages/rzrasel/android-java-core-library-center/android-core-library/images/download.svg) ](https://bintray.com/rzrasel/android-java-core-library-center/android-core-library/_latestVersion)

## Advanced Android Library In Java - Integration
### Gradle Dependency
build.gradle (project path)  
```groovy_project_path 
buildscript {  
  repositories {
    jcenter()
  }
}  
```  
build.gradle (module path)
```groovy_android_gradle_dependency
dependencies {  
  implementation "rz.rasel:android-java-core-library:128.00.01"
}
```

### Usage Of LogWriter
LogWriter Log
```log_writer_log
// Enable or disable LogWriter. By default LogWriter is enabled.
LogWriter.isDebug = true; // If debug is true -> LogWriter is enabled. Else if debug is false -> LogWriter is disabled
LogWriter.Log("DEBUG_LOG: This is a LogWriter Log");
```
