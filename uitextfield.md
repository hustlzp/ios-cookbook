# UITextField

###垂直居中

```swift
textField.contentVerticalAlignment = .Center
```

###backspace检测


```swift
import UIKit

@objc protocol DeletionDetectableTextFieldDelegate: class {
    optional func textFieldWillDelete()
    optional func textFieldDidDelete()
}

class DeletionDetectableTextField: UITextField {

    weak var deletionDetectableDelegate: DeletionDetectableTextFieldDelegate?
    
    override func deleteBackward() {
        deletionDetectableDelegate?.textFieldWillDelete?()
        
        super.deleteBackward()

        deletionDetectableDelegate?.textFieldDidDelete?()
    }
    
}
```