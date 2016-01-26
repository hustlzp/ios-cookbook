# Blur

###使用GPUImage

```swift
import GPUImage

let stillImageSource = GPUImagePicture(image: image)
let blurFilter = GPUImageiOSBlurFilter()

stillImageSource.addTarget(blurFilter)
blurFilter.useNextFrameForImageCapture()
stillImageSource.processImage()

let blurredImage = brightnessFilter.imageFromCurrentFramebuffer()
```

###UIVisualEffectView


```swift
let blurEffect = UIBlurEffect(style: .Light)
let blurredView = UIVisualEffectView(effect: blurEffect)
```

缺点：style只有三种：Light、ExtraLight、Dark

###第三方库


* [FXBlurView](https://github.com/nicklockwood/FXBlurView)
