# Project Structure

##MVC

```
├─ Models
├─ Views
├─ Controllers
├─ Extensions
├─ Utils
├─ Additions
```

对于顶级目录，建议与真实文件夹关联起来（选中Group，打开右侧Utilities面板，点击文件夹图标进行关联）。

##常量

对于全局常量，建议放在单独的文件中（比如：`Constants.swift`），示例：


```swift

struct Font {
    static let WenTingFont = "FZLTTHK--GBK1-0"
}

struct Color {
    static let viewBackgroundColor = UIColor.colorWithRGBA(0xF6F5F3FF)
    static let textColor = UIColor.colorWithRGBA(0x444444FF)
    static let borderColor = UIColor.colorWithRGBA(0xDDDDDDFF)
}

struct Notification {
    static let logOut = "logoutNotification"
    static let logIn = "logInNotification"
}

struct Size {
    static let statusBarHeight: CGFloat = 20
    static let navigationBarHeight: CGFloat = 64
    static let navigationBarWithoutStatusHeight = navigationBarHeight - statusBarHeight
    static let tabBarHeight: CGFloat = 49
    
    static let screenWidth = UIScreen.mainScreen().bounds.size.width
    static let screenHeight = UIScreen.mainScreen().bounds.size.height
    static let screenMaxLength = max(Size.screenWidth, Size.screenHeight)
}

struct Device {
    static let isPhone = UIDevice.currentDevice().userInterfaceIdiom == .Phone
    static let isPhone4 = Device.isPhone && Int(Size.screenMaxLength) < 568
    static let isPhone5 = Device.isPhone && Int(Size.screenMaxLength) == 568
    static let isPhone6 = Device.isPhone && Int(Size.screenMaxLength) == 667
    static let isPhone6P = Device.isPhone && Int(Size.screenMaxLength) == 736
}
```