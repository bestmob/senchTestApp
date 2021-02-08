### Description

Top Notch Display Issue, Push Notification, PDF annotation , image plug in for image annotation and multi select function off images

### Installation

    cordova plugin add cordova-plugin-splashscreen
    cordova plugin add cordova-plugin-statusbar
    cordova plugin add cordova-plugin-device
    cordova plugin add cordova-plugin-camera
    cordova plugin add cordova-plugin-network-information
    cordova plugin add cordova-plugin-inappbrowser
    # cordova plugin add cordova-plugin-ionic-webview
    cordova plugin add cordova-plugin-geolocation
    cordova plugin add https://github.com/gearit/RadaeePDF-Cordova.git
    cordova plugin add @havesource/cordova-plugin-push
    cordova plugin add cordova-plugin-x-socialsharing@5.0.12
    
    # cordova plugin add cordova-plugin-androidx
    # cordova plugin add cordova-plugin-androidx-adapter

    ------------------------

    cordova plugin add https://github.com/bestmob/cordova-plugin-customCamera.git

    cordova plugin add https://github.com/bestmob/cordova-plugin-MultipleImageSelection.git

    cordova plugin add https://github.com/bestmob/cordova-plugin-multiplePhotos.git

    cordova plugin add https://github.com/bestmob/cordova-plugin-aviaryImageAnnotation.git

    # cordova plugin add https://github.com/transistorsoft/cordova-background-geolocation-lt.git

    ------------------------

    cordova build android

### Uninstall

    cordova plugin rm cordova-plugin-splashscreen
    cordova plugin rm cordova-plugin-device
    cordova plugin rm cordova-plugin-camera
    cordova plugin rm cordova-plugin-network-information
    cordova plugin rm cordova-plugin-inappbrowser
    # cordova plugin rm cordova-plugin-ionic-webview
    cordova plugin rm cordova-plugin-geolocation
    cordova plugin rm com.radaee.cordova
    cordova plugin rm havesource-cordova-plugin-push
    cordova plugin rm cordova-plugin-x-socialsharing
    
    # cordova plugin rm cordova-plugin-androidx
    # cordova plugin rm cordova-plugin-androidx-adapter
    
    ------------------------

    cordova plugin rm cordova-plugin-customCamera
    cordova plugin rm cordova-plugin-MultipleImageSelection
    cordova plugin rm cordova-plugin-multiplePhotos
    cordova plugin rm cordova-plugin-aviaryImageAnnotation
    # cordova plugin rm cordova-background-geolocation-lt

### Android Setup

- update build.gradle file and sync (File/Sync Project with Gradle Files)
      (App\platforms\android\app\build.gradle   in line 356)
  ```
    dependencies {
      implementation ("com.github.bumptech.glide:glide:3.8.0") {
        //exclude group: "com.android.support"
      }
      //implementation 'com.android.support:appcompat-v7:28.0.0'
      //implementation "com.android.support:support-fragment:26.1.0"
      
      //implementation "com.adobe.creativesdk.foundation:auth:0.9.1251"
      //implementation "com.adobe.creativesdk:image:4.8.4"
      //repositories {
      //  maven { url 'https://maven.localytics.com/public' }
      //}
      //implementation "com.localytics.android:library:4.0.1"

      //implementation "com.android.support:multidex:1.0.1"
      //implementation "com.android.support:support-v4:27.+"
      //implementation "com.android.support:support-v4:25.3.1"
    }
  ```
  \platforms\android\com.radaee.cordova\buildshop-build-extras.gradle
  It has
    api 'com.android.support:support-v4:26.1.0'
    api 'com.android.support:multidex:1.0.1'
  so don't need to add support-v4, multidex in the other gradle config.
  If there is duplicated support-v4, remove one.

- update build.gradle file and sync (File/Sync Project with Gradle Files)
      (App\platforms\android\app\build.gradle in line 252)
  ```
    android {
      defaultConfig {
        multiDexEnabled true
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
remove com.android.support:support
`#cordova.system.library.1=com.android.support:support-v4:27.+`
`#cordova.system.library.2=com.android.support:support-v13:28.0.0`
`#cordova.system.library.2=com.android.support:appcompat-v7:28.+`

- src\main\AndroidManifest.xml, update manifest and supports-screens, insert following 
```
 <manifest xmlns:tools="http://schemas.android.com/tools" >
 <supports-screens tools:replace="android:smallScreens" >
```

- src\main\AndroidManifest.xml, make sure CustomCameraActivity, MultipleSelectionActivity is added into manifest
```
<application  ...>

  <activity android:configChanges="orientation" android:hardwareAccelerated="true" android:name="com.best.cordova.plugins.camera.CustomCameraActivity" android:screenOrientation="portrait" />
  
  <activity android:configChanges="orientation|keyboardHidden|screenSize" android:name="com.best.cordova.plugins.MultipleImageSelection.MultipleSelectionActivity" android:screenOrientation="portrait" android:theme="@android:style/Theme.NoTitleBar" />
</application>
```

- src\main\AndroidManifest.xml, add ApplicationMainClass into android:name  under application tag
```
<application android:name="com.best.cordova.plugins.ImageAnnotation.ApplicationMainClass" />
```
This is for cordova-plugin-aviaryImageAnnotation, if it's duplicated, remove it.

### iOS Setup

#### install cordova-plugin-aviaryImageAnnotation plugin
extract src/ios/AdobeCreativeSDKFrameworks.zip.

cordova platform add ios
cordova build ios

- AdobeCreativeSDKCore configuration 
  // Add -ObjC as a linker flag in Build Settings/Linking/Other Linker Flags.
  
  ?? In Build Settings, Apple LLVM - Preprocessing, add USE_CSDK_COMPONENTS to the Preprocessor Macros.
  
  1. In General, Frameworks, Libraries, and Embedded Content
    AdobeCreativeSDKCore.framework    changed to Embed & Sign
    AdobeCreativeSDKImage.framework    changed to Embed & Sign
    

  

### Reference
    https://github.com/CreativeSDK/ios-getting-started-samples/blob/master/Framework%20Dependencies/Guide/Guide.md#core
    https://github.com/jeduan/cordova-plugin-imagepicker
    https://github.com/gearit/RadaeePDF-Cordova.git
