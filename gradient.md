# Gradient

###CAGradientLayer

```swift
var view: UIView = UIView(frame: CGRectMake(0.0, 0.0, 320.0, 50.0))
var gradient: CAGradientLayer = CAGradientLayer()
gradient.frame = view.bounds
gradient.colors = [UIColor.whiteColor().CGColor, UIColor.blackColor().CGColor]
view.layer.insertSublayer(gradient, atIndex: 0)
```

控制渐变方向：

```swift
gradient.startPoint = CGPointMake(0.0, 0.5)
gradient.endPoint = CGPointMake(1.0, 0.5)
```