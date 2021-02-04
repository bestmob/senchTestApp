Before install

- update build.gradle file and sync (File/Sync Project with Gradle Files)
      (App\platforms\android\app\build.gradle   in line 356)
  ```
    dependencies {
      //implementation "com.android.support:support-v4:27.+"
      //implementation 'com.android.support:support-v4:25.3.1'
      implementation ("com.github.bumptech.glide:glide:3.8.0") {
        exclude group: "com.android.support"
      }
      //implementation 'com.android.support:appcompat-v7:28.0.0'
      //implementation "com.android.support:support-fragment:26.1.0"
      implementation "com.adobe.creativesdk.foundation:auth:0.9.1251"
      implementation "com.adobe.creativesdk:image:4.8.4"
      
      repositories {
          maven { url 'https://maven.localytics.com/public' }
      }
      implementation "com.localytics.android:library:4.0.1"
    }
  ```

- update build.gradle file and sync (File/Sync Project with Gradle Files)
      (App\platforms\android\app\build.gradle   in line 249)
  ```
    android {
      defaultConfig {
        manifestPlaceholders = [appPackageName: "e9ef8e6f6f764b27b6fd89087cf66c45"]
      }
    }
  ```

If com.localytics.android:library:4.0.1 has error, then download
https://localytics.jfrog.io/artifactory/public/com/localytics/android/library/4.0.1/

https://maven.localytics.com/public/com/localytics/android/library/4.0.1/
  ```
library-4.0.1-javadoc.jar
library-4.0.1.aar
library-4.0.1.pom
  ```

- platforms\android\project.properties
remove com.android.support:support-v4:27.+
#cordova.system.library.1=com.android.support:support-v4:27.+


- src\main\AndroidManifest.xml, update manifest and supports-screens, insert following 
```
 <manifest xmlns:tools="http://schemas.android.com/tools" >
 <supports-screens tools:replace="android:smallScreens" >
```
Installation

    cordova plugin add https://github.com/bestmob/cordova-plugin-customCamera.git
    
    cordova plugin add https://github.com/bestmob/cordova-plugin-MultipleImageSelection.git

    cordova plugin add cordova-plugin-imagepicker

    cordova plugin add https://github.com/bestmob/cordova-plugin-aviaryImageAnnotation.git


Uninstall

    cordova plugin rm cordova-plugin-customCamera

    cordova plugin rm cordova-plugin-MultipleImageSelection

    cordova plugin rm cordova-plugin-image-picker

    cordova plugin rm cordova-plugin-aviaryImageAnnotation


Reference

    https://github.com/jeduan/cordova-plugin-imagepicker