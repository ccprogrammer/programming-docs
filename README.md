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
  
<br />
  
## Git Command
  
 #### # Cloning + remote
1. Choose which folder to save the cloned repo
2. Right click in the folder and choose git bash
3. run command: `git clone (repo/remote url)`

![image](https://user-images.githubusercontent.com/90954993/162659441-36a96723-517b-4413-a509-a54a4e139d7f.png)

#### # Cloning repo will only clone the master and cannot choose spesific branch to clone but you can choose spesific branch with command
```git checkout (branch name ~~without bracket~~)```

#### # Forking Git Repository
What is forking? it is copying other people repo with all the history to our repo it's just like making new repo but the repo is from other people repo. To do it just press 'Fork' in the repo you want to fork

#### # Add new branch from Github Website
If you want to add new branch from another branch, just select the branch first then add new branch
![image](https://user-images.githubusercontent.com/90954993/162657746-d4e99e72-5b77-403b-98f5-fcdb13f18af1.png)


#### # Adding new code update / push
This will update your branch with your code that has been updated, it will only add new code or remove the code that you had remove in Text Editor not uploading all files but but only updated code/files
```
1. git add  (the . means adding all files that has changed)
2. git commit -m 'Commit message explaining what change you do to the code
3. git push 
```

#### # Undo all **Modified** but not removing new folder

```git checkout -- .```
  
  <br />

