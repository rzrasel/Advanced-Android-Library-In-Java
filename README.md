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
  implementation "rz.rasel:android-java-core-library:128.00.02"
}
```

### Android Libraries In "rz.rasel:android-java-core-library:{version}"
* Libraries In This Package:
    * [LogWriter Library](#logwriter-log-library "Goto #logwriter-log-library")
	* [RedirectWindow Library](#redirectwindow-library "Goto #redirectwindow-library")
	* [ManifestPermissions Library](#manifestpermissions-library "Goto #manifestpermissions-library")

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
public class ActivityMain {
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
public class ActivityMain {
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
public class ActivityMain {
    //...

    private void onRedirectActivity(Class argRedirectClass) {
        //...
        redirectWindow.execute(argRedirectClass);
    }
}
```
Redirect With Passing Data To Redirected Activity
```redirect_window_004
public class ActivityMain {
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

- - - -

### Usage Of ManifestPermissions - Android Library
#### ManifestPermissions Library:
```manifest_permissions_001
private ManifestPermissions manifestPermissions;
private String[] PERMISSIONS = {
	Manifest.permission.WRITE_EXTERNAL_STORAGE,
	Manifest.permission.READ_EXTERNAL_STORAGE,
	Manifest.permission.READ_PHONE_STATE,
	//Manifest.permission.REQUEST_INSTALL_PACKAGES,
};
public static int PERMISSIONS_REQUEST_CODE = 1120;
private boolean isPermissionGranted = false;

private void onManifestPermissions() {
	manifestPermissions = ManifestPermissions.getInstance(context);
	manifestPermissions.onSetEventListener(new ManifestPermissions.OnEventListenerHandler() {
		@Override
		public void onPermissionGranted(boolean argIsGranted) {
			//isPermissionGranted = argIsGranted;
			System.out.println("ERROR_SUCCESS_DEBUG_RESPONSE: called");
			if (!argIsGranted) {
				manifestPermissions.onRequestPermissions(ManifestPermissions.READ_LOGS, PERMISSIONS);
			} else {
				isPermissionGranted = true;
				//onRedirectWindow(ActivitySplashMidwayOne.class);
				//onPerformRequest();
			}
		}
	});
	if (!manifestPermissions.hasPermission(PERMISSIONS)) {
		isPermissionGranted = false;
		manifestPermissions.onRequestPermissions(ManifestPermissions.READ_LOGS, PERMISSIONS);
	} else {
		isPermissionGranted = true;
		//onRedirectWindow(ActivitySplashMidwayOne.class);
		//onPerformRequest();
	}
}

@Override
public void onRequestPermissionsResult(int argRequestCode, @NonNull String[] argPermissions, @NonNull int[] argGrantResults) {
	if (argRequestCode == ManifestPermissions.READ_LOGS) {
		manifestPermissions.onRequestPermissionsResult(argRequestCode, argPermissions, argGrantResults, ManifestPermissions.READ_LOGS);
	}
	super.onRequestPermissionsResult(argRequestCode, argPermissions, argGrantResults);
}
```
