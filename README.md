# coding-doc



## Playstore Things

#### # Build Keystore & Keytool list
Run this in cmd (Administrator)
```
1. locate project directory
2. keytool -genkey -v -keystore c:\Users\USER_NAME\key-keystore.jks -storetype JKS -keyalg RSA -keysize 2048 -validity 10000 -alias key
3. make and put key.properties file in android/ folder 

  storePassword=keystorePassword
  keyPassword=keystorePassword
  keyAlias=key
  storeFile=D:/Keep Out/Asal Ngoding/Development/WORKSPACE/Flutter/on_tracker/android/upload-keystore.jks
  
  CHECK Keystore
  1. open cmd and go to android folder > cd android
  2. type gradlew signinReport
  
4. Add the keystore information from your properties file before the android block in [project]/android/app/build.gradle

   def keystoreProperties = new Properties()
   def keystorePropertiesFile = rootProject.file('key.properties')
   if (keystorePropertiesFile.exists()) {
       keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
   }
   
    android {
         ...
   }

5. Find the buildTypes block in [project]/android/app/build.gradle
 
     buildTypes {
       release {
           // TODO: Add your own signing config for the release build.
           // Signing with the debug keys for now,
           // so `flutter run --release` works.
           signingConfig signingConfigs.debug
       }
   }
   
6. And replace it with the following signing configuration info:
   
   signingConfigs {
       release {
           keyAlias keystoreProperties['keyAlias']
           keyPassword keystoreProperties['keyPassword']
           storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
           storePassword keystoreProperties['storePassword']
       }
   }
   buildTypes {
       release {
           signingConfig signingConfigs.release
       }
   }
 
```

**KEYTOOL LIST**
in Visual Studio Code terminal
```
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```
<br />

## Upgrading/Downgrading flutter sdk/version

#### # Change Channel
Flutter has 4 channel stable(the latest stable version), master(on progress development like -pree version), beta, and dev
```
1. flutter channel (will show the list of channel)
2. flutter channel (channel name)
3. flutter upgrade
```

#### # Upgrading sdk
```1. flutter upgrade (this command will upgrade the latest version your current channel)```

#### # Upgrade/downgrade by changing repository
```
1. locate flutter directory, for example **C:\flutter**
2. run git bash
3. git checkout (flutter version) / example git checkout 1.22.6 / example git checkout 2.10.2
4. flutter doctor (to perform download and compile for the selected version)
```

<br />
