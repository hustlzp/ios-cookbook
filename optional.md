# Optional

###给Optional添加默认值

```swift
var unwrappedValue = optionalValue ?? defaultValue
```

等同于：

```swift
var unwrappedValue = optionalValue ? optionalValue! : defaultValue
```

[出处](http://stackoverflow.com/a/24100008/1954737)。