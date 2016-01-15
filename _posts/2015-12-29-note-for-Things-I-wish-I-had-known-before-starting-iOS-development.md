---
layout: post
title: 《那些我希望你在开始 iOS 开发前就知道的事情》笔记
quote: Love apple, hate apple.
image: /media/2015-12-29-note-for-Things-I-wish-I-had-known-before-starting-iOS-development/20150405_New_working_table.jpg
comments: true
video: false
---

    To be a qualified Apple(果) fan(粉), learning iOS development.

*************


1. 善用开源项目，比如作者举例首次开启 App 时的引导动画 https://github.com/mamaral/Onboard
   
2. 注重基础，作者说他接触 iOS 开发是从斯坦福白胡子老爷爷那里开始的，那门课很好却没有涉及很多基础，导致开始写代码的时候写了有很多低级错误的代码。Big Nerd Ranch Guide for Objective-C and The Apple's Guide for Swift
   
3. Github 是人类的好朋友，开始写自己的类库之前先上 Github 和 Google 搜索下。
   
4. 高效的使用你的工具，Xcode快捷键， Cocoapods, continuos integration, TestFlight, Crashlytics, Parse
   
5. 读 Blog 和 Newsletters，Cocoa with love，iOS Dev Weekly，NSHipster，Ray Wenderlich...
   
6. 学一点设计，Sketch
   
7. bug 总是有的，使用 Debug 工具吧。Pong Debugger，Cocoa Lumberjack, Reveal, OHHTTPStubs
   
8. 数据存储
   
   ~~~
   If the data fits in memory entirely and is relatively unstructured, use plist

   If the data fits in memory entirely and has tree-like structure, use XML

   If the data does not fit in memory and has a structure of a graph, and the app does not need extraordinary query capabilities, use Core Data

   If the data does not fit in memory, has a complex structure, or the app benefits from powerful query capabilities provided by relational databases, use sqlite

   If the data must be secret (e.g. a password), use keychain.
   ~~~
   
   FMDB, SSFKeychain, Magical Record
   
9. 啊，网络。AFNetworking, Restkit, Alamofire
   
10. 依赖管理，Cocoapods, Carthage
    
11. 请写测试，XCTest, KIF, Kiwi, Quick



Source links:

1. [https://medium.com/ios-os-x-development/things-i-wish-i-had-known-before-starting-ios-development-part-1-421a05e8447e#.9nerbzkbx](https://medium.com/ios-os-x-development/things-i-wish-i-had-known-before-starting-ios-development-part-1-421a05e8447e#.9nerbzkbx)
2. [https://medium.com/ios-os-x-development/things-i-wish-i-had-known-before-starting-ios-development-part-2-d696eec65866#.rtyh23wao](https://medium.com/ios-os-x-development/things-i-wish-i-had-known-before-starting-ios-development-part-2-d696eec65866#.rtyh23wao)


