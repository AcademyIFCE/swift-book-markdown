[Document Revision History](https://docs.swift.org/swift-book/RevisionHistory/RevisionHistory.html#document-revision-history)
=========================

**2020-09-16**

*   Updated for Swift 5.3.
*   Added information about multiple trailing closures to the [Trailing Closures](https://docs.swift.org/swift-book/LanguageGuide/Closures.html#ID102) section, and 
added information about how trailing closures are matched to parameters to the 
[Function Call Expression](https://docs.swift.org/swift-book/ReferenceManual/Expressions.html#ID398) section.
*   Added information about synthesized implementations of `Comparable` for enumerations 
to the [Adopting a Protocol Using a Synthesized Implementation](https://docs.swift.org/swift-book/LanguageGuide/Protocols.html#ID627) section.
*   Added the [Contextual Where Clauses](https://docs.swift.org/swift-book/LanguageGuide/Generics.html#ID628) section now that you can write a generic `where`
clause in more places.
*   Added the [Unowned Optional References](https://docs.swift.org/swift-book/LanguageGuide/AutomaticReferenceCounting.html#ID625) section with information about using 
unowned references with optional values.
*   Added information about the `@main` attribute to the [main](https://docs.swift.org/swift-book/ReferenceManual/Attributes.html#ID626) section.
*   Added `#filePath` to the [Literal Expression](https://docs.swift.org/swift-book/ReferenceManual/Expressions.html#ID390) section, and updated the discussion of 
`#file`.
*   Updated the [Escaping Closures](https://docs.swift.org/swift-book/LanguageGuide/Closures.html#ID546) section, now that closures can refer to `self` implicitly in 
more scenarios.
*   Updated the [Handling Errors Using Do-Catch](https://docs.swift.org/swift-book/LanguageGuide/ErrorHandling.html#ID541) and [Do Statement](https://docs.swift.org/swift-book/ReferenceManual/Statements.html#ID533) sections, now that a 
`catch` clause can match against multiple errors.
*   Added more information about `Any` and moved it into the new [Any Type](https://docs.swift.org/swift-book/ReferenceManual/Types.html#ID629) section.
*   Updated the [Property Observers](https://docs.swift.org/swift-book/LanguageGuide/Properties.html#ID262) section, now that lazy properties can have observers.
*   Updated the [Protocol Declaration](https://docs.swift.org/swift-book/ReferenceManual/Declarations.html#ID369) section, now that members of an enumeration can 
satisfy protocol requirements.
*   Updated the [Stored Variable Observers and Property Observers](https://docs.swift.org/swift-book/ReferenceManual/Declarations.html#ID359) section to describe 
when the getter is called before the observer.
*   Updated the [Memory Safety](https://docs.swift.org/swift-book/LanguageGuide/MemorySafety.html) chapter to mention atomic operations.

**2020-03-24**

*   Updated for Swift 5.2.
*   Added information about passing a key path instead of a closure to the [Key-Path
    Expression](https://docs.swift.org/swift-book/ReferenceManual/Expressions.html#ID563) section.
*   Added the [Methods with Special Names](https://docs.swift.org/swift-book/ReferenceManual/Declarations.html#ID622) section with information about syntactic sugar 
the lets instances of classes, structures, and enumerations be used with function call
syntax.
*   Updated the [Subscript Options](https://docs.swift.org/swift-book/LanguageGuide/Subscripts.html#ID308) section, now that subscripts support parameters with 
default values.
*   Updated the [Self Type](https://docs.swift.org/swift-book/ReferenceManual/Types.html#ID610) section, now that the `Self` can be used in more contexts.
*   Updated the [Implicitly Unwrapped Optionals](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html#ID334) section to make it clearer that an implicitly 
unwrapped optional value can be used as either an optional or non-optional value.

**2019-09-10**

*   Updated for Swift 5.1.
*   Added information about functions that specify a protocol that their return value conforms to, instead of providing a specific named return type, to the [Opaque Types](../LanguageGuide/OpaqueTypes.xhtml) chapter.
*   Added information about property wrappers to the [Property Wrappers](../LanguageGuide/Properties.xhtml#ID617) section.
*   Added information enumerations and structures that are frozen for library evolution to the [frozen](../ReferenceManual/Attributes.xhtml#ID620) section.
*   Added the [Functions With an Implicit Return](../LanguageGuide/Functions.xhtml#ID607) and [Shorthand Getter Declaration](../LanguageGuide/Properties.xhtml#ID608) sections with information about functions that omit `return`.
*   Added information about using subscripts on types to the [Type Subscripts](../LanguageGuide/Subscripts.xhtml#ID609) section.
*   Updated the [Enumeration Case Pattern](../ReferenceManual/Patterns.xhtml#ID424) section, now that an enumeration case pattern can match an optional value.
*   Updated the [Memberwise Initializers for Structure Types](../LanguageGuide/Initialization.xhtml#ID214) section, now that memberwise initializers support omitting parameters for properties that have a default value.
*   Added information about dynamic members that are looked up by key path at run time to the [dynamicMemberLookup](../ReferenceManual/Attributes.xhtml#ID585) section.
*   Added `macCatalyst` to the list of target environments in [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539).
*   Updated the [Self Type](../ReferenceManual/Types.xhtml#ID610) section, now that `Self` can be used to refer to the type introduced by the current class, structure, or enumeration declaration.

**2019-03-25**

*   Updated for Swift 5.0.
*   Added the [Extended String Delimiters](../LanguageGuide/StringsAndCharacters.xhtml#ID606) section and updated the [String Literals](../ReferenceManual/LexicalStructure.xhtml#ID417) section with information about extended string delimiters.
*   Added the [dynamicCallable](../ReferenceManual/Attributes.xhtml#ID603) section with information about dynamically calling instances as functions using the `dynamicCallable` attribute.
*   Added the [unknown](../ReferenceManual/Attributes.xhtml#ID605) and [Switching Over Future Enumeration Cases](../ReferenceManual/Statements.xhtml#ID602) sections with information about handling future enumeration cases in switch statements using the `unknown` switch case attribute.
*   Added information about the identity key path (`\.self`) to the [Key-Path Expression](../ReferenceManual/Expressions.xhtml#ID563) section.
*   Added information about using the less than (`<`) operator in platform conditions to the [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539) section.

**2018-09-17**

*   Updated for Swift 4.2.
*   Added information about accessing all of an enumeration’s cases to the [Iterating over Enumeration Cases](../LanguageGuide/Enumerations.xhtml#ID581) section.
*   Added information about `#error` and `#warning` to the [Compile-Time Diagnostic Statement](../ReferenceManual/Statements.xhtml#ID582) section.
*   Added information about inlining to the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section under the `inlinable` and `usableFromInline` attributes.
*   Added information about members that are looked up by name at runtime to the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section under the `dynamicMemberLookup` attribute.
*   Added information about the `requires_stored_property_inits` and `warn_unqualified_access` attributes to the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section.
*   Added information about how to conditionally compile code depending on the Swift compiler version being used to the [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539) section.
*   Added information about `#dsohandle` to the [Literal Expression](../ReferenceManual/Expressions.xhtml#ID390) section.

**2018-03-29**

*   Updated for Swift 4.1.
*   Added information about synthesized implementations of equivalence operators to the [Equivalence Operators](../LanguageGuide/AdvancedOperators.xhtml#ID45) section.
*   Added information about conditional protocol conformance to the [Extension Declaration](../ReferenceManual/Declarations.xhtml#ID378) section of the [Declarations](../ReferenceManual/Declarations.xhtml) chapter, and to the [Conditionally Conforming to a Protocol](../LanguageGuide/Protocols.xhtml#ID574) section of the [Protocols](../LanguageGuide/Protocols.xhtml) chapter.
*   Added information about recursive protocol constraints to the [Using a Protocol in Its Associated Type’s Constraints](../LanguageGuide/Generics.xhtml#ID575) section.
*   Added information about the `canImport()` and `targetEnvironment()` platform conditions to [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539).

**2017-12-04**

*   Updated for Swift 4.0.3.
*   Updated the [Key-Path Expression](../ReferenceManual/Expressions.xhtml#ID563) section, now that key paths support subscript components.

**2017-09-19**

*   Updated for Swift 4.0.
*   Added information about exclusive access to memory to the [Memory Safety](../LanguageGuide/MemorySafety.xhtml) chapter.
*   Added the [Associated Types with a Generic Where Clause](../LanguageGuide/Generics.xhtml#ID557) section, now that you can use generic `where` clauses to constrain associated types.
*   Added information about multiline string literals to the [String Literals](../LanguageGuide/StringsAndCharacters.xhtml#ID286) section of the [Strings and Characters](../LanguageGuide/StringsAndCharacters.xhtml) chapter, and to the [String Literals](../ReferenceManual/LexicalStructure.xhtml#ID417) section of the [Lexical Structure](../ReferenceManual/LexicalStructure.xhtml) chapter.
*   Updated the discussion of the `objc` attribute in [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348), now that this attribute is inferred in fewer places.
*   Added the [Generic Subscripts](../LanguageGuide/Generics.xhtml#ID558) section, now that subscripts can be generic.
*   Updated the discussion in the [Protocol Composition](../LanguageGuide/Protocols.xhtml#ID282) section of the [Protocols](../LanguageGuide/Protocols.xhtml) chapter, and in the [Protocol Composition Type](../ReferenceManual/Types.xhtml#ID454) section of the [Types](../ReferenceManual/Types.xhtml) chapter, now that protocol composition types can contain a superclass requirement.
*   Updated the discussion of protocol extensions in [Extension Declaration](../ReferenceManual/Declarations.xhtml#ID378) now that `final` isn’t allowed in them.
*   Added information about preconditions and fatal errors to the [Assertions and Preconditions](../LanguageGuide/TheBasics.xhtml#ID335) section.

**2017-03-27**

*   Updated for Swift 3.1.
*   Added the [Extensions with a Generic Where Clause](../LanguageGuide/Generics.xhtml#ID553) section with information about extensions that include requirements.
*   Added examples of iterating over a range to the [For-In Loops](../LanguageGuide/ControlFlow.xhtml#ID121) section.
*   Added an example of failable numeric conversions to the [Failable Initializers](../LanguageGuide/Initialization.xhtml#ID224) section.
*   Added information to the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section about using the `available` attribute with a Swift language version.
*   Updated the discussion in the [Function Type](../ReferenceManual/Types.xhtml#ID449) section to note that argument labels are not allowed when writing a function type.
*   Updated the discussion of Swift language version numbers in the [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539) section, now that an optional patch number is allowed.
*   Updated the discussion in the [Function Type](../ReferenceManual/Types.xhtml#ID449) section, now that Swift distinguishes between functions that take multiple parameters and functions that take a single parameter of a tuple type.
*   Removed the Dynamic Type Expression section from the [Expressions](../ReferenceManual/Expressions.xhtml) chapter, now that `type(of:)` is a Swift standard library function.

**2016-10-27**

*   Updated for Swift 3.0.1.
*   Updated the discussion of weak and unowned references in the [Automatic Reference Counting](../LanguageGuide/AutomaticReferenceCounting.xhtml) chapter.
*   Added information about the `unowned`, `unowned(safe)`, and `unowned(unsafe)` declaration modifiers in the [Declaration Modifiers](../ReferenceManual/Declarations.xhtml#ID381) section.
*   Added a note to the [Type Casting for Any and AnyObject](../LanguageGuide/TypeCasting.xhtml#ID342) section about using an optional value when a value of type `Any` is expected.
*   Updated the [Expressions](../ReferenceManual/Expressions.xhtml) chapter to separate the discussion of parenthesized expressions and tuple expressions.

**2016-09-13**

*   Updated for Swift 3.0.
*   Updated the discussion of functions in the [Functions](../LanguageGuide/Functions.xhtml) chapter and the [Function Declaration](../ReferenceManual/Declarations.xhtml#ID362) section to note that all parameters get an argument label by default.
*   Updated the discussion of operators in the [Advanced Operators](../LanguageGuide/AdvancedOperators.xhtml) chapter, now that you implement them as type methods instead of as global functions.
*   Added information about the `open` and `fileprivate` access-level modifiers to the [Access Control](../LanguageGuide/AccessControl.xhtml) chapter.
*   Updated the discussion of `inout` in the [Function Declaration](../ReferenceManual/Declarations.xhtml#ID362) section to note that it appears in front of a parameter’s type instead of in front of a parameter’s name.
*   Updated the discussion of the `@noescape` and `@autoclosure` attributes in the [Escaping Closures](../LanguageGuide/Closures.xhtml#ID546) and [Autoclosures](../LanguageGuide/Closures.xhtml#ID543) sections and the [Attributes](../ReferenceManual/Attributes.xhtml) chapter now that they are type attributes, rather than declaration attributes.
*   Added information about operator precedence groups to the [Precedence for Custom Infix Operators](../LanguageGuide/AdvancedOperators.xhtml#ID47) section of the [Advanced Operators](../LanguageGuide/AdvancedOperators.xhtml) chapter, and to the [Precedence Group Declaration](../ReferenceManual/Declarations.xhtml#ID550) section of the [Declarations](../ReferenceManual/Declarations.xhtml) chapter.
*   Updated discussion throughout to use macOS instead of OS X, `Error` instead of `ErrorProtocol`, and protocol names such as `ExpressibleByStringLiteral` instead of `StringLiteralConvertible`.
*   Updated the discussion in the [Generic Where Clauses](../LanguageGuide/Generics.xhtml#ID192) section of the [Generics](../LanguageGuide/Generics.xhtml) chapter and in the [Generic Parameters and Arguments](../ReferenceManual/GenericParametersAndArguments.xhtml) chapter, now that generic `where` clauses are written at the end of a declaration.
*   Updated the discussion in the [Escaping Closures](../LanguageGuide/Closures.xhtml#ID546) section, now that closures are nonescaping by default.
*   Updated the discussion in the [Optional Binding](../LanguageGuide/TheBasics.xhtml#ID333) section of the [The Basics](../LanguageGuide/TheBasics.xhtml) chapter and the [While Statement](../ReferenceManual/Statements.xhtml#ID432) section of the [Statements](../ReferenceManual/Statements.xhtml) chapter, now that `if`, `while`, and `guard` statements use a comma-separated list of conditions without `where` clauses.
*   Added information about switch cases that have multiple patterns to the [Switch](../LanguageGuide/ControlFlow.xhtml#ID129) section of the [Control Flow](../LanguageGuide/ControlFlow.xhtml) chapter and the [Switch Statement](../ReferenceManual/Statements.xhtml#ID436) section of the [Statements](../ReferenceManual/Statements.xhtml) chapter.
*   Updated the discussion of function types in the [Function Type](../ReferenceManual/Types.xhtml#ID449) section now that function argument labels are no longer part of a function’s type.
*   Updated the discussion of protocol composition types in the [Protocol Composition](../LanguageGuide/Protocols.xhtml#ID282) section of the [Protocols](../LanguageGuide/Protocols.xhtml) chapter and in the [Protocol Composition Type](../ReferenceManual/Types.xhtml#ID454) section of the [Types](../ReferenceManual/Types.xhtml) chapter to use the new `Protocol1 & Protocol2` syntax.
*   Updated the discussion in the Dynamic Type Expression section to use the new `type(of:)` syntax for dynamic type expressions.
*   Updated the discussion of line control statements to use the `#sourceLocation(file:line:)` syntax in the [Line Control Statement](../ReferenceManual/Statements.xhtml#ID540) section.
*   Updated the discussion in [Functions that Never Return](../ReferenceManual/Declarations.xhtml#ID551) to use the new `Never` type.
*   Added information about playground literals to the [Literal Expression](../ReferenceManual/Expressions.xhtml#ID390) section.
*   Updated the discussion in the [In-Out Parameters](../ReferenceManual/Declarations.xhtml#ID545) section to note that only nonescaping closures can capture in-out parameters.
*   Updated the discussion about default parameters in the [Default Parameter Values](../LanguageGuide/Functions.xhtml#ID169) section, now that they can’t be reordered in function calls.
*   Updated attribute arguments to use a colon in the [Attributes](../ReferenceManual/Attributes.xhtml) chapter.
*   Added information about throwing an error inside the catch block of a rethrowing function to the [Rethrowing Functions and Methods](../ReferenceManual/Declarations.xhtml#ID531) section.
*   Added information about accessing the selector of an Objective-C property’s getter or setter to the [Selector Expression](../ReferenceManual/Expressions.xhtml#ID547) section.
*   Added information to the [Type Alias Declaration](../ReferenceManual/Declarations.xhtml#ID361) section about generic type aliases and using type aliases inside of protocols.
*   Updated the discussion of function types in the [Function Type](../ReferenceManual/Types.xhtml#ID449) section to note that parentheses around the parameter types are required.
*   Updated the [Attributes](../ReferenceManual/Attributes.xhtml) chapter to note that the `@IBAction`, `@IBOutlet`, and `@NSManaged` attributes imply the `@objc` attribute.
*   Added information about the `@GKInspectable` attribute to the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section.
*   Updated the discussion of optional protocol requirements in the [Optional Protocol Requirements](../LanguageGuide/Protocols.xhtml#ID284) section to clarify that they are used only in code that interoperates with Objective-C.
*   Removed the discussion of explicitly using `let` in function parameters from the [Function Declaration](../ReferenceManual/Declarations.xhtml#ID362) section.
*   Removed the discussion of the `Boolean` protocol from the [Statements](../ReferenceManual/Statements.xhtml) chapter, now that the protocol has been removed from the Swift standard library.
*   Corrected the discussion of the `@NSApplicationMain` attribute in the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section.

**2016-03-21**

*   Updated for Swift 2.2.
*   Added information about how to conditionally compile code depending on the version of Swift being used to the [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539) section.
*   Added information about how to distinguish between methods or initializers whose names differ only by the names of their arguments to the [Explicit Member Expression](../ReferenceManual/Expressions.xhtml#ID400) section.
*   Added information about the `#selector` syntax for Objective-C selectors to the [Selector Expression](../ReferenceManual/Expressions.xhtml#ID547) section.
*   Updated the discussion of associated types to use the `associatedtype` keyword in the [Associated Types](../LanguageGuide/Generics.xhtml#ID189) and [Protocol Associated Type Declaration](../ReferenceManual/Declarations.xhtml#ID374) sections.
*   Updated information about initializers that return `nil` before the instance is fully initialized in the [Failable Initializers](../LanguageGuide/Initialization.xhtml#ID224) section.
*   Added information about comparing tuples to the [Comparison Operators](../LanguageGuide/BasicOperators.xhtml#ID70) section.
*   Added information about using keywords as external parameter names to the [Keywords and Punctuation](../ReferenceManual/LexicalStructure.xhtml#ID413) section.
*   Updated the discussion of the `@objc` attribute in the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section to note that enumerations and enumeration cases can use this attribute.
*   Updated the [Operators](../ReferenceManual/LexicalStructure.xhtml#ID418) section with discussion of custom operators that contain a dot.
*   Added a note to the [Rethrowing Functions and Methods](../ReferenceManual/Declarations.xhtml#ID531) section that rethrowing functions can’t directly throw errors.
*   Added a note to the [Property Observers](../LanguageGuide/Properties.xhtml#ID262) section about property observers being called when you pass a property as an in-out parameter.
*   Added a section about error handling to the [A Swift Tour](../GuidedTour/SwiftTour.xhtml) chapter.
*   Updated figures in the [Weak References](../LanguageGuide/AutomaticReferenceCounting.xhtml#ID53) section to show the deallocation process more clearly.
*   Removed discussion of C-style `for` loops, the `++` prefix and postfix operators, and the `--` prefix and postfix operators.
*   Removed discussion of variable function arguments and the special syntax for curried functions.

**2015-10-20**

*   Updated for Swift 2.1.
*   Updated the [String Interpolation](../LanguageGuide/StringsAndCharacters.xhtml#ID292) and [String Literals](../ReferenceManual/LexicalStructure.xhtml#ID417) sections now that string interpolations can contain string literals.
*   Added the [Escaping Closures](../LanguageGuide/Closures.xhtml#ID546) section with information about the `@noescape` attribute.
*   Updated the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) and [Conditional Compilation Block](../ReferenceManual/Statements.xhtml#ID539) sections with information about tvOS.
*   Added information about the behavior of in-out parameters to the [In-Out Parameters](../ReferenceManual/Declarations.xhtml#ID545) section.
*   Added information to the [Capture Lists](../ReferenceManual/Expressions.xhtml#ID544) section about how values specified in closure capture lists are captured.
*   Updated the [Accessing Properties Through Optional Chaining](../LanguageGuide/OptionalChaining.xhtml#ID248) section to clarify how assignment through optional chaining behaves.
*   Improved the discussion of autoclosures in the [Autoclosures](../LanguageGuide/Closures.xhtml#ID543) section.
*   Added an example that uses the `??` operator to the [A Swift Tour](../GuidedTour/SwiftTour.xhtml) chapter.

**2015-09-16**

*   Updated for Swift 2.0.
*   Added information about error handling to the [Error Handling](../LanguageGuide/ErrorHandling.xhtml) chapter, the [Do Statement](../ReferenceManual/Statements.xhtml#ID533) section, the [Throw Statement](../ReferenceManual/Statements.xhtml#ID518) section, the [Defer Statement](../ReferenceManual/Statements.xhtml#ID532) section, and the [Try Operator](../ReferenceManual/Expressions.xhtml#ID516) section.
*   Updated the [Representing and Throwing Errors](../LanguageGuide/ErrorHandling.xhtml#ID509) section, now that all types can conform to the `ErrorType` protocol.
*   Added information about the new `try?` keyword to the [Converting Errors to Optional Values](../LanguageGuide/ErrorHandling.xhtml#ID542) section.
*   Added information about recursive enumerations to the [Recursive Enumerations](../LanguageGuide/Enumerations.xhtml#ID536) section of the [Enumerations](../LanguageGuide/Enumerations.xhtml) chapter and the [Enumerations with Cases of Any Type](../ReferenceManual/Declarations.xhtml#ID365) section of the [Declarations](../ReferenceManual/Declarations.xhtml) chapter.
*   Added information about API availability checking to the [Checking API Availability](../LanguageGuide/ControlFlow.xhtml#ID523) section of the [Control Flow](../LanguageGuide/ControlFlow.xhtml) chapter and the [Availability Condition](../ReferenceManual/Statements.xhtml#ID522) section of the [Statements](../ReferenceManual/Statements.xhtml) chapter.
*   Added information about the new `guard` statement to the [Early Exit](../LanguageGuide/ControlFlow.xhtml#ID525) section of the [Control Flow](../LanguageGuide/ControlFlow.xhtml) chapter and the [Guard Statement](../ReferenceManual/Statements.xhtml#ID524) section of the [Statements](../ReferenceManual/Statements.xhtml) chapter.
*   Added information about protocol extensions to the [Protocol Extensions](../LanguageGuide/Protocols.xhtml#ID521) section of the [Protocols](../LanguageGuide/Protocols.xhtml) chapter.
*   Added information about access control for unit testing to the [Access Levels for Unit Test Targets](../LanguageGuide/AccessControl.xhtml#ID519) section of the [Access Control](../LanguageGuide/AccessControl.xhtml) chapter.
*   Added information about the new optional pattern to the [Optional Pattern](../ReferenceManual/Patterns.xhtml#ID520) section of the [Patterns](../ReferenceManual/Patterns.xhtml) chapter.
*   Updated the [Repeat-While](../LanguageGuide/ControlFlow.xhtml#ID126) section with information about the `repeat`\-`while` loop.
*   Updated the [Strings and Characters](../LanguageGuide/StringsAndCharacters.xhtml) chapter, now that `String` no longer conforms to the `CollectionType` protocol from the Swift standard library.
*   Added information about the new Swift standard library `print(_:separator:terminator)` function to the [Printing Constants and Variables](../LanguageGuide/TheBasics.xhtml#ID314) section.
*   Added information about the behavior of enumeration cases with `String` raw values to the [Implicitly Assigned Raw Values](../LanguageGuide/Enumerations.xhtml#ID535) section of the [Enumerations](../LanguageGuide/Enumerations.xhtml) chapter and the [Enumerations with Cases of a Raw-Value Type](../ReferenceManual/Declarations.xhtml#ID366) section of the [Declarations](../ReferenceManual/Declarations.xhtml) chapter.
*   Added information about the `@autoclosure` attribute—including its `@autoclosure(escaping)` form—to the [Autoclosures](../LanguageGuide/Closures.xhtml#ID543) section.
*   Updated the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section with information about the `@available` and `@warn_unused_result` attributes.
*   Updated the [Type Attributes](../ReferenceManual/Attributes.xhtml#ID350) section with information about the `@convention` attribute.
*   Added an example of using multiple optional bindings with a `where` clause to the [Optional Binding](../LanguageGuide/TheBasics.xhtml#ID333) section.
*   Added information to the [String Literals](../ReferenceManual/LexicalStructure.xhtml#ID417) section about how concatenating string literals using the `+` operator happens at compile time.
*   Added information to the [Metatype Type](../ReferenceManual/Types.xhtml#ID455) section about comparing metatype values and using them to construct instances with initializer expressions.
*   Added a note to the [Debugging with Assertions](../LanguageGuide/TheBasics.xhtml#ID336) section about when user-defined assertions are disabled.
*   Updated the discussion of the `@NSManaged` attribute in the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section, now that the attribute can be applied to certain instance methods.
*   Updated the [Variadic Parameters](../LanguageGuide/Functions.xhtml#ID171) section, now that variadic parameters can be declared in any position in a function’s parameter list.
*   Added information to the [Overriding a Failable Initializer](../LanguageGuide/Initialization.xhtml#ID229) section about how a nonfailable initializer can delegate up to a failable initializer by force-unwrapping the result of the superclass’s initializer.
*   Added information about using enumeration cases as functions to the [Enumerations with Cases of Any Type](../ReferenceManual/Declarations.xhtml#ID365) section.
*   Added information about explicitly referencing an initializer to the [Initializer Expression](../ReferenceManual/Expressions.xhtml#ID399) section.
*   Added information about build configuration and line control statements to the [Compiler Control Statements](../ReferenceManual/Statements.xhtml#ID538) section.
*   Added a note to the [Metatype Type](../ReferenceManual/Types.xhtml#ID455) section about constructing class instances from metatype values.
*   Added a note to the [Weak References](../LanguageGuide/AutomaticReferenceCounting.xhtml#ID53) section about weak references being unsuitable for caching.
*   Updated a note in the [Type Properties](../LanguageGuide/Properties.xhtml#ID264) section to mention that stored type properties are lazily initialized.
*   Updated the [Capturing Values](../LanguageGuide/Closures.xhtml#ID103) section to clarify how variables and constants are captured in closures.
*   Updated the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section to describe when you can apply the `@objc` attribute to classes.
*   Added a note to the [Handling Errors](../LanguageGuide/ErrorHandling.xhtml#ID512) section about the performance of executing a `throw` statement. Added similar information about the `do` statement in the [Do Statement](../ReferenceManual/Statements.xhtml#ID533) section.
*   Updated the [Type Properties](../LanguageGuide/Properties.xhtml#ID264) section with information about stored and computed type properties for classes, structures, and enumerations.
*   Updated the [Break Statement](../ReferenceManual/Statements.xhtml#ID441) section with information about labeled break statements.
*   Updated a note in the [Property Observers](../LanguageGuide/Properties.xhtml#ID262) section to clarify the behavior of `willSet` and `didSet` observers.
*   Added a note to the [Access Levels](../LanguageGuide/AccessControl.xhtml#ID5) section with information about the scope of `private` access.
*   Added a note to the [Weak References](../LanguageGuide/AutomaticReferenceCounting.xhtml#ID53) section about the differences in weak references between garbage collected systems and ARC.
*   Updated the [Special Characters in String Literals](../LanguageGuide/StringsAndCharacters.xhtml#ID295) section with a more precise definition of Unicode scalars.

**2015-04-08**

*   Updated for Swift 1.2.
*   Swift now has a native `Set` collection type. For more information, see [Sets](../LanguageGuide/CollectionTypes.xhtml#ID484).
*   `@autoclosure` is now an attribute of the parameter declaration, not its type. There is also a new `@noescape` parameter declaration attribute. For more information, see [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348).
*   Type methods and properties now use the `static` keyword as a declaration modifier. For more information see [Type Variable Properties](../ReferenceManual/Declarations.xhtml#ID483).
*   Swift now includes the `as?` and `as!` failable downcast operators. For more information, see [Checking for Protocol Conformance](../LanguageGuide/Protocols.xhtml#ID283).
*   Added a new guide section about [String Indices](../LanguageGuide/StringsAndCharacters.xhtml#ID534).
*   Removed the overflow division (`&/`) and overflow remainder (`&%`) operators from [Overflow Operators](../LanguageGuide/AdvancedOperators.xhtml#ID37).
*   Updated the rules for constant and constant property declaration and initialization. For more information, see [Constant Declaration](../ReferenceManual/Declarations.xhtml#ID355).
*   Updated the definition of Unicode scalars in string literals. See [Special Characters in String Literals](../LanguageGuide/StringsAndCharacters.xhtml#ID295).
*   Updated [Range Operators](../LanguageGuide/BasicOperators.xhtml#ID73) to note that a half-open range with the same start and end index will be empty.
*   Updated [Closures Are Reference Types](../LanguageGuide/Closures.xhtml#ID104) to clarify the capturing rules for variables.
*   Updated [Value Overflow](../LanguageGuide/AdvancedOperators.xhtml#ID38) to clarify the overflow behavior of signed and unsigned integers
*   Updated [Protocol Declaration](../ReferenceManual/Declarations.xhtml#ID369) to clarify protocol declaration scope and members.
*   Updated [Defining a Capture List](../LanguageGuide/AutomaticReferenceCounting.xhtml#ID58) to clarify the syntax for weak and unowned references in closure capture lists.
*   Updated [Operators](../ReferenceManual/LexicalStructure.xhtml#ID418) to explicitly mention examples of supported characters for custom operators, such as those in the Mathematical Operators, Miscellaneous Symbols, and Dingbats Unicode blocks.
*   Constants can now be declared without being initialized in local function scope. They must have a set value before first use. For more information, see [Constant Declaration](../ReferenceManual/Declarations.xhtml#ID355).
*   In an initializer, constant properties can now only assign a value once. For more information, see [Assigning Constant Properties During Initialization](../LanguageGuide/Initialization.xhtml#ID212).
*   Multiple optional bindings can now appear in a single `if` statement as a comma-separated list of assignment expressions. For more information, see [Optional Binding](../LanguageGuide/TheBasics.xhtml#ID333).
*   An [Optional-Chaining Expression](../ReferenceManual/Expressions.xhtml#ID405) must appear within a postfix expression.
*   Protocol casts are no longer limited to `@objc` protocols.
*   Type casts that can fail at runtime now use the `as?` or `as!` operator, and type casts that are guaranteed not to fail use the `as` operator. For more information, see [Type-Casting Operators](../ReferenceManual/Expressions.xhtml#ID388).

**2014-10-16**

*   Updated for Swift 1.1.
*   Added a full guide to [Failable Initializers](../LanguageGuide/Initialization.xhtml#ID224).
*   Added a description of [Failable Initializer Requirements](../LanguageGuide/Protocols.xhtml#ID274) for protocols.
*   Constants and variables of type `Any` can now contain function instances. Updated the example in [Type Casting for Any and AnyObject](../LanguageGuide/TypeCasting.xhtml#ID342) to show how to check for and cast to a function type within a `switch` statement.
*   Enumerations with raw values now have a `rawValue` property rather than a `toRaw()` method and a failable initializer with a `rawValue` parameter rather than a `fromRaw()` method. For more information, see [Raw Values](../LanguageGuide/Enumerations.xhtml#ID149) and [Enumerations with Cases of a Raw-Value Type](../ReferenceManual/Declarations.xhtml#ID366).
*   Added a new reference section about [Failable Initializers](../ReferenceManual/Declarations.xhtml#ID376), which can trigger initialization failure.
*   Custom operators can now contain the `?` character. Updated the [Operators](../ReferenceManual/LexicalStructure.xhtml#ID418) reference to describe the revised rules. Removed a duplicate description of the valid set of operator characters from [Custom Operators](../LanguageGuide/AdvancedOperators.xhtml#ID46).

**2014-08-18**

*   New document that describes Swift 1.0, Apple’s new programming language for building iOS and OS X apps.
*   Added a new section about [Initializer Requirements](../LanguageGuide/Protocols.xhtml#ID272) in protocols.
*   Added a new section about [Class-Only Protocols](../LanguageGuide/Protocols.xhtml#ID281).
*   [Assertions and Preconditions](../LanguageGuide/TheBasics.xhtml#ID335) can now use string interpolation. Removed a note to the contrary.
*   Updated the [Concatenating Strings and Characters](../LanguageGuide/StringsAndCharacters.xhtml#ID291) section to reflect the fact that `String` and `Character` values can no longer be combined with the addition operator (`+`) or addition assignment operator (`+=`). These operators are now used only with `String` values. Use the `String` type’s `append(_:)` method to append a single `Character` value onto the end of a string.
*   Added information about the `availability` attribute to the [Declaration Attributes](../ReferenceManual/Attributes.xhtml#ID348) section.
*   [Optionals](../LanguageGuide/TheBasics.xhtml#ID330) no longer implicitly evaluate to `true` when they have a value and `false` when they do not, to avoid confusion when working with optional `Bool` values. Instead, make an explicit check against `nil` with the `==` or `!=` operators to find out if an optional contains a value.
*   Swift now has a [Nil-Coalescing Operator](../LanguageGuide/BasicOperators.xhtml#ID72) (`a ?? b`), which unwraps an optional’s value if it exists, or returns a default value if the optional is `nil`.
*   Updated and expanded the [Comparing Strings](../LanguageGuide/StringsAndCharacters.xhtml#ID298) section to reflect and demonstrate that string and character comparison and prefix / suffix comparison are now based on Unicode canonical equivalence of extended grapheme clusters.
*   You can now try to set a property’s value, assign to a subscript, or call a mutating method or operator through [Optional Chaining](../LanguageGuide/OptionalChaining.xhtml). The information about [Accessing Properties Through Optional Chaining](../LanguageGuide/OptionalChaining.xhtml#ID248) has been updated accordingly, and the examples of checking for method call success in [Calling Methods Through Optional Chaining](../LanguageGuide/OptionalChaining.xhtml#ID249) have been expanded to show how to check for property setting success.
*   Added a new section about [Accessing Subscripts of Optional Type](../LanguageGuide/OptionalChaining.xhtml#ID251) through optional chaining.
*   Updated the [Accessing and Modifying an Array](../LanguageGuide/CollectionTypes.xhtml#ID110) section to note that you can no longer append a single item to an array with the `+=` operator. Instead, use the `append(_:)` method, or append a single-item array with the `+=` operator.
*   Added a note that the start value `a` for the [Range Operators](../LanguageGuide/BasicOperators.xhtml#ID73) `a...b` and `a..<b` must not be greater than the end value `b`.
*   Rewrote the [Inheritance](../LanguageGuide/Inheritance.xhtml) chapter to remove its introductory coverage of initializer overrides. This chapter now focuses more on the addition of new functionality in a subclass, and the modification of existing functionality with overrides. The chapter’s example of [Overriding Property Getters and Setters](../LanguageGuide/Inheritance.xhtml#ID200) has been rewritten to show how to override a `description` property. (The examples of modifying an inherited property’s default value in a subclass initializer have been moved to the [Initialization](../LanguageGuide/Initialization.xhtml) chapter.)
*   Updated the [Initializer Inheritance and Overriding](../LanguageGuide/Initialization.xhtml#ID221) section to note that overrides of a designated initializer must now be marked with the `override` modifier.
*   Updated the [Required Initializers](../LanguageGuide/Initialization.xhtml#ID231) section to note that the `required` modifier is now written before every subclass implementation of a required initializer, and that the requirements for required initializers can now be satisfied by automatically inherited initializers.
*   Infix [Operator Methods](../LanguageGuide/AdvancedOperators.xhtml#ID42) no longer require the `@infix` attribute.
*   The `@prefix` and `@postfix` attributes for [Prefix and Postfix Operators](../LanguageGuide/AdvancedOperators.xhtml#ID43) have been replaced by `prefix` and `postfix` declaration modifiers.
*   Added a note about the order in which [Prefix and Postfix Operators](../LanguageGuide/AdvancedOperators.xhtml#ID43) are applied when both a prefix and a postfix operator are applied to the same operand.
*   Operator functions for [Compound Assignment Operators](../LanguageGuide/AdvancedOperators.xhtml#ID44) no longer use the `@assignment` attribute when defining the function.
*   The order in which modifiers are specified when defining [Custom Operators](../LanguageGuide/AdvancedOperators.xhtml#ID46) has changed. You now write `prefix operator` rather than `operator prefix`, for example.
*   Added information about the `dynamic` declaration modifier in [Declaration Modifiers](../ReferenceManual/Declarations.xhtml#ID381).
*   Added information about how type inference works with [Literals](../ReferenceManual/LexicalStructure.xhtml#ID414).
*   Added more information about curried functions.
*   Added a new chapter about [Access Control](../LanguageGuide/AccessControl.xhtml).
*   Updated the [Strings and Characters](../LanguageGuide/StringsAndCharacters.xhtml) chapter to reflect the fact that Swift’s `Character` type now represents a single Unicode extended grapheme cluster. Includes a new section on [Extended Grapheme Clusters](../LanguageGuide/StringsAndCharacters.xhtml#ID296) and more information about [Unicode Scalar Values](../LanguageGuide/StringsAndCharacters.xhtml#ID294) and [Comparing Strings](../LanguageGuide/StringsAndCharacters.xhtml#ID298).
*   Updated the [String Literals](../LanguageGuide/StringsAndCharacters.xhtml#ID286) section to note that Unicode scalars inside string literals are now written as `\u{n}`, where `n` is a hexadecimal number between 0 and 10FFFF, the range of Unicode’s codespace.
*   The `NSString` `length` property is now mapped onto Swift’s native `String` type as `utf16Count`, not `utf16count`.
*   Swift’s native `String` type no longer has an `uppercaseString` or `lowercaseString` property. The corresponding section in [Strings and Characters](../LanguageGuide/StringsAndCharacters.xhtml) has been removed, and various code examples have been updated.
*   Added a new section about [Initializer Parameters Without Argument Labels](../LanguageGuide/Initialization.xhtml#ID210).
*   Added a new section about [Required Initializers](../LanguageGuide/Initialization.xhtml#ID231).
*   Added a new section about [Optional Tuple Return Types](../LanguageGuide/Functions.xhtml#ID165).
*   Updated the [Type Annotations](../LanguageGuide/TheBasics.xhtml#ID312) section to note that multiple related variables can be defined on a single line with one type annotation.
*   The `@optional`, `@lazy`, `@final`, and `@required` attributes are now the `optional`, `lazy`, `final`, and `required` [Declaration Modifiers](../ReferenceManual/Declarations.xhtml#ID381).
*   Updated the entire book to refer to `..<` as the [Half-Open Range Operator](../LanguageGuide/BasicOperators.xhtml#ID75) (rather than the “half-closed range operator”).
*   Updated the [Accessing and Modifying a Dictionary](../LanguageGuide/CollectionTypes.xhtml#ID116) section to note that `Dictionary` now has a Boolean `isEmpty` property.
*   Clarified the full list of characters that can be used when defining [Custom Operators](../LanguageGuide/AdvancedOperators.xhtml#ID46).
*   `nil` and the Booleans `true` and `false` are now [Literals](../ReferenceManual/LexicalStructure.xhtml#ID414).
*   Swift’s `Array` type now has full value semantics. Updated the information about [Mutability of Collections](../LanguageGuide/CollectionTypes.xhtml#ID106) and [Arrays](../LanguageGuide/CollectionTypes.xhtml#ID107) to reflect the new approach. Also clarified the assignment and copy behavior for strings arrays and dictionaries.
*   [Array Type Shorthand Syntax](../LanguageGuide/CollectionTypes.xhtml#ID108) is now written as `[SomeType]` rather than `SomeType[]`.
*   Added a new section about [Dictionary Type Shorthand Syntax](../LanguageGuide/CollectionTypes.xhtml#ID114), which is written as `[KeyType: ValueType]`.
*   Added a new section about [Hash Values for Set Types](../LanguageGuide/CollectionTypes.xhtml#ID493).
*   Examples of [Closure Expressions](../LanguageGuide/Closures.xhtml#ID95) now use the global `sorted(_:_:)` function rather than the global `sort(_:_:)` function, to reflect the new array value semantics.
*   Updated the information about [Memberwise Initializers for Structure Types](../LanguageGuide/Initialization.xhtml#ID214) to clarify that the memberwise structure initializer is made available even if a structure’s stored properties do not have default values.
*   Updated to `..<` rather than `..` for the [Half-Open Range Operator](../LanguageGuide/BasicOperators.xhtml#ID75).
*   Added an example of [Extending a Generic Type](../LanguageGuide/Generics.xhtml#ID185).
