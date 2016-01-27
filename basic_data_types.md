# 基本数据类型

###值传递 or 引用传递

* Class instances are reference types (i.e. your reference to a class instance is effectively a pointer)
* Functions are reference types
* Everything else is a value type; "everything else" simply means instances of structs and instances of enums, because that's all there is in Swift. Arrays and strings are struct instances, for example. You can pass a reference to one of those things (as a function argument) by using inout and taking the address, as newacct has pointed out. But the type is itself a value type.

[出处](http://stackoverflow.com/a/27366050/1954737)