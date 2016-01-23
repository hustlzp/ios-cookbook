# UIImage

##图像操作

###resize

```swift
UIGraphicsBeginImageContext(CGSize(width: newWidth, height: newHeight))
croppedImage.drawInRect(CGRect(x: 0, y: 0, width: newWidth, height: newHeight))
let newImage = UIGraphicsGetImageFromCurrentImageContext()
UIGraphicsEndImageContext()
```

###crop

```swift
func crop(rect: CGRect) -> UIImage {
    var rectTransform: CGAffineTransform

    switch imageOrientation {
    case .Left:
        rectTransform = CGAffineTransformTranslate(CGAffineTransformMakeRotation(CGFloat(M_PI_2)), 0, -size.height)
    case .Right:
        rectTransform = CGAffineTransformTranslate(CGAffineTransformMakeRotation(CGFloat(-M_PI_2)), -size.width, 0)
    case .Down:
        rectTransform = CGAffineTransformTranslate(CGAffineTransformMakeRotation(CGFloat(-M_PI)), -size.width, -size.height)
    default:
        rectTransform = CGAffineTransformIdentity
    }

    rectTransform = CGAffineTransformScale(rectTransform, self.scale, self.scale)
    let imageRef = CGImageCreateWithImageInRect(CGImage, CGRectApplyAffineTransform(rect, rectTransform))
    return UIImage(CGImage: imageRef!, scale: self.scale, orientation: imageOrientation)
}
```

###merge

```swift
// TODO
```

###blur

使用GPUImage库

```swift
import GPUImage

let stillImageSource = GPUImagePicture(image: image)
let blurFilter = GPUImageiOSBlurFilter()

stillImageSource.addTarget(blurFilter)
blurFilter.useNextFrameForImageCapture()
stillImageSource.processImage()

let blurredImage = brightnessFilter.imageFromCurrentFramebuffer()
```

##显示

###显示原图像

在navBar、tabBar中，系统会更改图像的颜色，若想保持原图则需如下代码：

```objc
img = img.imageWithRenderingMode(.AlwaysOriginal)
```

##读取


###读取App图标

```objc
let image = UIImage(named:"AppIcon40x40")
```
