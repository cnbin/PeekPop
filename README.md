![PeekPop - backwards-compatible peek and pop in Swift](https://cloud.githubusercontent.com/assets/889949/13729164/1df56d7a-e92f-11e5-8190-4188f7e848aa.png)

[![Build Status](https://travis-ci.org/marmelroy/PeekPop.svg?branch=master)](https://travis-ci.org/marmelroy/PeekPop) [![Version](http://img.shields.io/cocoapods/v/PeekPop.svg)](http://cocoapods.org/?q=PeekPop)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

# PeekPop
Peek and Pop is a phenomenal iOS feature introduced with iPhone 6S and 6S+ that allows you to easily preview content. Sadly, almost 80% of users are on older devices. PeekPop is a Swift framework that brings backwards-compatibility to Peek and Pop.  

<p align="center"><img src="http://i.giphy.com/3o7ablu0adICfQ3OXC.gif" width="242" height="425"/></p>

## Features


              |  Features
--------------------------|------------------------------------------------------------
:star2: | Uses Apple's beautiful peek and pop interaction for devices with 3D touch.
:point_up_2: | Pressure-sensitive tap recognition for older devices.
:heartpulse: | Faithful recreation of the peek and pop animation on older devices. 
:iphone: | Almost identical API to Apple's.

Missing features:
- Support for peek and pop preview actions in devices that don't have 3D touch. 

## Usage

Import PeekPop at the top of the Swift file.

```swift
import PeekPop
```

Create a PeekPop object and register your object for handling the peek by specifying the source view. You will also need to declare that your object will conform to the PeekPopPreviewingDelegate protocol.

```swift
class MyViewController: UIViewController, PeekPopPreviewingDelegate {
    
    var peekPop: PeekPop?
        
    override func viewDidLoad() {
        peekPop = PeekPop(viewController: self)
        peekPop?.registerForPreviewingWithDelegate(self, sourceView: collectionView)
    }
```

PeekPopPreviewingDelegate requires two simple functions. You will need to tell it what view controller to present for peeking purposes with: 
```swift
    func previewingContext(previewingContext: PreviewingContext, viewControllerForLocation location: CGPoint) -> UIViewController?
```

.. and you will need to tell it how to commit the preview view controller at the end of the transition with: 
```swift
    func previewingContext(previewingContext: PreviewingContext, commitViewController viewControllerToCommit: UIViewController)
```

### Setting up with [CocoaPods](http://cocoapods.org/?q=PeekPop)
```ruby
source 'https://github.com/CocoaPods/Specs.git'
pod 'PeekPop', '~> 0.1'
```

### Setting up with Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that automates the process of adding frameworks to your Cocoa application.

You can install Carthage with [Homebrew](http://brew.sh/) using the following command:

```bash
$ brew update
$ brew install carthage
```

To integrate PeekPop into your Xcode project using Carthage, specify it in your `Cartfile`:

```ogdl
github "marmelroy/PeekPop"
```
