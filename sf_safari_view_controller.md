# SFSafariViewController

Available: iOS9+

在应用内部使用Safari打开。


```swift
import SafariService

if #available(iOS 9.0, *) {
    let controller = SFSafariViewController(URL: NSURL(string: "http://www.douban.com")!, entersReaderIfAvailable: true)
    self.presentViewController(controller, animated: true, completion: nil)
} else {
    // Fallback on earlier versions
}
```
