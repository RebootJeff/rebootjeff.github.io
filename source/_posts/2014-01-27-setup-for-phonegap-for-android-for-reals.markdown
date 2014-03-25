---
layout: post
title: "Setup for PhoneGap for Android for Reals"
date: 2014-01-27 17:52
comments: true
categories: ['Android', 'PhoneGap', 'development tools', 'technical posts']
---

![PhoneGap and Android have wonderful conversations](/images/20140127/phonegap-android.png)

PhoneGap is a crazy tool for building “hybrid” smartphone apps. You write HTML, CSS, and JavaScript code for PhoneGap to compile into an app for iOS, Android, Windows Phone, Blackberry, etc. The app will simply use a browser embedded in a native app wrapper (hence, the “hybrid” label).

There are many pros and cons to developing with PhoneGap, but I won’t review those because you can find debates on the usefulness of PhoneGap and others like it so long as you have (at least) mediocre Google Fu. You do have Google Fu, [right](http://lmgtfy.com/?q=google+fu)? Don’t forget that Adobe PhoneGap is oftentimes referred to as Apache Cordova (even in modern documentation).

Anyway, this blog post is meant to disclose the growing pains you could encounter upon trying PhoneGap for the first time for Android development. Although if you’re developing for iOS, you’ll still face annoyances like having to disable WebView bounce (why doesn’t PhoneGap do that for you by default?!).

There were many unspoken hoops I had to jump through to get it working for me when I worked on an [outdoor video game app](https://github.com/RebootJeff/phone-tag-phonegap). I really wish someone had warned me about these hoops, but my loss is your gain.

# Installfest

I’m sure you were told to just install the Android SDK plus PhoneGap and then you’d be off to the races, right? [WRONG](http://imgur.com/gallery/4clw90A). So wrong. Incredibly wrong. Maybe it’s because my personal dev machine is running Ubuntu, but I had to install many missing pieces to the PhoneGap puzzle. Some PhoneGap tutorials cover some of these dev components, but I don’t remember seeing one that covered all of them so here you go:

- Apache Ant: Java library/tool
- JRE: Java Runtime Environment
- JDK: Java Development Kit
- Android SDK: platform Software Dev Kit (make sure it comes with Eclipse)

After you install the Android SDK, you probably want to make sure you have the right API version. I used API 17 for supporting phones with Android v4.2. Use the SDK manager to install the desired API. Type `android` in a terminal to open the SDK manager. If that doesn’t work, it’s probably because you have a problem that will be solved by reading the next section of this blog post.

# Command Line Goodness

Everyone wants to use command line tools. In fact, PhoneGap wants to use some commands for Android development, but SURPRISE! Those commands are not available until you manually edit your .bash_profile file. You may have to do some searching to find where your .bash_profile sleeps at night, but mine was in my home directory (aka ~/.bash_profile). Keep in mind that it is a hidden file, so you need to enable viewing hidden files (in case you didn’t know). I created a Development folder for my Android dev tools. Then I added the following lines to my .bash_profile (make sure you replace my filepath with your filepath):

{% coderay .bash_profile %}
# Adds Android SDK tools to command line
export PATH=$PATH:/home/myUserName/Development/adt-bundle-linux-x86_64-20131030/sdk/tools
export PATH=$PATH:/home/myUserName/Development/adt-bundle-linux-x86_64-20131030/sdk/platform-tools
{% endcoderay %}

Now, you’re finally set to begin development with PhoneGap. However, if you want certain features to work, you may have to modify some XML files. Read on, my relative from a common-and-super-old ancestor.

# XML File Modifications

Want your app to access external networks? Getting origin errors? Try the sweet taste of the `<access origin>` tag. Want to enable geolocation? Try the soothing sounds eminating from the `<feature>` tag. These tags need to be edited/added to the `config.xml` file of your PhoneGap project. Put your Google Fu to practice if you need more details. Just keep in mind that if you run into various problems in the future, the `config.xml` file is yet another possible source of irritation to debug.

Here’s a snippet from my config file:

{% coderay config.xml %}
# Adds Android SDK tools to command line
<access origin="http://yourserver.com">
<feature name="http://api.phonegap.com/1.0/geolocation" />
{% endcoderay %}

By the way, it’s best practice to declare what kind of voodoo your app is utilizing. In case of GPS usage, modify your `/platforms/android/AndroidManifest.xml` file as follows:

{% coderay /platforms/android/AndroidManifest.xml %}
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_LOCATION_EXTRA_COMMANDS" />
{% endcoderay %}

# Down the Rabbit Hole

Using PhoneGap for the first time can be incredibly frustrating. I ran into so many small issues when learning how to use it. There can be problems with connecting a device to your computer, enabling certain phone features, dealing with compatibility quirks, etc.

## Connecting an Android Device
Type `adb devices` into a terminal after you use a USB cable to attach an Android phone to your computer. Make sure that the phone is put into **USB Debugging mode**. You can find that mode in the developer options. Different versions of Android have different ways to access the developer options.

If you don’t see any devices listed, you may need to investigate drivers for your phone. Sometimes there are other problems with adb that can be solved be restarting: try typing `adb kill-server && adb start-server` in your terminal (possibly with `sudo`).

## Plugins Not Included
When using GPS, I ran into some blog posts claiming that it’s necessary to install a geolocation plugin. In my experience, it’s not needed, but for other features, it may be a different story. If you’re trying to access a hardware sensor or simply want to use a feature someone has already implemented (e.g., bar code scanner), then you may need to investigate plugins. This might be helpful: [About Cordova plugin registry](http://cordova.apache.org/news/2013/10/21/cordova-registry.html)

## Android Fragmentation Strikes Again
Be warned: PhoneGap has different bugs for different versions of Android. For example, the PhoneGap app I worked on was built with Android API 17 (aka 4.2 aka Jelly Bean). I tested the app on a phone that uses Android 4.2.2 and a second phone that uses Android 4.4 (aka KitKat). The Jelly Bean phone had no functional issues with the app, but some CSS rules weren’t being applied correctly, which created some off-center layouts. The KitKat phone had no CSS issues, so it looked nice, but it had some functional issues regarding touch gestures. However, that could’ve been a problem with [Hammer.js](http://eightmedia.github.io/hammer.js/).

FYI, my team also encountered a problem in Android 4.4 and iOS 7 where scrolling wasn’t available for a `<section>` that had overflowing text. We tried the usual CSS rules, but to no avail.

#Links? Links!

I saved a few links that I found particularly useful. I shall deposit said links right here because I can and totally not for SEO purposes.

- [Setting Up An Android App Build Environment With Android SDK and PhoneGap in Ubuntu 13.04](http://yaizabailen.com/setting-up-an-android-app-build-environment-with-android-sdk-and-phonegap-in-ubuntu-13-04/)
- [StackOverflow: restarting adb](http://stackoverflow.com/questions/3127539/ubuntu-android-device-debug/3129903#3129903)
- [StackOverflow: USB debugging mode](http://stackoverflow.com/questions/6116724/how-to-use-android-phone-instead-of-emulator)
- [PhoneGap 3.0 - Stuff You Should Know](http://devgirl.org/2013/09/05/phonegap-3-0-stuff-you-should-know/)

# To PhoneGap or Not to PhoneGap

So is PhoneGap worth the trouble? This blog post probably makes it sound like there’s a lot of shit to scoop before uncovering any treasure. That’s…mostly true. If rapid development is a priority, then PhoneGap is still a solid choice when you lack Objective-C and Java experience. I’ve heard from colleagues that learning Objective-C is its own special kind of hell, so that’s a +1 for PhoneGap, I guess.

To me, tech enthusiasts need to look at the bigger picture: imagine a world where mobile web apps dominate rather than having native apps dominate the smartphone landscape. Firefox OS is actually trying to embrace JavaScript, but why does it matter? Consider the differences in distribution. Forget app marketplaces. Forget Apple acting as a gatekeeper for iOS apps. Imagine that your app is as available as any other website. Web apps are becoming more and more powerful. There are new frameworks (e.g., [Famous](http://famo.us/) and another brand new one that I can’t remember at the moment) that make it possible to replicate the oohlala of the much-lauded Yahoo! Weather native app.

The problem is that web apps for mobile devices can’t yet access native notifications. This is a huge obstacle for mobile web app dominance. Companies want their apps to have notifications to enhance user engagement and fight churn. Users want their apps to have notifications because it makes smartphones more helpful (although the line between helpful and spammy seems slimmer than my chances of becoming a guitar master). That said, web apps are getting better at using phones’ GPS sensors, cameras, accelerometers, etc. Hopefully the barrier between native app and mobile web app will continue to whither and eventually die like smallpox. In the words of unoriginal coaches every where, “WE CAN DO IT!”
