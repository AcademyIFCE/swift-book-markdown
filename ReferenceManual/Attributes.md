Attributes  

Attributes
==========

There are two kinds of attributes in Swift—those that apply to declarations and those that apply to types. An attribute provides additional information about the declaration or type. For example, the `discardableResult` attribute on a function declaration indicates that, although the function returns a value, the compiler shouldn’t generate a warning if the return value is unused.

You specify an attribute by writing the `@` symbol followed by the attribute’s name and any arguments that the attribute accepts:

```swift
@(attribute name)
@(attribute name)((attribute arguments))
```

Some declaration attributes accept arguments that specify more information about the attribute and how it applies to a particular declaration. These *attribute arguments* are enclosed in parentheses, and their format is defined by the attribute they belong to.

Declaration Attributes
----------------------

You can apply a declaration attribute to declarations only.

### available

Apply this attribute to indicate a declaration’s life cycle relative to certain Swift language versions or certain platforms and operating system versions.

The `available` attribute always appears with a list of two or more comma-separated attribute arguments. These arguments begin with one of the following platform or language names:

*   `iOS`
    
*   `iOSApplicationExtension`
    
*   `macOS`
    
*   `macOSApplicationExtension`
    
*   `watchOS`
    
*   `watchOSApplicationExtension`
    
*   `tvOS`
    
*   `tvOSApplicationExtension`
    
*   `swift`
    

You can also use an asterisk (`*`) to indicate the availability of the declaration on all of the platform names listed above. An `available` attribute that specifies availability using a Swift version number can’t use the asterisk.

The remaining arguments can appear in any order and specify additional information about the declaration’s life cycle, including important milestones.

*   The `unavailable` argument indicates that the declaration isn’t available on the specified platform. This argument can’t be used when specifying Swift version availability.
    
*   The `introduced` argument indicates the first version of the specified platform or language in which the declaration was introduced. It has the following form:

    ```swift
    introduced: (version number)
    ```

    The *version number* consists of one to three positive integers, separated by periods.
    
*   The `deprecated` argument indicates the first version of the specified platform or language in which the declaration was deprecated. It has the following form:
    
    ```swift
    deprecated: (version number)
    ```
    
    The optional *version number* consists of one to three positive integers, separated by periods. Omitting the version number indicates that the declaration is currently deprecated, without giving any information about when the deprecation occurred. If you omit the version number, omit the colon (`:`) as well.
    
*   The `obsoleted` argument indicates the first version of the specified platform or language in which the declaration was obsoleted. When a declaration is obsoleted, it’s removed from the specified platform or language and can no longer be used. It has the following form:
    
    ```swift
    obsoleted: (version number)
    ```
    
    The *version number* consists of one to three positive integers, separated by periods.
    
*   The `message` argument provides a textual message that the compiler displays when emitting a warning or error about the use of a deprecated or obsoleted declaration. It has the following form:
    
    ```swift
    message: (message)
    ```
    
    The *message* consists of a string literal.
    
*   The `renamed` argument provides a textual message that indicates the new name for a declaration that’s been renamed. The compiler displays the new name when emitting an error about the use of a renamed declaration. It has the following form:
    
    ```swift
    renamed: (new name)
    ```
    
    The *new name* consists of a string literal.
    
    You can apply the `available` attribute with the `renamed` and `unavailable` arguments to a type alias declaration, as shown below, to indicate that the name of a declaration changed between releases of a framework or library. This combination results in a compile-time error that the declaration has been renamed.
    
    ```swift
    // First release
    protocol MyProtocol {
        // protocol definition
    }
    
    // Subsequent release renames MyProtocol
    protocol MyRenamedProtocol {
        // protocol definition
    }
    
    @available(*, unavailable, renamed: "MyRenamedProtocol")
    typealias MyProtocol = MyRenamedProtocol
    ```
    

You can apply multiple `available` attributes on a single declaration to specify the declaration’s availability on different platforms and different versions of Swift. The declaration that the `available` attribute applies to is ignored if the attribute specifies a platform or language version that doesn’t match the current target. If you use multiple `available` attributes, the effective availability is the combination of the platform and Swift availabilities.

