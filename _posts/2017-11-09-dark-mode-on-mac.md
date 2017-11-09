---
title: "Enable 'Dark Mode' on your Mac with this tool"
tags: tools apple mac
categories: Apple
date: 2017-11-09 19:18:00 +0100
excerpt: "In this post, we'll see how to darken OS X/macOS apps in a cool way!"
toc: true
toc_label: "To darken OS X Apps"
toc_icon: "gear"
featured: true
---
OS X is known to be light, extremely light. That's why, an user named **@guilhermerambo** created [this tool](https://medium.com/@guilhermerambo/how-to-enable-real-dark-mode-on-os-x-macos-14966f9f7d24), which makes any system control in any app **dark** and is easy as 1-2-3!
But this tool is **not** the perfection. In fact it can only darken apps on a _app per app basis_, and once you quit an app, you lose the "dark mode". The developer even said:

> The service I've written to enable dark mode in apps is just an experiment. You should not expect it to work or work reliably. I will not help anyone with this, it's just a proof of concept.

There's another complication: if an app doesn't contain or contains few system's built-in controls, the tool will result literally **useless**!

Two disclaimers by the developer:
> Disclaimer 1: Please note that, while I have SIP disabled on my machine, I do not recommend it to anyone, it's an important security feature and you should only disable it if you know the implications.

> Disclaimer 2: I am not responsible for any issues you might face while trying this out. If you computer blows up, it's not my fault.

So, with this on mind, let's start!

## Requisites
+ OS X El Capitan or later ver.
+ Xcode and Command Line Tools installed
+ [System Integrity Protection (SIP)](https://support.apple.com/en-us/HT204899) disabled ([how-to](https://www.imore.com/el-capitan-system-integrity-protection-helps-keep-malware-away))

## Instructions
1. Download [this file](https://github.com/insidegui/DarkMode/raw/master/Release/DarkMode.zip) and extract it to _~/Library/Services_.
1. Open the app you want to darken and press `[NameoftheApp]`>`Services`>`Apply Dark Mode`
1. Wait ~10 secs and —**voilà!**—your app should be dark.
