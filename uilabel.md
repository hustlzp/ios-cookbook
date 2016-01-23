# UILabel

###多行

```swift
label.numberOfLines = 0
label.lineBreakMode = .ByWordWrapping
```

###计算行数

```swift
extension UILabel {
    var numberOfLines: Int {
        if text == nil{
            return 0
        }

        let rect = CGSize(width: bounds.width, height: CGFloat.max)
        let size = (text! as NSString).boundingRectWithSize(rect, options: [.UsesLineFragmentOrigin, .UsesFontLeading], attributes: [NSFontAttributeName: font], context: nil)

        return Int(ceil(size.height / font.lineHeight))
    }
}
```

###AutoLayout时自动设置preferredMaxLayoutWidth

```swift
class AutoLayoutLabel: UILabel {
    override func layoutSubviews() {
        super.layoutSubviews()

        if numberOfLines == 0 {
            preferredMaxLayoutWidth = bounds.width
        }
    }
}
```

###识别URL、hashtag、手机号码

* [TTTAttributedLabel](https://github.com/TTTAttributedLabel/TTTAttributedLabel)：不支持NSTextAttachment
* [YYText](https://github.com/ibireme/YYText/)：特性丰富、但不支持AutoLayout
* [ActiveLabel.swift](https://github.com/optonaut/ActiveLabel.swift)：不支持中文