If an `available` attribute only specifies an `introduced` argument in addition to a platform or language name argument, you can use the following shorthand syntax instead:

```swift
@available((platform name) (version number), *)
@available(swift (version number))
```

The shorthand syntax for `available` attributes concisely expresses availability for multiple platforms. Although the two forms are functionally equivalent, the shorthand form is preferred whenever possible.

```swift
@available(iOS 10.0, macOS 10.12, *)
class MyClass {
    // class definition
}
```

An `available` attribute that specifies availability using a Swift version number can’t additionally specify a declaration’s platform availability. Instead, use separate `available` attributes to specify a Swift version availability and one or more platform availabilities.

```swift
@available(swift 3.0.2)
@available(macOS 10.12, *)
struct MyStruct {
    // struct definition
}
```

### discardableResult

Apply this attribute to a function or method declaration to suppress the compiler warning when the function or method that returns a value is called without using its result.

### dynamicCallable

Apply this attribute to a class, structure, enumeration, or protocol to treat instances of the type as callable functions. The type must implement either a `dynamicallyCall(withArguments:)` method, a `dynamicallyCall(withKeywordArguments:)` method, or both.

You can call an instance of a dynamically callable type as if it’s a function that takes any number of arguments.

```swift
@dynamicCallable
struct TelephoneExchange {
    func dynamicallyCall(withArguments phoneNumber: [Int]) {
        if phoneNumber == [4, 1, 1] {
            print("Get Swift help on forums.swift.org")
        } else {
            print("Unrecognized number")
        }
    }
}

let dial = TelephoneExchange()

// Use a dynamic method call.
dial(4, 1, 1)
// Prints "Get Swift help on forums.swift.org"

dial(8, 6, 7, 5, 3, 0, 9)
// Prints "Unrecognized number"

// Call the underlying method directly.
dial.dynamicallyCall(withArguments: [4, 1, 1])
```

