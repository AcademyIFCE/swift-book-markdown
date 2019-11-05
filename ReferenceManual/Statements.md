 Statements  

Statements
==========

In Swift, there are three kinds of statements: simple statements, compiler control statements, and control flow statements. Simple statements are the most common and consist of either an expression or a declaration. Compiler control statements allow the program to change aspects of the compiler’s behavior and include a conditional compilation block and a line control statement.

Control flow statements are used to control the flow of execution in a program. There are several types of control flow statements in Swift, including loop statements, branch statements, and control transfer statements. Loop statements allow a block of code to be executed repeatedly, branch statements allow a certain block of code to be executed only when certain conditions are met, and control transfer statements provide a way to alter the order in which code is executed. In addition, Swift provides a `do` statement to introduce scope, and catch and handle errors, and a `defer` statement for running cleanup actions just before the current scope exits.

A semicolon (`;`) can optionally appear after any statement and is used to separate multiple statements if they appear on the same line.

>**Grammar of a statement**
>
>statement → [expression](../ReferenceManual/Expressions.md#grammar_expression) `;`<sub>opt</sub>
>
>statement → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) `;`<sub>opt</sub>
>
>statement → [loop-statement](../ReferenceManual/Statements.md#grammar_loop-statement) `;`<sub>opt</sub>
>
>statement → [branch-statement](../ReferenceManual/Statements.md#grammar_branch-statement) `;`<sub>opt</sub>
>
>statement → [labeled-statement](../ReferenceManual/Statements.md#grammar_labeled-statement) `;`<sub>opt</sub>
>
>statement → [control-transfer-statement](../ReferenceManual/Statements.md#grammar_control-transfer-statement) `;`<sub>opt</sub>
>
>statement → [defer-statement](../ReferenceManual/Statements.md#grammar_defer-statement) `;`<sub>opt</sub>
>
>statement → [do-statement](../ReferenceManual/Statements.md#grammar_do-statement) `;`<sub>opt</sub>
>
>statement → [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)
>
>statements → [statement](../ReferenceManual/Statements.md#grammar_statement) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>

Loop Statements
---------------

Loop statements allow a block of code to be executed repeatedly, depending on the conditions specified in the loop. Swift has three loop statements: a `for`-`in` statement, a `while` statement, and a `repeat`-`while` statement.

Control flow in a loop statement can be changed by a `break` statement and a `continue` statement and is discussed in [Break Statement](#break-statement) and [Continue Statement](#continue-statement) below.

>**Grammar of a loop statement**
>
>loop-statement → [for-in-statement](../ReferenceManual/Statements.md#grammar_for-in-statement)
>
>loop-statement → [while-statement](../ReferenceManual/Statements.md#grammar_while-statement)
>
>loop-statement → [repeat-while-statement](../ReferenceManual/Statements.md#grammar_repeat-while-statement)

### For-In Statement

A `for`-`in` statement allows a block of code to be executed once for each item in a collection (or any type) that conforms to the [`Sequence`](https://developer.apple.com/documentation/swift/sequence) protocol.

A `for`-`in` statement has the following form:

```swift
for (item) in (collection) {
  (statements)
}
```

The `makeIterator()` method is called on the *collection* expression to obtain a value of an iterator type—that is, a type that conforms to the [`IteratorProtocol`](https://developer.apple.com/documentation/swift/iteratorprotocol) protocol. The program begins executing a loop by calling the `next()` method on the iterator. If the value returned is not `nil`, it is assigned to the *item* pattern, the program executes the *statements*, and then continues execution at the beginning of the loop. Otherwise, the program does not perform assignment or execute the *statements*, and it is finished executing the `for`-`in` statement.

>**Grammar of a for-in statement**
>
>for-in-statement → `for` `case`opt [pattern](../ReferenceManual/Patterns.md#grammar_pattern) `in` [expression](../ReferenceManual/Expressions.md#grammar_expression) [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

### While Statement

A `while` statement allows a block of code to be executed repeatedly, as long as a condition remains true.

A `while` statement has the following form:

```swift
while (condition) {
  (statements)
}
```

A `while` statement is executed as follows:

1.  The *condition* is evaluated.
    
    If `true`, execution continues to step 2. If `false`, the program is finished executing the `while` statement.
    
2.  The program executes the *statements*, and execution returns to step 1.
    

Because the value of the *condition* is evaluated before the *statements* are executed, the *statements* in a `while` statement can be executed zero or more times.

The value of the *condition* must be of type `Bool` or a type bridged to `Bool`. The condition can also be an optional binding declaration, as discussed in [Optional Binding](../LanguageGuide/TheBasics.md#optional-binding).

>**Grammar of a while statement**
>
>while-statement → `while` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list) [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>condition-list → [condition](../ReferenceManual/Statements.md#grammar_condition) | [condition](../ReferenceManual/Statements.md#grammar_condition) `,` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list)
>
>condition → [expression](../ReferenceManual/Expressions.md#grammar_expression) | [availability-condition](../ReferenceManual/Statements.md#grammar_availability-condition) | [case-condition](../ReferenceManual/Statements.md#grammar_case-condition) | [optional-binding-condition](../ReferenceManual/Statements.md#grammar_optional-binding-condition)
>
>case-condition → `case` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer)
>
>optional-binding-condition → `let` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer) | `var` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer)

### Repeat-While Statement

A `repeat`-`while` statement allows a block of code to be executed one or more times, as long as a condition remains true.

A `repeat`-`while` statement has the following form:

```swift
repeat {
  (statements)
} while (condition)
```

A `repeat`-`while` statement is executed as follows:

1.  The program executes the *statements*, and execution continues to step 2.
    
2.  The *condition* is evaluated.
    
    If `true`, execution returns to step 1. If `false`, the program is finished executing the `repeat`-`while` statement.
    

Because the value of the *condition* is evaluated after the *statements* are executed, the *statements* in a `repeat`-`while` statement are executed at least once.

The value of the *condition* must be of type `Bool` or a type bridged to `Bool`. The condition can also be an optional binding declaration, as discussed in [Optional Binding](../LanguageGuide/TheBasics.md#Ioptional-binding).

>**Grammar of a repeat-while statement**
>
>repeat-while-statement → `repeat` [code-block](../ReferenceManual/Declarations.md#grammar_code-block) `while` [expression](../ReferenceManual/Expressions.md#grammar_expression)

Branch Statements
-----------------

Branch statements allow the program to execute certain parts of code depending on the value of one or more conditions. The values of the conditions specified in a branch statement control how the program branches and, therefore, what block of code is executed. Swift has three branch statements: an `if` statement, a `guard` statement, and a `switch` statement.

Control flow in an `if` statement or a `switch` statement can be changed by a `break` statement and is discussed in [Break Statement](#break-statement) below.

>**Grammar of a branch statement**
>
>branch-statement → [if-statement](../ReferenceManual/Statements.md#grammar_if-statement)
>
>branch-statement → [guard-statement](../ReferenceManual/Statements.md#grammar_guard-statement)
>
>branch-statement → [switch-statement](../ReferenceManual/Statements.md#grammar_switch-statement)

### If Statement

An `if` statement is used for executing code based on the evaluation of one or more conditions.

There are two basic forms of an `if` statement. In each form, the opening and closing braces are required.

The first form allows code to be executed only when a condition is true and has the following form:

```swift
if (condition) {
  (statements)
}
```

The second form of an `if` statement provides an additional *else clause* (introduced by the `else` keyword) and is used for executing one part of code when the condition is true and another part of code when the same condition is false. When a single else clause is present, an `if` statement has the following form:

```swift
if (condition) {
  (statements to execute if condition is true)
} else {
  (statements to execute if condition is false)
}
```

The else clause of an `if` statement can contain another `if` statement to test more than one condition. An `if` statement chained together in this way has the following form:

```swift
if (condition 1) {
  (statements to execute if condition 1 is true)
} else if (condition 2) {
  (statements to execute if condition 2 is true)
} else {
  (statements to execute if both conditions are false)
}
```

The value of any condition in an `if` statement must be of type `Bool` or a type bridged to `Bool`. The condition can also be an optional binding declaration, as discussed in [Optional Binding](../LanguageGuide/TheBasics.md#optional-binding).

>**Grammar of an if statement**
>
>if-statement → `if` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list) [code-block](../ReferenceManual/Declarations.md#grammar_code-block) [else-clause](../ReferenceManual/Statements.md#grammar_else-clause) <sub>opt</sub>
>
>else-clause → `else` [code-block](../ReferenceManual/Declarations.md#grammar_code-block) | `else` [if-statement](../ReferenceManual/Statements.md#grammar_if-statement)

### Guard Statement

A `guard` statement is used to transfer program control out of a scope if one or more conditions aren’t met.

A `guard` statement has the following form:

```swift
guard (condition) else {
  (statements)
}
```

The value of any condition in a `guard` statement must be of type `Bool` or a type bridged to `Bool`. The condition can also be an optional binding declaration, as discussed in [Optional Binding](../LanguageGuide/TheBasics.md#optional-binding).

Any constants or variables assigned a value from an optional binding declaration in a `guard` statement condition can be used for the rest of the guard statement’s enclosing scope.

The `else` clause of a `guard` statement is required, and must either call a function with the `Never` return type or transfer program control outside the guard statement’s enclosing scope using one of the following statements:

*   `return`
    
*   `break`
    
*   `continue`
    
*   `throw`
    

Control transfer statements are discussed in [Control Transfer Statements](#control-transfer-statements) below. For more information on functions with the `Never` return type, see [Functions that Never Return](Declarations.md#functions-that-never-return).

>**Grammar of a guard statement**
>
>guard-statement → `guard` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list) `else` [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

### Switch Statement

A `switch` statement allows certain blocks of code to be executed depending on the value of a control expression.

A `switch` statement has the following form:

```swift
switch (control expression) {
case (pattern 1):
  (statements)
case (pattern 2) where (condition):
  (statements)
case (pattern 3) where (condition),
     (pattern 4) where (condition):
  (statements)
default:
  (statements)
}
```

The *control expression* of the `switch` statement is evaluated and then compared with the patterns specified in each case. If a match is found, the program executes the *statements* listed within the scope of that case. The scope of each case can’t be empty. As a result, you must include at least one statement following the colon (`:`) of each case label. Use a single `break` statement if you don’t intend to execute any code in the body of a matched case.

The values of expressions your code can branch on are very flexible. For example, in addition to the values of scalar types, such as integers and characters, your code can branch on the values of any type, including floating-point numbers, strings, tuples, instances of custom classes, and optionals. The value of the *control expression* can even be matched to the value of a case in an enumeration and checked for inclusion in a specified range of values. For examples of how to use these various types of values in `switch` statements, see [Switch](../LanguageGuide/ControlFlow.md#switch) in [Control Flow](../LanguageGuide/ControlFlow.md).

A `switch` case can optionally contain a `where` clause after each pattern. A *where clause* is introduced by the `where` keyword followed by an expression, and is used to provide an additional condition before a pattern in a case is considered matched to the *control expression*. If a `where` clause is present, the *statements* within the relevant case are executed only if the value of the *control expression* matches one of the patterns of the case and the expression of the `where` clause evaluates to `true`. For example, a *control expression* matches the case in the example below only if it is a tuple that contains two elements of the same value, such as `(1, 1)`.

```swift
case let (x, y) where x == y:
```

As the above example shows, patterns in a case can also bind constants using the `let` keyword (they can also bind variables using the `var` keyword). These constants (or variables) can then be referenced in a corresponding `where` clause and throughout the rest of the code within the scope of the case. If the case contains multiple patterns that match the control expression, all of the patterns must contain the same constant or variable bindings, and each bound variable or constant must have the same type in all of the case’s patterns.

A `switch` statement can also include a default case, introduced by the `default` keyword. The code within a default case is executed only if no other cases match the control expression. A `switch` statement can include only one default case, which must appear at the end of the `switch` statement.

Although the actual execution order of pattern-matching operations, and in particular the evaluation order of patterns in cases, is unspecified, pattern matching in a `switch` statement behaves as if the evaluation is performed in source order—that is, the order in which they appear in source code. As a result, if multiple cases contain patterns that evaluate to the same value, and thus can match the value of the control expression, the program executes only the code within the first matching case in source order.

#### Switch Statements Must Be Exhaustive

In Swift, every possible value of the control expression’s type must match the value of at least one pattern of a case. When this simply isn’t feasible (for example, when the control expression’s type is `Int`), you can include a default case to satisfy the requirement.

#### Switching Over Future Enumeration Cases

A *nonfrozen enumeration* is a special kind of enumeration that may gain new enumeration cases in the future—even after you compile and ship an app. Switching over a nonfrozen enumeration requires extra consideration. When a library’s authors mark an enumeration as nonfrozen, they reserve the right to add new enumeration cases, and any code that interacts with that enumeration *must* be able to handle those future cases without being recompiled. Code that’s compiled in library evolution mode, code in the standard library, Swift overlays for Apple frameworks, and C and Objective-C code can declare nonfrozen enumerations. For information about frozen and nonfrozen enumerations, see [frozen](Attributes.md#frozen).

When switching over a nonfrozen enumeration value, you always need to include a default case, even if every case of the enumeration already has a corresponding switch case. You can apply the `@unknown` attribute to the default case, which indicates that the default case should match only enumeration cases that are added in the future. Swift produces a warning if the default case matches any enumeration case that is known at compiler time. This future warning informs you that the library author added a new case to the enumeration that doesn’t have a corresponding switch case.

The following example switches over all three existing cases of the standard library’s [`Mirror.AncestorRepresentation`](https://developer.apple.com/documentation/swift/mirror/ancestorrepresentation) enumeration. If you add additional cases in the future, the compiler generates a warning to indicate that you need to update the switch statement to take the new cases into account.

```swift
let representation: Mirror.AncestorRepresentation = .generated
switch representation {
case .customized:
  print("Use the nearest ancestor’s implementation.")
case .generated:
  print("Generate a default mirror for all ancestor classes.")
case .suppressed:
  print("Suppress the representation of all ancestor classes.")
@unknown default:
  print("Use a representation that was unknown when this code was compiled.")
}
// Prints "Generate a default mirror for all ancestor classes."
```

#### Execution Does Not Fall Through Cases Implicitly

After the code within a matched case has finished executing, the program exits from the `switch` statement. Program execution does not continue or “fall through” to the next case or default case. That said, if you want execution to continue from one case to the next, explicitly include a `fallthrough` statement, which simply consists of the `fallthrough` keyword, in the case from which you want execution to continue. For more information about the `fallthrough` statement, see [Fallthrough Statement](#fallthrough-statement) below.

>**Grammar of a switch statement**
>
>switch-statement → `switch` [expression](../ReferenceManual/Expressions.md#grammar_expression) `{` [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub> `}`
>
>switch-cases → [switch-case](../ReferenceManual/Statements.md#grammar_switch-case) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>
>
>switch-case → [case-label](../ReferenceManual/Statements.md#grammar_case-label) [statements](../ReferenceManual/Statements.md#grammar_statements)
>
>switch-case → [default-label](../ReferenceManual/Statements.md#grammar_default-label) [statements](../ReferenceManual/Statements.md#grammar_statements)
>
>switch-case → [conditional-switch-case](../ReferenceManual/Statements.md#grammar_conditional-switch-case)
>
>case-label → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `case` [case-item-list](../ReferenceManual/Statements.md#grammar_case-item-list) `:`
>
>case-item-list → [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> | [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> `,` [case-item-list](../ReferenceManual/Statements.md#grammar_case-item-list)
>
>default-label → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `default` `:`
>
>where-clause → `where` [where-expression](../ReferenceManual/Statements.md#grammar_where-expression)
>
>where-expression → [expression](../ReferenceManual/Expressions.md#grammar_expression)
>
>conditional-switch-case → [switch-if-directive-clause](../ReferenceManual/Statements.md#grammar_switch-if-directive-clause) [switch-elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_switch-elseif-directive-clauses) <sub>opt</sub> [switch-else-directive-clause](../ReferenceManual/Statements.md#grammar_switch-else-directive-clause) <sub>opt</sub> [endif-directive](../ReferenceManual/Statements.md#grammar_endif-directive)
>
>switch-if-directive-clause → [if-directive](../ReferenceManual/Statements.md#grammar_if-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>
>
>switch-elseif-directive-clauses → [elseif-directive-clause](../ReferenceManual/Statements.md#grammar_elseif-directive-clause) [switch-elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_switch-elseif-directive-clauses) <sub>opt</sub>
>
>switch-elseif-directive-clause → [elseif-directive](../ReferenceManual/Statements.md#grammar_elseif-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>
>
>switch-else-directive-clause → [else-directive](../ReferenceManual/Statements.md#grammar_else-directive) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>

Labeled Statement
-----------------

You can prefix a loop statement, an `if` statement, a `switch` statement, or a `do` statement with a *statement label*, which consists of the name of the label followed immediately by a colon (:). Use statement labels with `break` and `continue` statements to be explicit about how you want to change control flow in a loop statement or a `switch` statement, as discussed in [Break Statement](#break-statement) and [Continue Statement](#continue-statement) below.

The scope of a labeled statement is the entire statement following the statement label. You can nest labeled statements, but the name of each statement label must be unique.

For more information and to see examples of how to use statement labels, see [Labeled Statements](../LanguageGuide/ControlFlow.md#labeled-statements) in [Control Flow](../LanguageGuide/ControlFlow.md).

>**Grammar of a labeled statement**
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [loop-statement](../ReferenceManual/Statements.md#grammar_loop-statement)
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [if-statement](../ReferenceManual/Statements.md#grammar_if-statement)
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [switch-statement](../ReferenceManual/Statements.md#grammar_switch-statement)
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [do-statement](../ReferenceManual/Statements.md#grammar_do-statement)
>
>statement-label → [label-name](../ReferenceManual/Statements.md#grammar_label-name) `:`
>
>label-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

Control Transfer Statements
---------------------------

Control transfer statements can change the order in which code in your program is executed by unconditionally transferring program control from one piece of code to another. Swift has five control transfer statements: a `break` statement, a `continue` statement, a `fallthrough` statement, a `return` statement, and a `throw` statement.

>**Grammar of a control transfer statement**
>
>control-transfer-statement → [break-statement](../ReferenceManual/Statements.md#grammar_break-statement)
>
>control-transfer-statement → [continue-statement](../ReferenceManual/Statements.md#grammar_continue-statement)
>
>control-transfer-statement → [fallthrough-statement](../ReferenceManual/Statements.md#grammar_fallthrough-statement)
>
>control-transfer-statement → [return-statement](../ReferenceManual/Statements.md#grammar_return-statement)
>
>control-transfer-statement → [throw-statement](../ReferenceManual/Statements.md#grammar_throw-statement)

### Break Statement

A `break` statement ends program execution of a loop, an `if` statement, or a `switch` statement. A `break` statement can consist of only the `break` keyword, or it can consist of the `break` keyword followed by the name of a statement label, as shown below.

```swift
break
break (label name)
```

When a `break` statement is followed by the name of a statement label, it ends program execution of the loop, `if` statement, or `switch` statement named by that label.

When a `break` statement is not followed by the name of a statement label, it ends program execution of the `switch` statement or the innermost enclosing loop statement in which it occurs. You can’t use an unlabeled `break` statement to break out of an `if` statement.

In both cases, program control is then transferred to the first line of code following the enclosing loop or `switch` statement, if any.

For examples of how to use a `break` statement, see [Break](../LanguageGuide/ControlFlow.md#break) and [Labeled Statements](../LanguageGuide/ControlFlow.md#labeled-statements) in [Control Flow](../LanguageGuide/ControlFlow.md).

>**Grammar of a break statement**
>
>break-statement → `break` [label-name](../ReferenceManual/Statements.md#grammar_label-name) <sub>opt</sub>

### Continue Statement

A `continue` statement ends program execution of the current iteration of a loop statement but does not stop execution of the loop statement. A `continue` statement can consist of only the `continue` keyword, or it can consist of the `continue` keyword followed by the name of a statement label, as shown below.

```swift
continue
continue (label name)
```

When a `continue` statement is followed by the name of a statement label, it ends program execution of the current iteration of the loop statement named by that label.

When a `continue` statement is not followed by the name of a statement label, it ends program execution of the current iteration of the innermost enclosing loop statement in which it occurs.

In both cases, program control is then transferred to the condition of the enclosing loop statement.

In a `for` statement, the increment expression is still evaluated after the `continue` statement is executed, because the increment expression is evaluated after the execution of the loop’s body.

For examples of how to use a `continue` statement, see [Continue](../LanguageGuide/ControlFlow.md#continue) and [Labeled Statements](../LanguageGuide/ControlFlow.md#labeled-statements) in [Control Flow](../LanguageGuide/ControlFlow.md).

>**Grammar of a continue statement**
>
>continue-statement → `continue` [label-name](../ReferenceManual/Statements.md#grammar_label-name) opt

### Fallthrough Statement

A `fallthrough` statement consists of the `fallthrough` keyword and occurs only in a case block of a `switch` statement. A `fallthrough` statement causes program execution to continue from one case in a `switch` statement to the next case. Program execution continues to the next case even if the patterns of the case label do not match the value of the `switch` statement’s control expression.

A `fallthrough` statement can appear anywhere inside a `switch` statement, not just as the last statement of a case block, but it can’t be used in the final case block. It also cannot transfer control into a case block whose pattern contains value binding patterns.

For an example of how to use a `fallthrough` statement in a `switch` statement, see [Control Transfer Statements](../LanguageGuide/ControlFlow.md#control-transfer-statements) in [Control Flow](../LanguageGuide/ControlFlow.md).

>**Grammar of a fallthrough statement**
>
>fallthrough-statement → `fallthrough`

### Return Statement

A `return` statement occurs in the body of a function or method definition and causes program execution to return to the calling function or method. Program execution continues at the point immediately following the function or method call.

A `return` statement can consist of only the `return` keyword, or it can consist of the `return` keyword followed by an expression, as shown below.

```swift
return
return (expression)
```

When a `return` statement is followed by an expression, the value of the expression is returned to the calling function or method. If the value of the expression does not match the value of the return type declared in the function or method declaration, the expression’s value is converted to the return type before it is returned to the calling function or method.

>**Note**
>
>As described in [Failable Initializers](Declarations.md#failable-initializers), a special form of the `return` statement (`return nil`) can be used in a failable initializer to indicate initialization failure.

When a `return` statement is not followed by an expression, it can be used only to return from a function or method that does not return a value (that is, when the return type of the function or method is `Void` or `()`).

>**Grammar of a return statement**
>
>return-statement → `return` [expression](../ReferenceManual/Expressions.md#grammar_expression) ,<sub>opt</sub>

### Throw Statement

A `throw` statement occurs in the body of a throwing function or method, or in the body of a closure expression whose type is marked with the `throws` keyword.

A `throw` statement causes a program to end execution of the current scope and begin error propagation to its enclosing scope. The error that’s thrown continues to propagate until it’s handled by a `catch` clause of a `do` statement.

A `throw` statement consists of the `throw` keyword followed by an expression, as shown below.

```swift
throw expression
```

The value of the *expression* must have a type that conforms to the `Error` protocol.

For an example of how to use a `throw` statement, see [Propagating Errors Using Throwing Functions](../LanguageGuide/ErrorHandling.md#propagating-errors-using-throwing-functions) in [Error Handling](../LanguageGuide/ErrorHandling.md).

>**Grammar of a throw statement**
>
>throw-statement → `throw` [expression](../ReferenceManual/Expressions.md#grammar_expression)

Defer Statement
---------------

A `defer` statement is used for executing code just before transferring program control outside of the scope that the `defer` statement appears in.

A `defer` statement has the following form:

```swift
defer {
  (statements)
}
```

The statements within the `defer` statement are executed no matter how program control is transferred. This means that a `defer` statement can be used, for example, to perform manual resource management such as closing file descriptors, and to perform actions that need to happen even if an error is thrown.

If multiple `defer` statements appear in the same scope, the order they appear is the reverse of the order they are executed. Executing the last `defer` statement in a given scope first means that statements inside that last `defer` statement can refer to resources that will be cleaned up by other `defer` statements.

```swift
func f() {
  defer { print("First defer") }
  defer { print("Second defer") }
  print("End of function")
}
f()
// Prints "End of function"
// Prints "Second defer"
// Prints "First defer"
```

The statements in the `defer` statement can’t transfer program control outside of the `defer` statement.

>**Grammar of a defer statement**
>
>defer-statement → `defer` [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

Do Statement
------------

The `do` statement is used to introduce a new scope and can optionally contain one or more `catch` clauses, which contain patterns that match against defined error conditions. Variables and constants declared in the scope of a `do` statement can be accessed only within that scope.

A `do` statement in Swift is similar to curly braces (`{}`) in C used to delimit a code block, and does not incur a performance cost at runtime.

A `do` statement has the following form:

```swift
do {
  try (expression)
  (statements)
} catch (pattern 1) {
  statements
} catch (pattern 2) where (condition) {
  (statements)
}
```

Like a `switch` statement, the compiler attempts to infer whether `catch` clauses are exhaustive. If such a determination can be made, the error is considered handled. Otherwise, the error can propagate out of the containing scope, which means the error must be handled by an enclosing `catch` clause or the containing function must be declared with `throws`.

To ensure that an error is handled, use a `catch` clause with a pattern that matches all errors, such as a wildcard pattern (`_`). If a `catch` clause does not specify a pattern, the `catch` clause matches and binds any error to a local constant named `error`. For more information about the patterns you can use in a `catch` clause, see [Patterns](Patterns.md).

To see an example of how to use a `do` statement with several `catch` clauses, see [Handling Errors](../LanguageGuide/ErrorHandling.md#handling-errors).

>**Grammar of a do statement**
>
>do-statement → `do` [code-block](../ReferenceManual/Declarations.md#grammar_code-block) [catch-clauses](../ReferenceManual/Statements.md#grammar_catch-clauses) <sub>opt</sub>
>
>catch-clauses → [catch-clause](../ReferenceManual/Statements.md#grammar_catch-clause) [catch-clauses](../ReferenceManual/Statements.md#grammar_catch-clauses) <sub>opt</sub>
>
>catch-clause → `catch` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) <sub>opt</sub> [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

Compiler Control Statements
---------------------------

Compiler control statements allow the program to change aspects of the compiler’s behavior. Swift has three compiler control statements: a conditional compilation block a line control statement, and a compile-time diagnostic statement.

>**Grammar of a compiler control statement**
>
>compiler-control-statement → [conditional-compilation-block](../ReferenceManual/Statements.md#grammar_conditional-compilation-block)
>
>compiler-control-statement → [line-control-statement](../ReferenceManual/Statements.md#grammar_line-control-statement)
>
>compiler-control-statement → [diagnostic-statement](../ReferenceManual/Statements.md#grammar_diagnostic-statement)

### Conditional Compilation Block

A conditional compilation block allows code to be conditionally compiled depending on the value of one or more compilation conditions.

Every conditional compilation block begins with the `#if` compilation directive and ends with the `#endif` compilation directive. A simple conditional compilation block has the following form:

```swift
#if (compilation condition)
  (statements)
#endif
```

Unlike the condition of an `if` statement, the *compilation condition* is evaluated at compile time. As a result, the *statements* are compiled and executed only if the *compilation condition* evaluates to `true` at compile time.

The *compilation condition* can include the `true` and `false` Boolean literals, an identifier used with the `-D` command line flag, or any of the platform conditions listed in the table below.

| Platform condition  | Valid arguments |
| ------------- | ------------- |
| `os()` | `macOS`, `iOS`, `watchOS`, `tvOS`, `Linux` | 
| `arch()` | `i386`, `x86_64`, `arm`, `arm64` | 
| `swift()` | `>=` or `<` followed by a version number | 
| `compiler()` | `>=` or `<` followed by a version number | 
| `canImport()` | A module name | 
| `targetEnvironment()` | `simulator`, `macCatalyst` | 

The version number for the `swift()` and `compiler()` platform conditions consists of a major number, optional minor number, optional patch number, and so on, with a dot (`.`) separating each part of the version number. There must not be whitespace between the comparison operator and the version number. The version for `compiler()` is the compiler version, regardless of the Swift version setting passed to the compiler. The version for `swift()` is the language version currently being compiled. For example, if you compile your code using the Swift 5 compiler in Swift 4.2 mode, the compiler version is 5 and the language version is 4.2. With those settings, the following code prints all three messages:

```swift
#if compiler(>=5)
  print("Compiled with the Swift 5 compiler or later")
#endif
#if swift(>=4.2)
  print("Compiled in Swift 4.2 mode or later")
#endif
#if compiler(>=5) && swift(<5)
  print("Compiled with the Swift 5 compiler or later in a Swift mode earlier than 5")
#endif
// Prints "Compiled with the Swift 5 compiler or later"
// Prints "Compiled in Swift 4.2 mode or later"
// Prints "Compiled with the Swift 5 compiler or later in a Swift mode earlier than 5"
```

The argument for the `canImport()` platform condition is the name of a module that may not be present on all platforms. This condition tests whether it’s possible to import the module, but doesn’t actually import it. If the module is present, the platform condition returns `true`; otherwise, it returns `false`.

The `targetEnvironment()` platform condition returns `true` when code is compiled for a simulator; otherwise, it returns `false`.

>**Note**
>
>The `arch(arm)` platform condition does not return `true` for ARM 64 devices. The `arch(i386)` platform condition returns `true` when code is compiled for the 32–bit iOS simulator.

You can combine compilation conditions using the logical operators `&&`, `||`, and `!` and use parentheses for grouping. These operators have the same associativity and precedence as the logical operators that are used to combine ordinary Boolean expressions.

Similar to an `if` statement, you can add multiple conditional branches to test for different compilation conditions. You can add any number of additional branches using `#elseif` clauses. You can also add a final additional branch using an `#else` clause. Conditional compilation blocks that contain multiple branches have the following form:

```swift
#if (compilation condition 1)
  (statements to compile if compilation condition 1 is true)
#elseif (compilation condition 2)
  (statements to compile if compilation condition 2 is true)
#else
  (statements to compile if both compilation conditions are false)
#endif
```

>**Note**
>
>Each statement in the body of a conditional compilation block is parsed even if it’s not compiled. However, there is an exception if the compilation condition includes a `swift()` platform condition: The statements are parsed only if the compiler’s version of Swift matches what is specified in the platform condition. This exception ensures that an older compiler doesn’t attempt to parse syntax introduced in a newer version of Swift.

>**Grammar of a conditional compilation block**
>
>conditional-compilation-block → [if-directive-clause](../ReferenceManual/Statements.md#grammar_if-directive-clause) [elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_elseif-directive-clauses) <sub>opt</sub> [else-directive-clause](../ReferenceManual/Statements.md#grammar_else-directive-clause) <sub>opt</sub> [endif-directive](../ReferenceManual/Statements.md#grammar_endif-directive)
>
>if-directive-clause → [if-directive](../ReferenceManual/Statements.md#grammar_if-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>
>
>elseif-directive-clauses → [elseif-directive-clause](../ReferenceManual/Statements.md#grammar_elseif-directive-clause) [elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_elseif-directive-clauses) <sub>opt</sub>
>
>elseif-directive-clause → [elseif-directive](../ReferenceManual/Statements.md#grammar_elseif-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>
>
>else-directive-clause → [else-directive](../ReferenceManual/Statements.md#grammar_else-directive) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>
>
>if-directive → `#if`
>
>elseif-directive → `#elseif`
>
>else-directive → `#else`
>
>endif-directive → `#endif`
>
>compilation-condition → [platform-condition](../ReferenceManual/Statements.md#grammar_platform-condition)
>
>compilation-condition → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>compilation-condition → [boolean-literal](../ReferenceManual/LexicalStructure.md#grammar_boolean-literal)
>
>compilation-condition → `(` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) `)`
>
>compilation-condition → `!` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition)
>
>compilation-condition → [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) `&&` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition)
>
>compilation-condition → [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) `||` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition)
>
>platform-condition → `os` `(` [operating-system](../ReferenceManual/Statements.md#grammar_operating-system) `)`
>
>platform-condition → `arch` `(` [architecture](../ReferenceManual/Statements.md#grammar_architecture) `)`
>
>platform-condition → `swift` `(` `>=` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)` | `swift` `(` `<` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)`
>
>platform-condition → `compiler` `(` `>=` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)` | `compiler` `(` `<` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)`
>
>platform-condition → `canImport` `(` [module-name](../ReferenceManual/Statements.md#grammar_module-name) `)`
>
>platform-condition → `targetEnvironment` `(` [environment](../ReferenceManual/Statements.md#grammar_environment) `)`
>
>operating-system → `macOS` | `iOS` | `watchOS` | `tvOS`
>
>architecture → `i386` | `x86_64` | `arm` | `arm64`
>
>swift-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) [swift-version-continuation](../ReferenceManual/Statements.md#grammar_swift-version-continuation) <sub>opt</sub>
>
>swift-version-continuation → `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) [swift-version-continuation](../ReferenceManual/Statements.md#grammar_swift-version-continuation) <sub>opt</sub>
>
>module-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>environment → `simulator`

### Line Control Statement

A line control statement is used to specify a line number and filename that can be different from the line number and filename of the source code being compiled. Use a line control statement to change the source code location used by Swift for diagnostic and debugging purposes.

A line control statement has the following forms:

```swift
#sourceLocation(file: (filename), line: (line number))
#sourceLocation()
```

The first form of a line control statement changes the values of the `#line` and `#file` literal expressions, beginning with the line of code following the line control statement. The *line number* changes the value of `#line` and is any integer literal greater than zero. The *filename* changes the value of `#file` and is a string literal.

The second form of a line control statement, `#sourceLocation()`, resets the source code location back to the default line numbering and filename.

>**Grammar of a line control statement**
>
>line-control-statement → `#sourceLocation` `(` `file:` [file-name](../ReferenceManual/Statements.md#grammar_file-name) `,` `line:` [line-number](../ReferenceManual/Statements.md#grammar_line-number) `)`
>
>line-control-statement → `#sourceLocation` `(` `)`
>
>line-number → A decimal integer greater than zero
>
>file-name → [static-string-literal](../ReferenceManual/LexicalStructure.md#grammar_static-string-literal)

### Compile-Time Diagnostic Statement

A compile-time diagnostic statement causes the compiler to emit an error or a warning during compilation. A compile-time diagnostic statement has the following forms:

```swift
#error("error message")
#warning("warning message")
```

The first form emits the *error message* as a fatal error and terminates the compilation process. The second form emits the *warning message* as a nonfatal warning and allows compilation to proceed. You write the diagnostic message as a static string literal. Static string literals can’t use features like string interpolation or concatenation, but they can use the multiline string literal syntax.

>**Grammar of a compile-time diagnostic statement**
>
>diagnostic-statement → `#error` `(` [diagnostic-message](../ReferenceManual/Statements.md#grammar_diagnostic-message) `)`
>
>diagnostic-statement → `#warning` `(` [diagnostic-message](../ReferenceManual/Statements.md#grammar_diagnostic-message) `)`
>
>diagnostic-message → [static-string-literal](../ReferenceManual/LexicalStructure.md#grammar_static-string-literal)

Availability Condition
----------------------

An *availability condition* is used as a condition of an `if`, `while`, and `guard` statement to query the availability of APIs at runtime, based on specified platforms arguments.

An availability condition has the following form:

```swift
if #available((platform name) (version), ..., *) {
  (statements to execute if the APIs are available)
} else {
  (fallback statements to execute if the APIs are unavailable)
}
```

You use an availability condition to execute a block of code, depending on whether the APIs you want to use are available at runtime. The compiler uses the information from the availability condition when it verifies that the APIs in that block of code are available.

The availability condition takes a comma-separated list of platform names and versions. Use `iOS`, `macOS`, `watchOS`, and `tvOS` for the platform names, and include the corresponding version numbers. The `*` argument is required and specifies that on any other platform, the body of the code block guarded by the availability condition executes on the minimum deployment target specified by your target.

Unlike Boolean conditions, you can’t combine availability conditions using logical operators such as `&&` and `||`.

>**Grammar of an availability condition**
>
>availability-condition → `#available` `(` [availability-arguments](../ReferenceManual/Statements.md#grammar_availability-arguments) `)`
>
>availability-arguments → [availability-argument](../ReferenceManual/Statements.md#grammar_availability-argument) | [availability-argument](../ReferenceManual/Statements.md#grammar_availability-argument) `,` [availability-arguments](../ReferenceManual/Statements.md#grammar_availability-arguments)
>
>availability-argument → [platform-name](../ReferenceManual/Statements.md#grammar_platform-name) [platform-version](../ReferenceManual/Statements.md#grammar_platform-version)
>
>availability-argument → `*`
>
>platform-name → `iOS` | `iOSApplicationExtension`
>
>platform-name → `macOS` | `macOSApplicationExtension`
>
>platform-name → `watchOS`
>
>platform-name → `tvOS`
>
>platform-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)
>
>platform-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)
>
>platform-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)