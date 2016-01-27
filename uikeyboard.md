# UIKeyboard

###UIView跟随键盘animation

```swift
func keyboardWillShow(notification: NSNotification) {
    let kbSize = userInfo![UIKeyboardFrameEndUserInfoKey]!.CGRectValue.size
    let duration = (userInfo![UIKeyboardAnimationDurationUserInfoKey] as! NSNumber).doubleValue
    let curve = UIViewAnimationCurve(rawValue: (userInfo![UIKeyboardAnimationCurveUserInfoKey] as! NSNumber).integerValue)!
    
    var frame = self.accessoryView!.frame
    frame.origin.y = Size.screenHeight - frame.height - keyboardHeight

    UIView.beginAnimations(nil, context: nil)
    UIView.setAnimationDuration(duration)
    UIView.setAnimationCurve(curve)
    UIView.setAnimationBeginsFromCurrentState(true)
    self.accessoryView!.frame = frame
    UIView.commitAnimations()
}

func keyboardWillHide(notification: NSNotification) {
    let duration = (userInfo![UIKeyboardAnimationDurationUserInfoKey] as! NSNumber).doubleValue
    let curve = UIViewAnimationCurve(rawValue: (userInfo![UIKeyboardAnimationCurveUserInfoKey] as! NSNumber).integerValue)!
    
    var frame = self.accessoryView!.frame
    frame.origin.y = Size.screenHeight - frame.height

    UIView.beginAnimations(nil, context: nil)
    UIView.setAnimationDuration(duration)
    UIView.setAnimationCurve(curve)
    UIView.setAnimationBeginsFromCurrentState(true)
    self.accessoryView!.frame = frame
    UIView.commitAnimations()
}
```

[出处](http://stackoverflow.com/questions/18837166/how-to-mimic-keyboard-animation-on-ios-7-to-add-done-button-to-numeric-keyboar)