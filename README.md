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

### Android Libraries In "rz.rasel:android-java-core-library:{version}"
* Libraries In This Package:
    * [LogWriter](#logwriter-log "Goto #logwriter-log")
	* RedirectWindow

### Usage Of LogWriter Log - Android Library
#### LogWriter Log Library:
```log_writer_log_001
// Enable or disable LogWriter. By default LogWriter is enabled.
/*
* If debug is true -> LogWriter is enabled.
* Else if debug is false -> LogWriter is disabled
*/
LogWriter.isDebug = true;
LogWriter.Log("DEBUG_LOG: This is a LogWriter Log");
```

Simple Usage Of LogWriter Log:
```log_writer_log_002
// Option 1:
LogWriter.Log("DEBUG_LOG: This is a LogWriter Log");

// Option 2:
LogWriter.Log("TAG", "This is a LogWriter Log");

// Option 3:
LogWriter.iLog("TAG", "This is a LogWriter Log");

// Option 4:
LogWriter.iLog("This is a LogWriter Log");

// Option 5:
LogWriter.dLog("TAG", "This is a LogWriter Log");

// Option 6:
LogWriter.dLog("This is a LogWriter Log");
```
### Usage Of RedirectWindow - Android Library
#### RedirectWindow Library:
