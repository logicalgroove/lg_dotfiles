Start Android simulator
=======================

`cd /Users/macbook/Library/Android/sdk/tools/bin`

### Install required files

`./sdkmanager "system-images;android-26;google_apis;x86"`

### Accepr licences

`./sdkmanager --licenses`

### List available devices to test

`./avdmanager list device`

### Create an image file

`./avdmanager create avd -n test -k "system-images;android-26;google_apis;x86" -b x86 -c 400M -d 32 -f`

### Start simulator

```
cd ..
./emulator -avd test
```

### Enable keyboard and camera

`vim ~/.android/avd/test.avd/config.ini`

#### Add this

```
hw.keyboard=yes
hw.camera=yes
```

## Edit HOST on device

#### Install tool

`brew cask install android-platform-tools`

#### Make root

```
adb root
adb disable-verity
adb reboot
adb root
adb remount
```

#### Pull the file

`adb pull /system/etc/hosts .`

#### Push the file

`adb push hosts /system/etc`
