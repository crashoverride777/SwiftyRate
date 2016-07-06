# LeaveAppReview

A simple helper class to show a rate game/app alert after a set amount of app launches.

If you are looking for a more feature rich and more advanced helper have a look at these 2 great helpers.

https://github.com/nicklockwood/iRate

https://github.com/arashpayan/appirater

# SetUp

- Step 1:

Copy the LeaveAppReview.swift file into your project

- Step 2:

I prefer to show the rateGameAlert at app launch. To do this go to your intial ViewController (GameViewController) and comform to the protocol and than check for the alert in viewDidAppear (viewDidLoad is too early to show an alert)

```swift
class ViewController: UIViewController, RateGameAlertController {....

override func viewDidAppear(animated: Bool) {
        super.viewDidAppear(animated)
        
        let appStoreURL = getAppStoreURL(forAppID: "Enter your app I")
        
        // This way it will use the default app launches setting of 25
        checkRateGameAlert(forAppURL: appStoreURL)
        
        // This way it will use your own custom app launches setting
        checkRateGameAlert(forAppURL: appStoreURL, appLaunchesUntilAlert: 5) 

    }
```

To get your app ID, login to iTunes connect and go to MyApps-AppInformation and you should see it under General Information.

Note: 
If you want to show the alert at a later step simply add this code at the desired viewController

If you would like to show this alert in a SKScene than go to the helper and change the protocol extension from
```swift
extension RateGameAlert where Self: UIViewController {
```

to 
```swift
extension RateGameAlert where Self: SKScene {
```

# Release Notes

- v1.1

Tweaks and improvements

- v1.0
