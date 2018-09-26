# SwiftyRate

[![Swift 4.2](https://img.shields.io/badge/swift-4.2-ED523F.svg?style=flat)](https://swift.org/download/)
[![Platform](https://img.shields.io/cocoapods/p/SwiftyRate.svg?style=flat)]()
[![CocoaPods Compatible](https://img.shields.io/cocoapods/v/SwiftyRate.svg)](https://img.shields.io/cocoapods/v/SwiftyRate.svg)

iOS 11 note: Apple has updated the app store guidlines and it seems that with iOS 11 it is no longer allowed to show custom review prompts. I assume this also will apply to tvOS which sucks a bit because SKStoreReviewController is not supported on tvOS.

A simple helper to show a SKStoreReviewController (iOS 10.3 or above) or custom UIAlertController with similar rules and behaviours. 

## Requirements

- iOS 9.3+
- Swift 4.0+

## Installation

[CocoaPods](https://developers.google.com/admob/ios/quick-start#streamlined_using_cocoapods) is a dependency manager for Cocoa projects. Simply install the pod by adding the following line to your pod file


```swift
pod 'SwiftyRate'
```

There is now an [app](https://cocoapods.org/app) which makes handling pods much easier

Altenatively you can drag the swift file(s) manually into your project.

## Usage

- Add the import statment when you installed via cocoa pods. 

```swift
import SwiftyRate 
```

- Request review

As Apple describes in the documentation for SKStoreReviewController 

"Although you should call this method when it makes sense in the user experience flow of your app, the actual display of a rating/review request view is governed by App Store policy. Because this method may or may not present an alert, it's not appropriate to call it in response to a button tap or other user action."

UIViewController
```swift
SwiftyRate.request(from: self, afterAppLaunches: 15)
```

SKScene (needs to be called outside/after DidMoveToView or it will not work)
```swift
if let viewController = view?.window?.rootViewController {
     SwiftyRate.request(from: viewController, afterAppLaunches: 15)
}
```
