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

## INSTALLING GIT 

1. install git
> https://git-scm.com/downloads

2. sign in git in cmd / terminal 
> git config --global user.name "your_username" 

> git config --global user.email "your_email_address@example.com"

note: for a simple config just use the same email with github

3. create ssh key in your pc/laptop

- Generate SSH
> $ ssh-keygen

note: for enter passphrase just empty it

4. See ssh
> $ cat ~/.ssh/id_rsa.pub or $ pbcopy < ~/.ssh/id_rsa.pub

5. Check ssh // tbh i forgot what is this command doing hehe
> $ dir .ssh

4. sign the ssh key from your device pc/laptop to git web service profile

![image](https://user-images.githubusercontent.com/90954993/209432173-0de76a7e-5f64-4ea2-b62e-11634704a08f.png)


5. when cloning if asked to enter password create token in git web profile

![image](https://user-images.githubusercontent.com/90954993/209432378-e1745cbe-d7ba-4a28-93b9-05a4497832a8.png)


## SYNCHING MS VISUAL STUDIO CODE CONFIG

1. install Settings Sync extension from author Shan Khan
2. press f1 and choose download settings to download stored settings
3. choose update/upload to upload new settings

## SETTING FLUTTER PATH
1. check what shell you are using with
> echo $SHELL
2. open the shell
>  If you’re using Bash, edit $HOME/.bash_profile or $HOME/.bashrc. If you’re using Z shell, edit $HOME/.zshrc
3. add flutter/bin path to rc file 
> export PATH="$PATH:$HOME/flutter/bin"
4. run source
> source $HOME/.<rc file>

## Installing cocoapods

1. Run following command
> brew cleanup -d -v 
> brew install cocoapods 
Note: If you see failed to link then run brew link cocoapods

If linking is getting failed then run

> brew link --overwrite cocoapods

