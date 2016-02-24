Admob Unity Plugin
==============================

Admob Unity Plugin provides a way to integrate admob ads in Unity3D Game and u3d app.
You can use it for Unity iOS and Android App with the same c# or js code.

## Admob Unity3d Plugin Readme Contents

1. [Admob Unity Plugin Description](#Admob-Unity-Plugin-Description)
2. [Unity Admob Plugin Features](#Unity-Admob-Plugin-Features)
3. [Downloads Admob Unity Plugin](#Downloads-Admob-Unity-Plugin)
4. [Installation Admob Unity](#Installation-Admob-Unity)
5. [Unity Plugin Wiki and Documentation](#Unity-Plugin-Wiki-and-Documentation)
6. [Quick Start](#quick-start)
7. [Unity Admob Demo Usage](#Unity-Admob-Demo-Usage)
8. [Important Tips](#Important Tips)
9. [Screenshots](#screenshots)
10. [License](#License)

## Admob Unity Plugin Description
The Google Mobile Ads SDK is the latest generation in Google mobile advertising featuring refined ad formats and streamlined APIs for access to mobile ad networks and advertising solutions. The SDK enables Unity mobile app developers to maximize their monetization in native mobile apps.

This repository contains the source code for the Google Mobile Ads Unity plugin. This plugin enables Unity developers to easily serve Google Mobile Ads on Android and iOS apps without having to write Java or Objective-C code. The plugin provides a C# interface for requesting ads that is used by C# scripts in your Unity project.

## Unity Admob Plugin Features
Platforms supported in one plugin :
- [x] Android, via SDK v7.8 (part of Google Play service platform)
- [x] iOS, via SDK v7.6.0
- [x] Support all native events
- [x] AdRequest targeting methods,such as children target,test mode
- [x] Not need change Android package name
- [x] Very simple API

Ad Types:
- [x] Banner(All Banner Type and Custom banner sizes)
- [x] Interstitial (text, picture, video)


## Downloads Admob Unity Plugin
AdmobPluginRes/GoogleMobileAds.framework and admob_unity_plugin.unitypackage is reqired <br/>
Download those files from Admob Unity3d Plugin Project Home https://github.com/unity-plugins/Unity-Admob <br/>
or Download all the Unity admob plugin project https://github.com/unity-plugins/Unity-Admob/archive/master.zip<br/>

## Installation Admob Unity
1. Open your project in the Unity editor.
2. Navigate to **Assets -> Import Package -> Custom Package**.
3. Select the AdmobUnityPlugin.unitypackage file.
4. Import all of the files for the plugins by selecting **Import**. Make sure
   to check for any conflicts with files.

## Unity Plugin Wiki and Documentation
* [Document](https://github.com/unity-plugins/Unity-Admob/wiki/Admob-Unity-Plugin-Document)
* [API](https://github.com/unity-plugins/Unity-Admob/wiki/Admob-Unity-Plugin-API)
* [Tutorial](https://github.com/unity-plugins/Unity-Admob/wiki/How-to-Use-Admob-Plugin-for-Unity)

## Quick Start
#### 1.Add Admob Banner in Unity App 
Here is the minimal code needed to create a banner.
```
    using admob;
    Admob.Instance().initAdmob("admob banner id", "admob interstitial id");//admob id with format ca-app-pub-27960468906xxx/xxxx67388
    Admob.Instance().showBannerRelative(AdSize.Banner, AdPosition.BOTTOM_CENTER, 0);

```

The AdPosition class specifies where to place the banner. AdSize specifies witch size banner to show

#### 2.Remove Banner 
By default, banners are visible. To temporarily hide a banner, call:
```
    Admob.Instance().removeBanner();
```

#### 3.How to integrate Interstitial into Unity 3d app?

Here is the minimal banner code to create an interstitial.
```
    using admob;
    Admob.Instance().initAdmob("admob banner id", "admob interstitial id");//initAdmob just need call once,if you called when create banner ,you not need call any more
    Admob.Instance().loadInterstitial(); 
```
Unlike banners, interstitials need to be explicitly shown. At an appropriate
stopping point in your app, check that the interstitail is ready before
showing it:
```
    if (Admob.Instance().isInterstitialReady()) {
      Admob.Instance().showInterstitial();
    }
```
#### 4.Custom Admob Banner Ad Sizes
In addition to constants on _AdSize_, you can also create a custom size:
```
    using admob;
    //Create a 250x250 banner.
    AdSize adSize = new AdSize(250, 250);
    Admob.Instance().showBannerAbsolute(adSize,0,30);
```
#### 5.Admob test Ads and children app
If you want to test the ads or the your app with children target,you can set with admob unity plugin easy
```
    using admob;
    Admob.Instance().setTesting(true);
    Admob.Instance().setForChildren(true);
```
#### 6.Ad Events
Both _Banner_ and _Interstitial_ contain the same ad events that you can
register for. 
Here we'll demonstrate setting ad events on a interstitial,and show interstitial when load success:
```
    using admob;
    Admob.Instance().interstitialEventHandler += onInterstitialEvent;
    void onInterstitialEvent(string eventName, string msg)
    {
        Debug.Log("handler onAdmobEvent---" + eventName + "   " + msg);
        if (eventName == AdmobEvent.onAdLoaded)
        {
            Admob.Instance().showInterstitial();
        }
    }
```
You only need to register for the events you care about.

## Unity Admob Demo Usage
1. import AdmobUnityPlugin.unitypackage to your Unity project
2. copy admobdemo.cs from AdmobPluginRes to your unity project/assets dic
3. attach admobdemo.cs to the main camera
4. edit  admob id  in admobdemo.cs
5. build and run this in your device

## Important Tips
1. Add **GoogleMobileAds.framework**. to Xcode Project
2. Add the following framework to Xcode project
    AdSupport.framework,EventKit.framework,EventKitUI.framework,CoreTelephony.framework,StoreKit.framework,MessageUI.framework

## Screenshots
![ScreenShot](https://raw.githubusercontent.com/unity-plugins/Unity-Admob/master/doc/android_banner.jpg) 
![ScreenShot](https://raw.githubusercontent.com/unity-plugins/Unity-Admob/master/doc/android_full.jpg) 

## License
[Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0.html)