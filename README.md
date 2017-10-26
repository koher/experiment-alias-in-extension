# AliasInExtension

```swift
public struct Foo<T> {}

extension Foo where T == Float {
    public typealias A = Double
}

extension Foo where T == Int {
    public typealias A = Int64
}
```

```
$ swift build
Compile Swift Module 'AliasInExtension' (3 sources)
/path/to/AliasInExtension/Sources/AliasInExtension/FooFloat.swift:2:22: error: invalid redeclaration of 'A'
    public typealias A = Double
                     ^
/path/to/AliasInExtension/Sources/AliasInExtension/FooInt.swift:2:22: note: 'A' previously declared here
    public typealias A = Int64
                     ^
/path/to/AliasInExtension/Sources/AliasInExtension/FooInt.swift:2:22: error: invalid redeclaration of 'A'
    public typealias A = Int64
                     ^
/path/to/AliasInExtension/Sources/AliasInExtension/FooFloat.swift:2:22: note: 'A' previously declared here
    public typealias A = Double
                     ^
error: terminated(1): /usr/bin/swift-build-tool -f /path/to/AliasInExtension/.build/debug.yaml main

```
