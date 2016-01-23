#UIColor

##根据HEX值初始化颜色

```swift
extension UIColor {
    convenience init(hexValue: Int64) {
        self.init(red: (CGFloat)((color >> 24) & 0xFF) / 255.0, green: (CGFloat)((color >> 16) & 0xFF) / 255.0, blue: (CGFloat)((color >> 8) & 0xFF) / 255.0, alpha: (CGFloat)((color) & 0xFF) / 255.0)
    }
}
```

##获取tintColor

* view.tintColor