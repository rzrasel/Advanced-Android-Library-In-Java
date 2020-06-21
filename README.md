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
    * [LogWriter Library](#logwriter-log-library "Goto #logwriter-log-library")
	* [RedirectWindow Library](#redirectwindow-library "Goto #redirectwindow-library")

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
LogWriter.iLog("DEBUG_LOG: This is a LogWriter Log");

// Option 4:
LogWriter.iLog("TAG", "This is a LogWriter Log");

// Option 5:
LogWriter.dLog("DEBUG_LOG: This is a LogWriter Log");

// Option 6:
LogWriter.dLog("TAG", "This is a LogWriter Log");

// Option 7:
LogWriter.eLog("DEBUG_LOG: This is a LogWriter Log");

// Option 8:
LogWriter.eLog("TAG", "This is a LogWriter Log");
```

- - - -

### Usage Of RedirectWindow - Android Library
#### RedirectWindow Library:
Initialization RedirectWindow
```redirect_window_001
public class ActivitySplash {
    //...
    private RedirectWindow redirectWindow;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
	//...
        onRedirectActivity(ActivityToRedirect.class);
    }

    private void onRedirectActivity(Class argRedirectClass) {
        //...
        redirectWindow = new RedirectWindow(activity, context);
    }
}
```
Another Way Of Initialization RedirectWindow
```redirect_window_002
public class ActivitySplash {
    //...

    @Override
    protected void onCreate(Bundle savedInstanceState) {
	//...
        onRedirectActivity(ActivityToRedirect.class);
    }

    private void onRedirectActivity(Class argRedirectClass) {
        //...
        RedirectWindow redirectWindow = new RedirectWindow(activity, context);
    }
}
```
Simple Call Of RedirectWindow
```redirect_window_003
public class ActivitySplash {
    //...

    private void onRedirectActivity(Class argRedirectClass) {
        //...
        redirectWindow.execute(argRedirectClass);
    }
}
```
Redirect With Passing Data To Redirected Activity
```redirect_window_004
public class ActivitySplash {
    //...

    private void onRedirectActivity(Class argRedirectClass) {
        //...
	Intent intent = redirectWindow.getNewIntent();
	intent.putExtra("extra_item", extraData);

	Bundle bundle = new Bundle();
	bundle.putSerializable("serializable_item", serializableData);
	intent.putExtras(bundle);
		
        redirectWindow.withIntent(intent)
		.execute(argRedirectClass);
    }
}
```
Get/Grab Data From Redirected Activity
```redirect_window_005
public class ActivityToRedirect {
    //..
    private RedirectWindow redirectWindow;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        //...
        redirectWindow = new RedirectWindow(activity, context);
        Intent intent = redirectWindow.getParsedIntent();
        Bundle bundleExtras = intent.getExtras();
    }
}
```
```redirect_window_006
redirectWindow.withFlag()
	.withIntent(intent)
	.disposeWindow()
	.execute(ActivityTarget.class);
```
