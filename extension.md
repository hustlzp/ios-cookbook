# Extension

###扩展类型限制的Array

```swift
extension Array where Element : Idable {
    func filterWithId(id : String) -> [Element] {
        return self.filter { $0.id == id }
    }
}
```
