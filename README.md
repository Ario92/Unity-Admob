Admob Unity Plugin
==============================

Admob Unity Plugin provides a way to integrate admob ads in Unity Game and u3d app.
You can use it for Unity iOS and Android App with the same c# or js code.
Unity Admob Plugin features include:

* A single package with cross platform (Android/iOS) support
* Support for Admob Banner Ads
* Support for Admob Interstitial Ads
* Custom banner sizes
* Support all Admob native events
* AdRequest targeting methods
* A sample project to demonstrate plugin integration
* Very simple API 

AdmobUnityPlugin.unitypackage is the plugin  file for those that want to easily import
,AdmobPluginRes contains Admob iOS  sdk 7.6 and a simple demo file how to use this plugin.

Build base on 
------------
Admob iOS SDK 7.6 ,android google play service 8


Integrate the Admob Unity Plugin into your Unity Game
-----------------------------------

1. Open your project in the Unity editor.
2. Navigate to **Assets -> Import Package -> Custom Package**.
3. Select the AdmobUnityPlugin.unitypackage file.
4. Import all of the files for the plugins by selecting **Import**. Make sure
   to check for any conflicts with files.



Run the project
---------------

If you're running the **HelloWorld** sample project, you should be able to run
the project now.

To build and run on Android, click **File -> Build Settings**, select the
Android platform, then **Switch Platform**, then **Build and Run**.

To build and run on iOS, click **File -> Build Settings**, select the iOS
platform, then **Switch Platform**, then **Build**. This will export an
XCode project. You'll need to do the following before you can run it:

1. From the Xcode project navigator, right-click on the project, and choose
   Add Files To "<Project Name>".
2. Navigate to and select **GoogleMobileAds.framework**.
3. Add the following framework to xcode project

	AdSupport.framework,EventKit.framework,EventKitUI.framework,CoreTelephony.framework,StoreKit.framework,MessageUI.framework


Running the Unity Admob Plugin demo code 
===========================
1.copy admobdemo.cs from AdmobPluginRes to your unity project/assets dic
2.attach admobdemo.cs to the main camera
3.set the admob id  in admobdemo.cs
4.build and run this in your device

Integrate Google admob into Unity3d 
===========================

The remainder of this guide assumes you are now attempting to write your own
code to integrate Google Mobile Ads into your game.

Add Admob Banner in Unity App
-----------------
Here is the minimal code needed to create a banner.

    using admob;
    ...
   Admob.Instance().initAdmob("admob banner id", "admob interstitial id");//admob id with format ca-app-pub-2796046890663330/756767388
   Admob.Instance().showBannerRelative(AdSize.Banner, AdPosition.BOTTOM_CENTER, 0);

The AdPosition class specifies where to place the banner. AdSize specifies witch size banner to show


How to integrate Interstitial into Unity 3d app?
-----------------------
Here is the minimal banner code to create an interstitial.

    using admob;
    ...
   Admob.Instance().initAdmob("admob banner id", "admob interstitial id");//initAdmob just need call once,if you called when create banner ,you not need call any more
   Admob.Instance().loadInterstitial(); 

Unlike banners, interstitials need to be explicitly shown. At an appropriate
stopping point in your app, check that the interstitail is ready before
showing it:

    if (Admob.Instance().isInterstitialReady()) {
      Admob.Instance().showInterstitial();
    }

Custom Admob Banner Ad Sizes
---------------
In addition to constants on _AdSize_, you can also create a custom size:

    using admob;
    ...

    // Create a 250x250 banner.
    AdSize adSize = new AdSize(250, 250);
    Admob.Instance().showBannerAbsolute(adSize,0,30);

Banner Placement Locations
--------------------------
The following constants list the available ad positions:

    AdPosition.TOP_LEFT
    AdPosition.TOP_CENTER
    AdPosition.TOP_RIGHT
    AdPosition.MIDDLE_LEFT
    AdPosition.MIDDLE_CENTER
    AdPosition.MIDDLE_RIGHT
    AdPosition.BOTTOM_LEFT
    AdPosition.BOTTOM_CENTER
    AdPosition.BOTTOM_RIGHT

Admob test Ads and children app
--------------------
If you want to test the ads or the your app with children target,you can set with admob unity plugin easy


    using admob;
    ...

    Admob.Instance().setTesting(true);
    Admob.Instance().setForChildren(true);


Ad Events
---------
Both _Banner_ and _Interstitial_ contain the same ad events that you can
register for. 
Here we'll demonstrate setting ad events on a interstitial,and show interstitial when load success:

    using admob;
    ...

    Admob.Instance().interstitialEventHandler += onInterstitialEvent;
    ...
    void onInterstitialEvent(string eventName, string msg)
    {
        Debug.Log("handler onAdmobEvent---" + eventName + "   " + msg);
        if (eventName == AdmobEvent.onAdLoaded)
        {
            Admob.Instance().showInterstitial();
        }
    }

You only need to register for the events you care about.

Remove Banner 
----------------
By default, banners are visible. To temporarily hide a banner, call:

    Admob.Instance().removeBanner();

Additional Resources
====================
* [Admob](https://apps.admob.com/)
* [Admob Unity Plugin Home](https://groups.google.com/group/google-admob-ads-sdk)

