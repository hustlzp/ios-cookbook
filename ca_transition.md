# CATransition

###动画类型参考

[UIViewAnimation动画与CATransition类动画](http://www.cnblogs.com/pengyingh/articles/2339420.html)

###在navigationController.pushViewController/popViewController中使用CATransition

```swift
// push
let transition = CATransition()

transition.duration = 0.3
transition.type = "oglFlip"
transition.subtype = kCATransitionFromRight
navigationController?.view.layer.addAnimation(transition, forKey: kCATransition)
navigationController?.pushViewController(ShareUserViewController(user: user), animated: false)

// pop
let transition = CATransition()

transition.duration = 0.3
transition.type = "oglFlip"
transition.subtype = kCATransitionFromLeft
navigationController?.view.layer.addAnimation(transition, forKey: kCATransition)
navigationController?.popViewControllerAnimated(false)
```

###在presentViewController中使用

```swift
let transition = CATransition()
transition.duration = 0.3
transition.type = "oglFlip"
transition.subtype = kCATransitionFromRight
UIApplication.sharedApplication().keyWindow?.layer.addAnimation(transition, forKey: kCATransition)
presentViewController(ShareUserViewController(user: user), animated: false, completion: nil)

// dismiss
let transition = CATransition()

transition.duration = 0.3
transition.type = "oglFlip"
transition.subtype = kCATransitionFromLeft
UIApplication.sharedApplication().keyWindow?.layer.addAnimation(transition, forKey: kCATransition)
dismissViewControllerAnimated(false, completion: nil)
```

###CATransition结束时执行代码

```swift
animation.delegate = self
```

然后实现`animationDidStop:finished:`方法。