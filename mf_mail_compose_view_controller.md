# MFMailComposeViewController

Available: iOS3+

在应用内发送邮件。

```swift
import MessageUI

let mailComposeViewController = MFMailComposeViewController()
if MFMailComposeViewController.canSendMail() {
    mailComposerVC.mailComposeDelegate = self
    mailComposerVC.setToRecipients(["someone@somewhere.com"])
    mailComposerVC.setSubject("Sending you an in-app e-mail...")
    mailComposerVC.setMessageBody("Sending e-mail in-app is not so bad!", isHTML: false)
    
    self.presentViewController(mailComposeViewController, animated: true, completion: nil)
}

// MARK: MFMailComposeViewControllerDelegate Method
func mailComposeController(controller: MFMailComposeViewController!, didFinishWithResult result: MFMailComposeResult, error: NSError!) {
    controller.dismissViewControllerAnimated(true, completion: nil)
}
```