The declaration of the `dynamicallyCall(withArguments:)` method must have a single parameter that conforms to the [`ExpressibleByArrayLiteral`](https://developer.apple.com/documentation/swift/expressiblebyarrayliteral) protocol—like `[Int]` in the example above. The return type can be any type.

You can include labels in a dynamic method call if you implement the `dynamicallyCall(withKeywordArguments:)` method.

```swift
@dynamicCallable
struct Repeater {
    func dynamicallyCall(withKeywordArguments pairs: KeyValuePairs<String, Int>) -> String {
    return pairs
        .map { label, count in
            repeatElement(label, count: count).joined(separator: " ")
        }
        .joined(separator: "\n")
    }
}

let repeatLabels = Repeater()
print(repeatLabels(a: 1, b: 2, c: 3, b: 2, a: 1))
// a
// b b
// c c c
// b b
// a
```

The declaration of the `dynamicallyCall(withKeywordArguments:)` method must have a single parameter that conforms to the [`ExpressibleByDictionaryLiteral`](https://developer.apple.com/documentation/swift/expressiblebydictionaryliteral) protocol, and the return type can be any type. The parameter’s [`Key`](https://developer.apple.com/documentation/swift/expressiblebydictionaryliteral/2294108-key) must be [`ExpressibleByStringLiteral`](https://developer.apple.com/documentation/swift/expressiblebystringliteral). The previous example uses [`KeyValuePairs`](https://developer.apple.com/documentation/swift/keyvaluepairs) as the parameter type so that callers can include duplicate parameter labels—`a` and `b` appear multiple times in the call to `repeat`.

If you implement both `dynamicallyCall` methods, `dynamicallyCall(withKeywordArguments:)` is called when the method call includes keyword arguments. In all other cases, `dynamicallyCall(withArguments:)` is called.

You can only call a dynamically callable instance with arguments and a return value that match the types you specify in one of your `dynamicallyCall` method implementations. The call in the following example doesn’t compile because there isn’t an implementation of `dynamicallyCall(withArguments:)` that takes `KeyValuePairs<String, String>`.

```swift
repeatLabels(a: "four") // Error
```

### dynamicMemberLookup

Apply this attribute to a class, structure, enumeration, or protocol to enable members to be looked up by name at runtime. The type must implement a `subscript(dynamicMemberLookup:)` subscript.

In an explicit member expression, if there isn’t a corresponding declaration for the named member, the expression is understood as a call to the type’s `subscript(dynamicMemberLookup:)` subscript, passing information about the member as the argument. The subscript can accept a parameter that’s either a key path or a member name; if you implement both subscripts, the subscript that takes key path argument is used.

An implementation of `subscript(dynamicMemberLookup:)` can accept key paths using an argument of type [`KeyPath`](https://developer.apple.com/documentation/swift/keypath), [`WritableKeyPath`](https://developer.apple.com/documentation/swift/writablekeypath), or [`ReferenceWritableKeyPath`](https://developer.apple.com/documentation/swift/referencewritablekeypath). It can accept member names using an argument of a type that conforms to the [`ExpressibleByStringLiteral`](https://developer.apple.com/documentation/swift/expressiblebystringliteral) protocol—in most cases, `String`. The subscript’s return type can be any type.

Dynamic member lookup by member name can be used to create a wrapper type around data that can’t be type checked at compile time, such as when bridging data from other languages into Swift. For example:

```swift
@dynamicMemberLookup
struct DynamicStruct {
    let dictionary = ["someDynamicMember": 325,
    "someOtherMember": 787]
    subscript(dynamicMember member: String) -> Int {
        return dictionary[member] ?? 1054
    }
}
let s = DynamicStruct()

// Use dynamic member lookup.
let dynamic = s.someDynamicMember
print(dynamic)
// Prints "325"

// Call the underlying subscript directly.
let equivalent = s[dynamicMember: "someDynamicMember"]
print(dynamic == equivalent)
// Prints "true"
```

Dynamic member lookup by key path can be used to implement a wrapper type in a way that supports compile-time type checking. For example:

```swift
struct Point { var x, y: Int }

@dynamicMemberLookup
struct PassthroughWrapper<Value> {
    var value: Value
    subscript<T>(dynamicMember member: KeyPath<Value, T>) -> T {
        get { return value[keyPath: member] }
    }
}

let point = Point(x: 381, y: 431)
let wrapper = PassthroughWrapper(value: point)
print(wrapper.x)
```

### frozen

Apply this attribute to a structure or enumeration declaration to restrict the kinds of changes you can make to the type. This attribute is allowed only when compiling in library evolution mode. Future versions of the library can’t change the declaration by adding, removing, or reordering an enumeration’s cases or a structure’s stored instance properties. These changes are allowed on nonfrozen types, but they break ABI compatibility for frozen types.

>**Note**
>
>When the compiler isn’t in library evolution mode, all structures and enumerations are implicitly frozen, and you can’t use this attribute.

In library evolution mode, code that interacts with members of nonfrozen structures and enumerations is compiled in a way that allows it to continue working without recompiling even if a future version of the library adds, removes, or reorders some of that type’s members. The compiler makes this possible using techniques like looking up information at runtime and adding a layer of indirection. Marking a structure or enumeration as frozen gives up this flexibility to gain performance: Future versions of the library can make only limited changes to the type, but the compiler can make additional optimizations in code that interacts with the type’s members.

Frozen types, the types of the stored properties of frozen structures, and the associated values of frozen enumeration cases must be public or marked with the `usableFromInline` attribute. The properties of a frozen structure can’t have property observers, and expressions that provide the initial value for stored instance properties must follow the same restrictions as inlinable functions, as discussed in [inlinable](#inlinable).

To enable library evolution mode on the command line, pass the `-enable-library-evolution` option to the Swift compiler. To enable it in Xcode, set the “Build Libraries for Distribution” build setting (`BUILD_LIBRARY_FOR_DISTRIBUTION`) to Yes, as described in [Xcode Help](https://help.apple.com/xcode/mac/current/#/dev04b3a04ba).

A switch statement over a frozen enumeration doesn’t require a `default` case, as discussed in [Switching Over Future Enumeration Cases](Statements.md#switching-over-future-enumeration-cases). Including a `default` or `@unknown default` case when switching over a frozen enumeration produces a warning because that code is never executed.

### GKInspectable

Apply this attribute to expose a custom GameplayKit component property to the SpriteKit editor UI. Applying this attribute also implies the `objc` attribute.

### inlinable

Apply this attribute to a function, method, computed property, subscript, convenience initializer, or deinitializer declaration to expose that declaration’s implementation as part of the module’s public interface. The compiler is allowed to replace calls to an inlinable symbol with a copy of the symbol’s implementation at the call site.

Inlinable code can interact with `public` symbols declared in any module, and it can interact with `internal` symbols declared in the same module that are marked with the `usableFromInline` attribute. Inlinable code can’t interact with `private` or `fileprivate` symbols.

This attribute can’t be applied to declarations that are nested inside functions or to `fileprivate` or `private` declarations. Functions and closures that are defined inside an inlinable function are implicitly inlinable, even though they can’t be marked with this attribute.

### main

Apply this attribute to a structure, class, or enumeration declaration to indicate that it contains the top-level entry point for program flow. The type must provide a `main` type function that doesn’t take any arguments and returns `Void`. For example:

```swift
@main
struct MyTopLevel {
    static func main() {
        // Top-level code goes here
    }
}
```

Another way to describe the requirements of the `main` attribute is that the type you write this attribute on must satisfy the same requirements as types that conform to the following hypothetical protocol:`

```swift
protocol ProvidesMain {
    static func main() throws
}
```

### nonobjc

Apply this attribute to a method, property, subscript, or initializer declaration to suppress an implicit `objc` attribute. The `nonobjc` attribute tells the compiler to make the declaration unavailable in Objective-C code, even though it’s possible to represent it in Objective-C.

Applying this attribute to an extension has the same effect as applying it to every member of that extension that isn’t explicitly marked with the `objc` attribute.

You use the `nonobjc` attribute to resolve circularity for bridging methods in a class marked with the `objc` attribute, and to allow overloading of methods and initializers in a class marked with the `objc` attribute.

A method marked with the `nonobjc` attribute can’t override a method marked with the `objc` attribute. However, a method marked with the `objc` attribute can override a method marked with the `nonobjc` attribute. Similarly, a method marked with the `nonobjc` attribute can’t satisfy a protocol requirement for a method marked with the `objc` attribute.

### NSApplicationMain

Apply this attribute to a class to indicate that it’s the application delegate. Using this attribute is equivalent to calling the `NSApplicationMain(_:_:)` function.

If you don’t use this attribute, supply a `main.swift` file with code at the top level that calls the `NSApplicationMain(_:_:)` function as follows:

```swift
import AppKit
NSApplicationMain(CommandLine.argc, CommandLine.unsafeArgv)
```

### NSCopying

Apply this attribute to a stored variable property of a class. This attribute causes the property’s setter to be synthesized with a *copy* of the property’s value—returned by the `copyWithZone(_:)` method—instead of the value of the property itself. The type of the property must conform to the `NSCopying` protocol.

The `NSCopying` attribute behaves in a way similar to the Objective-C `copy` property attribute.

### NSManaged

Apply this attribute to an instance method or stored variable property of a class that inherits from `NSManagedObject` to indicate that Core Data dynamically provides its implementation at runtime, based on the associated entity description. For a property marked with the `NSManaged` attribute, Core Data also provides the storage at runtime. Applying this attribute also implies the `objc` attribute.

### objc

Apply this attribute to any declaration that can be represented in Objective-C—for example, nonnested classes, protocols, nongeneric enumerations (constrained to integer raw-value types), properties and methods (including getters and setters) of classes, protocols and optional members of a protocol, initializers, and subscripts. The `objc` attribute tells the compiler that a declaration is available to use in Objective-C code.

Applying this attribute to an extension has the same effect as applying it to every member of that extension that isn’t explicitly marked with the `nonobjc` attribute.

The compiler implicitly adds the `objc` attribute to subclasses of any class defined in Objective-C. However, the subclass must not be generic, and must not inherit from any generic classes. You can explicitly add the `objc` attribute to a subclass that meets these criteria, to specify its Objective-C name as discussed below. Protocols that are marked with the `objc` attribute can’t inherit from protocols that aren’t marked with this attribute.

The `objc` attribute is also implicitly added in the following cases:

*   The declaration is an override in a subclass, and the superclass’s declaration has the `objc` attribute.
    
*   The declaration satisfies a requirement from a protocol that has the `objc` attribute.
    
*   The declaration has the `IBAction`, `IBSegueAction`, `IBOutlet`, `IBDesignable`, `IBInspectable`, `NSManaged`, or `GKInspectable` attribute.
    

If you apply the `objc` attribute to an enumeration, each enumeration case is exposed to Objective-C code as the concatenation of the enumeration name and the case name. The first letter of the case name is capitalized. For example, a case named `venus` in a Swift `Planet` enumeration is exposed to Objective-C code as a case named `PlanetVenus`.

The `objc` attribute optionally accepts a single attribute argument, which consists of an identifier. The identifier specifies the name to be exposed to Objective-C for the entity that the `objc` attribute applies to. You can use this argument to name classes, enumerations, enumeration cases, protocols, methods, getters, setters, and initializers. If you specify the Objective-C name for a class, protocol, or enumeration, include a three-letter prefix on the name, as described in [Conventions](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Conventions/Conventions.html#//apple_ref/doc/uid/TP40011210-CH10-SW1) in [Programming with Objective-C](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html#//apple_ref/doc/uid/TP40011210). The example below exposes the getter for the `enabled` property of the `ExampleClass` to Objective-C code as `isEnabled` rather than just as the name of the property itself.

```swift
class ExampleClass: NSObject {
    @objc var enabled: Bool {
        @objc(isEnabled) get {
            // Return the appropriate value
        }
    }
}
```

### objcMembers

Apply this attribute to a class declaration, to implicitly apply the `objc` attribute to all Objective-C compatible members of the class, its extensions, its subclasses, and all of the extensions of its subclasses.

Most code should use the `objc` attribute instead, to expose only the declarations that are needed. If you need to expose many declarations, you can group them in an extension that has the `objc` attribute. The `objcMembers` attribute is a convenience for libraries that make heavy use of the introspection facilities of the Objective-C runtime. Applying the `objc` attribute when it isn’t needed can increase your binary size and adversely affect performance.

### propertyWrapper

Apply this attribute to a class, structure, or enumeration declaration to use that type as a property wrapper. When you apply this attribute to a type, you create a custom attribute with the same name as the type. Apply that new attribute to a property of a class, structure, or enumeration to wrap access to the property through an instance of the wrapper type. Local and global variables can’t use property wrappers.

The wrapper must define a `wrappedValue` instance property. The *wrapped value* of the property is the value that the getter and setter for this property expose. In most cases, `wrappedValue` is a computed value, but it can be a stored value instead. The wrapper is responsible for defining and managing any underlying storage needed by its wrapped value. The compiler synthesizes storage for the instance of the wrapper type by prefixing the name of the wrapped property with an underscore (`_`)—for example, the wrapper for `someProperty` is stored as `_someProperty`. The synthesized storage for the wrapper has an access control level of `private`.

A property that has a property wrapper can include `willSet` and `didSet` blocks, but it can’t override the compiler-synthesized `get` or `set` blocks.

Swift provides two forms of syntactic sugar for initialization of a property wrapper. You can use assignment syntax in the definition of a wrapped value to pass the expression on the right-hand side of the assignment as the argument to the `wrappedValue` parameter of the property wrapper’s initializer. You can also provide arguments to the attribute when you apply it to a property, and those arguments are passed to the property wrapper’s initializer. For example, in the code below, `SomeStruct` calls each of the initializers that `SomeWrapper` defines.

```swift
@propertyWrapper
struct SomeWrapper {
    var wrappedValue: Int
    var someValue: Double
    init() {
        self.wrappedValue = 100
        self.someValue = 12.3
    }
    init(wrappedValue: Int) {
        self.wrappedValue = wrappedValue
        self.someValue = 45.6
    }
    init(wrappedValue value: Int, custom: Double) {
        self.wrappedValue = value
        self.someValue = custom
    }
}

struct SomeStruct {
    // Uses init()
    @SomeWrapper var a: Int

    // Uses init(wrappedValue:)
    @SomeWrapper var b = 10

    // Both use init(wrappedValue:custom:)
    @SomeWrapper(custom: 98.7) var c = 30
    @SomeWrapper(wrappedValue: 30, custom: 98.7) var d
}
```

The *projected value* for a wrapped property is a second value that a property wrapper can use to expose additional functionality. The author of a property wrapper type is responsible for determining the meaning of its projected value and defining the interface that the projected value exposes. To project a value from a property wrapper, define a `projectedValue` instance property on the wrapper type. The compiler synthesizes an identifier for the projected value by prefixing the name of the wrapped property with a dollar sign (`$`)—for example, the projected value for `someProperty` is `$someProperty`. The projected value has the same access control level as the original wrapped property.

```swift
@propertyWrapper
struct WrapperWithProjection {
    var wrappedValue: Int
    var projectedValue: SomeProjection {
        return SomeProjection(wrapper: self)
    }
}
struct SomeProjection {
    var wrapper: WrapperWithProjection
}

struct SomeStruct {
    @WrapperWithProjection var x = 123
}
let s = SomeStruct()
s.x // Int value
s.$x // SomeProjection value
s.$x.wrapper // WrapperWithProjection value
```

### requires_stored_property_inits

Apply this attribute to a class declaration to require all stored properties within the class to provide default values as part of their definitions. This attribute is inferred for any class that inherits from `NSManagedObject`.

### testable

Apply this attribute to an `import` declaration to import that module with changes to its access control that simplify testing the module’s code. Entities in the imported module that are marked with the `internal` access-level modifier are imported as if they were declared with the `public` access-level modifier. Classes and class members that are marked with the `internal` or `public` access-level modifier are imported as if they were declared with the `open` access-level modifier. The imported module must be compiled with testing enabled.

### UIApplicationMain

Apply this attribute to a class to indicate that it’s the application delegate. Using this attribute is equivalent to calling the `UIApplicationMain` function and passing this class’s name as the name of the delegate class.

If you don’t use this attribute, supply a `main.swift` file with code at the top level that calls the [`UIApplicationMain(_:_:_:_:)`](https://developer.apple.com/documentation/uikit/1622933-uiapplicationmain) function. For example, if your app uses a custom subclass of `UIApplication` as its principal class, call the `UIApplicationMain(_:_:_:_:)` function instead of using this attribute.

### usableFromInline

Apply this attribute to a function, method, computed property, subscript, initializer, or deinitializer declaration to allow that symbol to be used in inlinable code that’s defined in the same module as the declaration. The declaration must have the `internal` access level modifier. A structure or class marked `usableFromInline` can use only types that are public or `usableFromInline` for its properties. An enumeration marked `usableFromInline` can use only types that are public or `usableFromInline` for the raw values and associated values of its cases.

Like the `public` access level modifier, this attribute exposes the declaration as part of the module’s public interface. Unlike `public`, the compiler doesn’t allow declarations marked with `usableFromInline` to be referenced by name in code outside the module, even though the declaration’s symbol is exported. However, code outside the module might still be able to interact with the declaration’s symbol by using runtime behavior.

Declarations marked with the `inlinable` attribute are implicitly usable from inlinable code. Although either `inlinable` or `usableFromInline` can be applied to `internal` declarations, applying both attributes is an error.

### warn_unqualified_access

Apply this attribute to a top-level function, instance method, or class or static method to trigger warnings when that function or method is used without a preceding qualifier, such as a module name, type name, or instance variable or constant. Use this attribute to help discourage ambiguity between functions with the same name that are accessible from the same scope.

For example, the Swift standard library includes both a top-level [`min(_:_:)`](https://developer.apple.com/documentation/swift/1538339-min/) function and a [`min()`](https://developer.apple.com/documentation/swift/sequence/1641174-min) method for sequences with comparable elements. The sequence method is declared with the `warn_unqualified_access` attribute to help reduce confusion when attempting to use one or the other from within a `Sequence` extension.

### Declaration Attributes Used by Interface Builder

Interface Builder attributes are declaration attributes used by Interface Builder to synchronize with Xcode. Swift provides the following Interface Builder attributes: `IBAction`, `IBSegueAction`, `IBOutlet`, `IBDesignable`, and `IBInspectable`. These attributes are conceptually the same as their Objective-C counterparts.

You apply the `IBOutlet` and `IBInspectable` attributes to property declarations of a class. You apply the `IBAction` and `IBSegueAction` attribute to method declarations of a class and the `IBDesignable` attribute to class declarations.

Applying the `IBAction`, `IBSegueAction`, `IBOutlet`, `IBDesignable`, or `IBInspectable` attribute also implies the `objc` attribute.

Type Attributes
---------------

You can apply type attributes to types only.

### autoclosure

Apply this attribute to delay the evaluation of an expression by automatically wrapping that expression in a closure with no arguments. You apply it to a parameter’s type in a method or function declaration, for a parameter whose type is a function type that takes no arguments and that returns a value of the type of the expression. For an example of how to use the `autoclosure` attribute, see [Autoclosures](../LanguageGuide/Closures.md#autoclosures) and [Function Type](Types.md#function-type).

### convention

Apply this attribute to the type of a function to indicate its calling conventions.

The `convention` attribute always appears with one of the following arguments:

*   The `swift` argument indicates a Swift function reference. This is the standard calling convention for function values in Swift.
    
*   The `block` argument indicates an Objective-C compatible block reference. The function value is represented as a reference to the block object, which is an `id`-compatible Objective-C object that embeds its invocation function within the object. The invocation function uses the C calling convention.
    
*   The `c` argument indicates a C function reference. The function value carries no context and uses the C calling convention.
    

With a few exceptions, a function of any calling convention can be used when a function any other calling convention is needed. A nongeneric global function, a local function that doesn’t capture any local variables or a closure that doesn’t capture any local variables can be converted to the C calling convention. Other Swift functions can’t be converted to the C calling convention. A function with the Objective-C block calling convention can’t be converted to the C calling convention.

### escaping

Apply this attribute to a parameter’s type in a method or function declaration to indicate that the parameter’s value can be stored for later execution. This means that the value is allowed to outlive the lifetime of the call. Function type parameters with the `escaping` type attribute require explicit use of `self.` for properties or methods. For an example of how to use the `escaping` attribute, see [Escaping Closures](../LanguageGuide/Closures.md#escaping-closures).

Switch Case Attributes
----------------------

You can apply switch case attributes to switch cases only.

### unknown

Apply this attribute to a switch case to indicate that it isn’t expected to be matched by any case of the enumeration that’s known at the time the code is compiled. For an example of how to use the `unknown` attribute, see [Switching Over Future Enumeration Cases](Statements.md#switching-over-future-enumeration-cases).

>**Grammar of an attribute**
>
>attribute → `@` [attribute-name](../ReferenceManual/Attributes.md#grammar_attribute-name) [attribute-argument-clause](../ReferenceManual/Attributes.md#grammar_attribute-argument-clause) <sub>opt</sub>
>
>attribute-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>attribute-argument-clause → `(` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `)`
>
>attributes → [attribute](../ReferenceManual/Attributes.md#grammar_attribute) [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub>
>
>balanced-tokens → [balanced-token](../ReferenceManual/Attributes.md#grammar_balanced-token) [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub>
>
>balanced-token → `(` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `)`
>
>balanced-token → `[` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `]`
>
>balanced-token → `{` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `}`
>
>balanced-token → Any identifier, keyword, literal, or operator
>
>balanced-token → Any punctuation except `(`, `)`, `[`, `]`, `{`, or `}`
