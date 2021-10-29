### Note 
_Apple will reject apps that are using private url schemes (Ugh, Apple....) if they are pretty much obvius. Some apps are rejected and others are not, so, be aware of this issue before implementing any of those URL's in your app as a feature._

### Updates

* [UPDATE 4] iOS 10 update: apparently settings now can be reached using App-Pref instead of prefs
* ~~[UPDATE 3] For now you just can use url schemes to open your apps's settings with Swift 3.0 (Xcode 8). I'll keep you informed when OS preferences can be reached~~
* ~~[UPDATE 2] The openURL() method of UIApplication is now deprecated. You should use application(_:open:options:) instead~~
* ~~[UPDATE 1] Not yet tested in iOS 10. It will fail because of policies changes in URL scheme handling.~~


### Testing

Download [this Workflow](https://workflow.is/workflows/5e26afaedcb8497b898adb27b0b8ce9f) to find and test new `App-prefs:` URL Schemes

### Other Apps' Settings

Sometimes we need to open Setting's Preferences not of our app, but of the iPhone itself. What should we do to acomplish this?


![keyboard](https://cloud.githubusercontent.com/assets/724536/9033179/41e2d7be-39c5-11e5-8c25-8d123923ae94.gif)


 1. You must configure the URL Schemes in your project. You will find it in Target, Info, URL Scheme. Once there, just type **prefs** 

![gif-settings](https://cloud.githubusercontent.com/assets/724536/9033051/567a347a-39c4-11e5-9885-1e26460beab3.gif)

 2.- Later, just write the code with the URL path of the preference needed. In my case was the keyboard path.

## Swift 1.2

```swift
   UIApplication.sharedApplication().openURL(NSURL(string:"prefs:root=General&path=Keyboard")!)
```

## Swift 3.0
 
 This is a work around to open your app's preferences, but it will crash if you don't have any. 
 
Open SO's preferences only #available(iOS 10.0, *):

```swift
     UIApplication.shared.open(URL(string:UIApplicationOpenSettingsURLString)!)
```
      

Open app's preferences:   
 
   ```swift
      UIApplication.shared.open(URL(string:"App-Prefs:root=General&path=Keyboard")!)
   ```

## Objective-c

  ```objective-c
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"prefs:root=General&path=Keyboard"]];
  ```

### URL Schemes

| Settings Section | Launch from Widget (`Prefs:`) | Launch from App (`App-prefs:`) |
| --- | --- | --- |
| Settings **topmost level** | `Prefs:` | `App-prefs:` |
| About | `Prefs:root=General&path=About` | `App-prefs:root=General&path=About` |
| Accessibility | `Prefs:root=General&path=ACCESSIBILITY` | `App-prefs:root=General&path=ACCESSIBILITY` |
| Account Settings | `Prefs:root=ACCOUNT_SETTINGS` |`App-prefs:root=ACCOUNT_SETTINGS` |
| Airplane Mode | `Prefs:root=AIRPLANE_MODE` | `App-prefs:root=AIRPLANE_MODE` |
| Auto-Lock iOS < 10 | `Prefs:root=General&path=AUTOLOCK` | `App-prefs:root=General&path=AUTOLOCK` |
| Auto-Lock iOS > 10 | `Prefs:root=DISPLAY&path=AUTOLOCK` | `App-prefs:root=DISPLAY&path=AUTOLOCK` |
| Battery | `Prefs:root=BATTERY_USAGE` | `App-prefs:root=BATTERY_USAGE` |
| Bluetooth iOS < 9 | `Prefs:root=General&path=Bluetooth` | `App-prefs:root=General&path=Bluetooth`|
| Bluetooth iOS > 9 && < 12 | `Prefs:root=Bluetooth` | `App-prefs:root=Bluetooth` |
| Bluetooth iOS > 12 |  | `App-prefs:Bluetooth` |
| Cellular | `Prefs:root=MOBILE_DATA_SETTINGS_ID` | `App-prefs:root=MOBILE_DATA_SETTINGS_ID` |
| Date & Time | `Prefs:root=General&path=DATE_AND_TIME` | `App-prefs:root=General&path=DATE_AND_TIME`|
| Dictionary | `Prefs:root=General&path=DICTIONARY` | `App-prefs:root=General&path=DICTIONARY` |
| Display & Brightness | `Prefs:root=Brightness` | `App-prefs:root=DISPLAY` |
| Do Not Disturb | `Prefs:root=General&path=DO_NOT_DISTURB` | `App-prefs:root=General&path=DO_NOT_DISTURB` |
| Facetime | `Prefs:root=FACETIME` | `App-prefs:root=FACETIME` |
| General | `Prefs:root=General` | `App-prefs:root=General` |
| HealthKit | | `App-Prefs:root=HealthKit` |
| iCloud | `Prefs:root=CASTLE` | `App-prefs:root=CASTLE` |
| iTunes | `Prefs:root=MUSIC` | `App-prefs:root=MUSIC` |
| iTunes Equalizer | `Prefs:root=MUSIC&path=EQ` | `App-prefs:root=MUSIC&path=EQ` |
| iTunes Volume | `Prefs:root=MUSIC&path=VolumeLimit` | `App-prefs:root=MUSIC&path=VolumeLimit` |
| Keyboard | `Prefs:root=General&path=Keyboard` | `App-prefs:root=General&path=Keyboard` |
| Keyboards | `Prefs:root=General&path=Keyboard/KEYBOARDS` | `App-prefs:root=General&path=Keyboard/KEYBOARDS` |
| Language & Region | `Prefs:root=General&path=INTERNATIONAL` | `App-prefs:root=General&path=INTERNATIONAL` |
| ~~Location Services~~ | ~~`Prefs:root=LOCATION_SERVICES`~~ | ~~`App-prefs:root=LOCATION_SERVICES`~~ |
| Music | `Prefs:root=MUSIC` | `App-prefs:root=MUSIC` |
| Network iOS < 10? | `Prefs:root=General&path=Network` | `App-prefs:root=General&path=Network` |
| Nike iPod | `Prefs:root=NIKE_PLUS_IPOD` | `App-prefs:root=NIKE_PLUS_IPOD`|
| Notes | `Prefs:root=NOTES` |`App-prefs:root=NOTES` |
| Notifications | `Prefs:root=NOTIFICATIONS_ID` | `App-prefs:root=NOTIFICATIONS_ID` |
| Passbook | `Prefs:root=PASSBOOK` | `App-prefs:root=PASSBOOK` |
| Passwords | `Prefs:root=SAFARI&path=Passwords` | `App-prefs:root=SAFARI&path=Passwords` |
| Personal Hotspot | `Prefs:root=INTERNET_TETHERING` | `App-prefs:root=INTERNET_TETHERING` |
| Phone | `Prefs:root=Phone` | `App-prefs:root=Phone` |
| Photos & Camera | `Prefs:root=Photos` | `App-prefs:root=Photos` |
| Privacy | `Prefs:root=Privacy` | `App-prefs:root=Privacy` |
| Profiles & Device Management | `Prefs:root=General&path=ManagedConfigurationList` | `App-prefs:root=General&path=ManagedConfigurationList` |
| Reset | `Prefs:root=General&path=Reset` | `App-prefs:root=General&path=Reset` |
| Ringtone | `Prefs:root=Sounds&path=Ringtone` | `App-prefs:root=Sounds&path=Ringtone` |
| Safari | `Prefs:root=SAFARI` | `App-prefs:root=SAFARI` |
| Siri iOS < 10? | `Prefs:root=General&path=Assistant` | `App-prefs:root=General&path=Assistant` |
| Siri iOS > 10? | `Prefs:root=SIRI` | `App-prefs:root=SIRI` |
| Sounds |  | `App-prefs:Sounds` |
| Sounds & Haptics | `Prefs:root=Sounds` | `App-prefs:root=Sounds` |
| Software Update | `Prefs:root=General&path=SOFTWARE_UPDATE_LINK` | `App-prefs:root=General&path=SOFTWARE_UPDATE_LINK` |
| Storage & Backup | `Prefs:root=CASTLE&path=STORAGE_AND_BACKUP` | `App-prefs:root=CASTLE&path=STORAGE_AND_BACKUP` |
| Store | `Prefs:root=STORE` | `App-prefs:root=STORE` |
| Twitter | `Prefs:root=TWITTER` | `App-prefs:root=TWITTER` |
| Usage | `Prefs:root=General&path=USAGE` | `App-prefs:root=General&path=USAGE` |
| Video | `Prefs:root=VIDEO` | `App-prefs:root=VIDEO` |
| VPN iOS < 10?| `Prefs:root=General&path=Network/VPN` | `App-prefs:root=General&path=Network/VPN` |
| VPN iOS > 10?| `Prefs:root=VPN` | `App-prefs:root=VPN` |
| Wallet & Apple Pay | `shoebox://url-scheme` | `shoebox://url-scheme` |
| Wallpaper | `Prefs:root=Wallpaper` | `App-prefs:root=Wallpaper` |
| Wi-Fi | `Prefs:root=WIFI` | `App-prefs:root=WIFI` |


### Open other App's Notification settings

You can open any app notification's settings, only if that app **HAS** notifications enabled. For that you need the **bundleID** added in path:

   ```swift
      UIApplication.shared.openURL(NSURL(string:"App-prefs:root=NOTIFICATIONS_ID&path=com.microsoft.Office.Word")! as URL)
   ```

Finding an app's bundle identifier of any app:

 > * Find the app you are looking for on the Apple AppStore. For this example, we’ll use Yelp: https://itunes.apple.com/us/app/yelp/id284910350?mt=8
 > * Copy the app ID number. It’s just the numbers after the text “id” and before the “?”. So in this case, it is: 284910350.
 > * Paste that ID number into this URL: https://itunes.apple.com/lookup?id=284910350
 > * This will download a file **1.txt**
 > * Search the output you get back for “**bundleId**”. The app’s bundle ID will be listed there: com.yelp.yelpiphone

source: https://kb.acronis.com/content/39368

### Bluetooth
As [@johnny77221](https://gist.github.com/johnny77221) mention in comments, he impleted a way to open bluetooth settings, read in link above:

 https://gist.github.com/johnny77221/bcaa5384a242b64bfd0b8a715f48e69f

### Apple Pay / Wallet
by [@luismadrigal](https://gist.github.com/luismadrigal)

    shoebox://

### Cordova Plugin
[@guyromb](https://gist.github.com/guyromb) made a cordova plugin

https://github.com/guyromb/Cordova-open-native-settings/blob/master/src/ios/NativeSettings.m

### A cocopods plugin
it seems [@yoiang](https://gist.github.com/yoiang) made a plugin for cocoapods. Although it appears that is not updated to iOS > 10 but you can contribute to his project if you like it ;)

https://github.com/Adorkable/SettingsAppAccessiOS

## Open App Store


   ```swift
      UIApplication.shared.openURL(URL(string: "itms-apps://itunes.apple.com/app/id" + appStoreAppID)!)
   ```


## Contributions: 

[@antonjn](https://gist.github.com/antonjn), [@mikengyn](https://gist.github.com/mikengyn), [@johnny77221](https://gist.github.com/johnny77221), [@luismadrigal](https://gist.github.com/luismadrigal), [@guyromb](https://gist.github.com/guyromb), [@yoiang](https://gist.github.com/yoiang), [@deanlyoung](https://gist.github.com/deanlyoung)