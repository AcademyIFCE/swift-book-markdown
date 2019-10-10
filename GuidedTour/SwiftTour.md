 Uma Tour pela Swift

Uma Tour pela Swift
============

A Tradição sugere que o primeiro programa feito em uma linguagem nova deve imprimir as palavras "Hello, world!" na tela. Em Swift isso pode ser feito em uma única linha de código:

```swift
print("Hello, world!")
// Imprime "Hello, world!"
```

Se você escreveu código em C ou Objective-C, esta sintaxe pode parece familiar pra voce, esta linha de código é um programa completo. Você não precisa importar uma biblioteca separada para funcionalidades como input output ou manipulação de string. Código escrito no escopo global é usado como um ponto de entrada para o programa, então você não precisa de uma função `main()`. Você também não precisa escrever ponto e virgula no final de cada declaração.

Esta tour lhe dará informação suficiente para começar a escrever código em Swift mostrando como concluir uma variedade de tarefas de programação. Não se preocupe se você não entender alguma coisa introduzida nessa Tour, pois será explicado em mais detalhes no resto desse livro.

**Nota**

> Em um Mac com Xcode instalado, ou em um iPad com Swift Playgrounds, você pode abrir esse capítulo como um playground. Playgrounds possibilita voce editar o código listings e ver os resultados imediatamente.

[Baixar Playground](https://docs.swift.org/swift-book/GuidedTour/GuidedTour.playground.zip)

[//]: # (Simple Values)
Valores Simples
-------------
Use `let` para criar uma constante e `var` para criar uma variável. O valor de uma constante não precisa ser conhecida em tempo de compilação, mas você precisa atribuir um valor exatamente uma vez. Isso significa que você pode usar constantes para nomear um valor que você determina uma vez, mas que você vai usar em muitos lugares.

```swift
var myVariable = 42
myVariable = 50
let myConstant = 42
```

Uma constante ou variável deve ser do mesmo tipo que o valor que você quer passar para ela. No entanto, você não precisa sempre escrever o tipo explicitamente. Dando um valor quando você cria uma constante ou variável permite com que o compilador infira o seu tipo. No exemplo acima, o compilador infere que `myVariable` é um inteiro porque o seu valor inicial é um inteiro.

Se o valor inicial do valor não der informação suficiente(ou se não tiver nenhum valor inicial), especifique o tipo escrevendo-o depois da variável, separado por uma virgula.

```swift
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double = 70
```

**Experimente**
> Crie uma constante com um tipo explícito `Float` e com um valor 4.

Valores nunca são convertidos implicitamente para outro tipo. Se você precisa converter um valor para um tipo diferente, faça uma instância explícita do tipo desejado.

```swift
let label = "A largura é "
let width = 94
let widthLabel = label + String(width)
```

**Experimente**

> Tente remover a conversão para o tipo `String` na última linha. Qual erro que aparece? 

Há uma maneira ainda mais simples para incluir valores em *strings*: Escreva o valor entre parênteses e escreva uma barra invertida(`\`) antes dos parênteses. Por exemplo:

```swift
let apples = 3
let oranges = 5
let appleSummary = "Eu tenho \(apples) maçãs."
let fruitSummary = "Eu tenho \(apples + oranges) pedaços de frutas."
```

**Experimente**

> Use `\()` para fazer um cálculo do tipo *Float* em uma *string* e coloque o nome de algúem em uma saudação.

Use três aspas duplas (`"""`) para *strings* que ocupem várias linhas. A indentação no começo de cada linha é removida, desde que corresponda à indentação das aspas finais.
Por exemplo:

```swift
let quotation = """
    Eu disse: "I tenho \(apples) maçãs."
    E então eu disse: "Eu tenho \(apples + oranges) pedaços de frutas."
"""
```

Crie *arrays* e dicionários que usem colchetes (`[]`), e acesse os seus elementos escrevendo o seu índice ou chave nos colchetes. Uma vírgula é permitida após o último elemento. 

```swift
var shoppingList = ["peixe-gato", "água", "tulipas"]
shoppingList[1] = "garrafa d'água"

var occupations = [
    "Malcolm": "Capitão",
    "Kaylee": "Mecânico",
]
occupations["Jayne"] = "Relações Públicas"
```

*Arrays* crescem automaticamente conforme você adiciona elementos.

```swift
shoppingList.append("tinta azul")
print(shoppingList)
```

Para criar um *array* ou dicionário, use a sintaxe de inicialização.

```swift
let emptyArray = [String]()
let emptyDictionary = [String: Float]()
```

Se a informação do tipo pode ser inferida, você pode escrever um *array* vazio como `[]` e um dicionário vazio como `[:]`—por exemplo, quando você define um novo valor para uma variável ou passa um argumento para uma função.

```swift
shoppingList = []
occupations = [:]
```

Controle de Fluxo
------------

Use `if` e `switch` para fazer condicionais, e use `for`\-`in`, e `repeat`\-`while` para fazer laços. Parênteses ao redor da condicional ou da variável de laço são opcionais. Chaves ao redor do corpo é necessário.

```swift
let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
print(teamScore)
// Imprime "11"
```

Em um declaração `if`, a condicional deve ser uma expressão Booleana, isso significa que código como `if score { ... }` é um erro, não uma comparação implícita a zero.

Você pode usar `if` e `let` juntos para trabalhar com valores que podem não existir. Esses valores são representados como opcionais. Um valor opcional contem um valor ou contem `nil` para indicar que o valor não existe. Escreva uma interrogação (`?`) após o tipo do valor para indicar o valor como opcional.

```swift
var optionalString: String? = "Hello"
print(optionalString == nil)
// Imprime "false"

var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}
```

**Experimento**

> Mudar `optionalName` para `nil`. Qual a saudação que você vai ter? Adicione uma condição `else` que mude a saudação se `optionalValue` for `nil`.

Se o valor opcional é `nil`, a condicional é `false` e o código nas chaves é pulado. Caso contrário, o valor opcional é desempacotado e atribuída para a constante após o `let`, que faz o valor desempacotado acessível dentro do bloco de código.

Outra maneira de manipular valores opcionais é prover um valor padrão usando o operador `??`. Se o valor do opcional estiver faltando, o valor padrão é usado.

```swift
let nickName: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickName ?? fullName)"
```

Switches suporta qualquer tipo de dado e uma grande variedade de operações de comparação, eles não são limitado a inteiros e testes de igualdade.

```swift
let vegetable = "red pepper"
switch vegetable {
case "celery":
    print("Add some raisins and make ants on a log.")
case "cucumber", "watercress":
    print("That would make a good tea sandwich.")
case let x where x.hasSuffix("pepper"):
    print("Is it a spicy \(x)?")
default:
    print("Everything tastes good in soup.")
}
// Imprime "Is it a spicy red pepper?"
```

**Experimento**

> Tente remover o caso padrão. Qual o erro que você recebe?

Perceba como `let` pode ser usado em um padrão para atribuir o valor que corresponde o padrão para uma constante.

Após executar o código dentro do switch case que coincidiu, o programa sai da declaração do switch. A execução não continua para o proximo case, então não há necessidade de usar break explicitamente no switch, no final de casa código dos cases.

You use `for`\-`in` to iterate over items in a dictionary by providing a pair of names to use for each key-value pair. Dictionaries are an unordered collection, so their keys and values are iterated over in an arbitrary order.

Você usa `for`\-`in` para iterar nos itens de um dicionário ao prover um par de nomes para usar para cada par chave-valor. Dicionários são uma coleção desordenada, então as chaves e valores são iterados em uma ordem arbitraria.

```swift
let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 9, 16, 25],
]
var largest = 0
for (kind, numbers) in interestingNumbers {
    for number in numbers {
        if number > largest {
            largest = number
        }
    }
}
print(largest)
// Imprime "25"
```

**Experimento**

> Adicione outra variável para observar do tipo do numero que foi o maior, assim como qual foi o maior numero.

Use `while` para repetir um bloco de código ate que uma condição mude. A condição do laço também pode ser no final, assegurantdo que o laço irá executar pelo menos uma vez.

```swift
var n = 2
while n < 100 {
    n *= 2
}
print(n)
// Imprime "128"

var m = 2
repeat {
    m *= 2
} while m < 100
print(m)
// Imprime "128"
```

Você pode manter um índice em um laço ao usar `..<` para fazer uma coleção de indices.

```swift
var total = 0
for i in 0..<4 {
    total += i
}
print(total)
// Imprime "6"
```

Use `..<`para fazer uma coleção que omite o maior final, e use `...`para fazer a coleção incluir os dois valores.

Functions and Closures
----------------------

Use `func` to declare a function. Call a function by following its name with a list of arguments in parentheses. Use `->` to separate the parameter names and types from the function’s return type.

```swift
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet(person: "Bob", day: "Tuesday")
```

**Experiment**

> Remove the `day` parameter. Add a parameter to include today’s lunch special in the greeting.

By default, functions use their parameter names as labels for their arguments. Write a custom argument label before the parameter name, or write `_` to use no argument label.

```swift
func greet(_ person: String, on day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet("John", on: "Wednesday")
```

Use a tuple to make a compound value—for example, to return multiple values from a function. The elements of a tuple can be referred to either by name or by number.

```swift
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
    var min = scores[0]
    var max = scores[0]
    var sum = 0

    for score in scores {
        if score > max {
            max = score
        } else if score < min {
            min = score
        }
        sum += score
    }

    return (min, max, sum)
}
let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
print(statistics.sum)
// Prints "120"
print(statistics.2)
// Prints "120"
```

Functions can be nested. Nested functions have access to variables that were declared in the outer function. You can use nested functions to organize the code in a function that is long or complex.

```swift
func returnFifteen() -> Int {
    var y = 10
    func add() {
        y += 5
    }
    add()
    return y
}
returnFifteen()
```

Functions are a first-class type. This means that a function can return another function as its value.

```swift
func makeIncrementer() -> ((Int) -> Int) {
    func addOne(number: Int) -> Int {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
increment(7)
```

A function can take another function as one of its arguments.

```swift
func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
}
func lessThanTen(number: Int) -> Bool {
    return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(list: numbers, condition: lessThanTen)
```

Functions are actually a special case of closures: blocks of code that can be called later. The code in a closure has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it is executed—you saw an example of this already with nested functions. You can write a closure without a name by surrounding code with braces (`{}`). Use `in` to separate the arguments and return type from the body.

```swift
numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
```

**Experiment**

> Rewrite the closure to return zero for all odd numbers.

You have several options for writing closures more concisely. When a closure’s type is already known, such as the callback for a delegate, you can omit the type of its parameters, its return type, or both. Single statement closures implicitly return the value of their only statement.

```swift
let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)
// Prints "[60, 57, 21, 36]"
```

You can refer to parameters by number instead of by name—this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses. When a closure is the only argument to a function, you can omit the parentheses entirely.

```swift
let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
// Prints "[20, 19, 12, 7]"
```

Objects and Classes
-------------------

Use `class` followed by the class’s name to create a class. A property declaration in a class is written the same way as a constant or variable declaration, except that it is in the context of a class. Likewise, method and function declarations are written the same way.

```swift
class Shape {
    var numberOfSides = 0
    func simpleDescription() -> String {
        return "A shape with \(numberOfSides) sides."
    }
}
```

**Experiment**

> Add a constant property with `let`, and add another method that takes an argument.

Create an instance of a class by putting parentheses after the class name. Use dot syntax to access the properties and methods of the instance.

```swift
var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
```
 
This version of the `Shape` class is missing something important: an initializer to set up the class when an instance is created. Use `init` to create one.

```swift
class NamedShape {
    var numberOfSides: Int = 0
    var name: String

    init(name: String) {
        self.name = name
    }

    func simpleDescription() -> String {
        return "A shape with \(numberOfSides) sides."
    }
}
```

Notice how `self` is used to distinguish the `name` property from the `name` argument to the initializer. The arguments to the initializer are passed like a function call when you create an instance of the class. Every property needs a value assigned—either in its declaration (as with `numberOfSides`) or in the initializer (as with `name`).

Use `deinit` to create a deinitializer if you need to perform some cleanup before the object is deallocated.

Subclasses include their superclass name after their class name, separated by a colon. There is no requirement for classes to subclass any standard root class, so you can include or omit a superclass as needed.

Methods on a subclass that override the superclass’s implementation are marked with `override`—overriding a method by accident, without `override`, is detected by the compiler as an error. The compiler also detects methods with `override` that don’t actually override any method in the superclass.

```swift
class Square: NamedShape {
    var sideLength: Double

    init(sideLength: Double, name: String) {
        self.sideLength = sideLength
        super.init(name: name)
        numberOfSides = 4
    }

    func area() -> Double {
        return sideLength * sideLength
    }

    override func simpleDescription() -> String {
        return "A square with sides of length \(sideLength)."
    }
}
let test = Square(sideLength: 5.2, name: "my test square")
test.area()
test.simpleDescription()
```

**Experiment**

> Make another subclass of `NamedShape` called `Circle` that takes a radius and a name as arguments to its initializer. Implement an `area()` and a `simpleDescription()` method on the `Circle` class.

In addition to simple properties that are stored, properties can have a getter and a setter.

```swift
class EquilateralTriangle: NamedShape {
    var sideLength: Double = 0.0

    init(sideLength: Double, name: String) {
        self.sideLength = sideLength
        super.init(name: name)
        numberOfSides = 3
    }

    var perimeter: Double {
        get {
            return 3.0 * sideLength
        }
        set {
            sideLength = newValue / 3.0
        }
     }

    override func simpleDescription() -> String {
        return "An equilateral triangle with sides of length \(sideLength)."
    }
}
var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
print(triangle.perimeter)
// Prints "9.3"
triangle.perimeter = 9.9
print(triangle.sideLength)
// Prints "3.3000000000000003"
``` 

In the setter for `perimeter`, the new value has the implicit name `newValue`. You can provide an explicit name in parentheses after `set`.

Notice that the initializer for the `EquilateralTriangle` class has three different steps:

1. Setting the value of properties that the subclass declares.
    
2. Calling the superclass’s initializer.
    
3. Changing the value of properties defined by the superclass. Any additional setup work that uses methods, getters, or setters can also be done at this point.
    
If you don’t need to compute the property but still need to provide code that is run before and after setting a new value, use `willSet` and `didSet`. The code you provide is run any time the value changes outside of an initializer. For example, the class below ensures that the side length of its triangle is always the same as the side length of its square.

```swift
class TriangleAndSquare {
    var triangle: EquilateralTriangle {
        willSet {
            square.sideLength = newValue.sideLength
        }
    }
    var square: Square {
        willSet {
            triangle.sideLength = newValue.sideLength
        }
    }
    init(size: Double, name: String) {
        square = Square(sideLength: size, name: name)
        triangle = EquilateralTriangle(sideLength: size, name: name)
    }
 }
var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
print(triangleAndSquare.square.sideLength)
// Prints "10.0"
print(triangleAndSquare.triangle.sideLength)
// Prints "10.0"
triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
print(triangleAndSquare.triangle.sideLength)
// Prints "50.0"
``` 

When working with optional values, you can write `?` before operations like methods, properties, and subscripting. If the value before the `?` is `nil`, everything after the `?` is ignored and the value of the whole expression is `nil`. Otherwise, the optional value is unwrapped, and everything after the `?` acts on the unwrapped value. In both cases, the value of the whole expression is an optional value.

```swift
let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
let sideLength = optionalSquare?.sideLength
``` 

Enumerations and Structures
---------------------------

Use `enum` to create an enumeration. Like classes and all other named types, enumerations can have methods associated with them.

```swift
enum Rank: Int {
    case ace = 1
    case two, three, four, five, six, seven, eight, nine, ten
    case jack, queen, king

    func simpleDescription() -> String {
        switch self {
        case .ace:
            return "ace"
        case .jack:
            return "jack"
        case .queen:
            return "queen"
        case .king:
            return "king"
        default:
            return String(self.rawValue)
        }
    }
}
let ace = Rank.ace
let aceRawValue = ace.rawValue
```

**Experiment**

> Write a function that compares two `Rank` values by comparing their raw values.

By default, Swift assigns the raw values starting at zero and incrementing by one each time, but you can change this behavior by explicitly specifying values. In the example above, `Ace` is explicitly given a raw value of `1`, and the rest of the raw values are assigned in order. You can also use strings or floating-point numbers as the raw type of an enumeration. Use the `rawValue` property to access the raw value of an enumeration case.

Use the `init?(rawValue:)` initializer to make an instance of an enumeration from a raw value. It returns either the enumeration case matching the raw value or `nil` if there is no matching `Rank`.

```swift
if let convertedRank = Rank(rawValue: 3) {
    let threeDescription = convertedRank.simpleDescription()
}
```

The case values of an enumeration are actual values, not just another way of writing their raw values. In fact, in cases where there isn’t a meaningful raw value, you don’t have to provide one.

```swift
enum Suit {
    case spades, hearts, diamonds, clubs

    func simpleDescription() -> String {
        switch self {
        case .spades:
            return "spades"
        case .hearts:
            return "hearts"
        case .diamonds:
            return "diamonds"
        case .clubs:
            return "clubs"
        }
    }
 }
let hearts = Suit.hearts
let heartsDescription = hearts.simpleDescription()
```

**Experiment**

> Add a `color()` method to `Suit` that returns “black” for spades and clubs, and returns “red” for hearts and diamonds.

Notice the two ways that the `hearts` case of the enumeration is referred to above: When assigning a value to the `hearts` constant, the enumeration case `Suit.hearts` is referred to by its full name because the constant doesn’t have an explicit type specified. Inside the switch, the enumeration case is referred to by the abbreviated form `.hearts` because the value of `self` is already known to be a suit. You can use the abbreviated form anytime the value’s type is already known.

If an enumeration has raw values, those values are determined as part of the declaration, which means every instance of a particular enumeration case always has the same raw value. Another choice for enumeration cases is to have values associated with the case—these values are determined when you make the instance, and they can be different for each instance of an enumeration case. You can think of the associated values as behaving like stored properties of the enumeration case instance. For example, consider the case of requesting the sunrise and sunset times from a server. The server either responds with the requested information, or it responds with a description of what went wrong.

```swift
 enum ServerResponse {
    case result(String, String)
    case failure(String)
}

 let success = ServerResponse.result("6:00 am", "8:09 pm")
 let failure = ServerResponse.failure("Out of cheese.")

 switch success {
 case let .result(sunrise, sunset):
    print("Sunrise is at \(sunrise) and sunset is at \(sunset).")
 case let .failure(message):
    print("Failure... \(message)")
 }
 // Prints "Sunrise is at 6:00 am and sunset is at 8:09 pm."
```

**Experiment**

> Add a third case to `ServerResponse` and to the switch.

Notice how the sunrise and sunset times are extracted from the `ServerResponse` value as part of matching the value against the switch cases.

Use `struct` to create a structure. Structures support many of the same behaviors as classes, including methods and initializers. One of the most important differences between structures and classes is that structures are always copied when they are passed around in your code, but classes are passed by reference.

```swift
struct Card {
    var rank: Rank
    var suit: Suit
    func simpleDescription() -> String {
        return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
    }
 }
let threeOfSpades = Card(rank: .three, suit: .spades)
let threeOfSpadesDescription = threeOfSpades.simpleDescription()
```

**Experiment**

> Write a function that returns an array containing a full deck of cards, with one card of each combination of rank and suit.

Protocols and Extensions
------------------------

Use `protocol` to declare a protocol.

```swift
protocol ExampleProtocol {
    var simpleDescription: String { get }
    mutating func adjust()
}
``` 

Classes, enumerations, and structs can all adopt protocols.

```swift
class SimpleClass: ExampleProtocol {
    var simpleDescription: String = "A very simple class."
    var anotherProperty: Int = 69105
    func adjust() {
        simpleDescription += " Now 100% adjusted."
    }
}
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription

struct SimpleStructure: ExampleProtocol {
    var simpleDescription: String = "A simple structure"
    mutating func adjust() {
        simpleDescription += " (adjusted)"
    }
}
var b = SimpleStructure()
b.adjust()
let bDescription = b.simpleDescription
``` 

**Experiment**

> Add another requirement to `ExampleProtocol`. What changes do you need to make to `SimpleClass` and `SimpleStructure` so that they still conform to the protocol?

Notice the use of the `mutating` keyword in the declaration of `SimpleStructure` to mark a method that modifies the structure. The declaration of `SimpleClass` doesn’t need any of its methods marked as mutating because methods on a class can always modify the class.

Use `extension` to add functionality to an existing type, such as new methods and computed properties. You can use an extension to add protocol conformance to a type that is declared elsewhere, or even to a type that you imported from a library or framework.

```swift
extension Int: ExampleProtocol {
    var simpleDescription: String {
        return "The number \(self)"
    }
    mutating func adjust() {
        self += 42
    }
 }
print(7.simpleDescription)
// Prints "The number 7"
```

**Experiment**

> Write an extension for the `Double` type that adds an `absoluteValue` property.

You can use a protocol name just like any other named type—for example, to create a collection of objects that have different types but that all conform to a single protocol. When you work with values whose type is a protocol type, methods outside the protocol definition are not available.

 let protocolValue: ExampleProtocol = a
 print(protocolValue.simpleDescription)
 // Prints "A very simple class. Now 100% adjusted."
 // print(protocolValue.anotherProperty) // Uncomment to see the error

Even though the variable `protocolValue` has a runtime type of `SimpleClass`, the compiler treats it as the given type of `ExampleProtocol`. This means that you can’t accidentally access methods or properties that the class implements in addition to its protocol conformance.

Error Handling
--------------

You represent errors using any type that adopts the `Error` protocol.

```swift
enum PrinterError: Error {
    case outOfPaper
    case noToner
    case onFire
}
```

Use `throw` to throw an error and `throws` to mark a function that can throw an error. If you throw an error in a function, the function returns immediately and the code that called the function handles the error.

```swift
func send(job: Int, toPrinter printerName: String) throws -> String {
    if printerName == "Never Has Toner" {
        throw PrinterError.noToner
    }
    return "Job sent"
}
```

There are several ways to handle errors. One way is to use `do`\-`catch`. Inside the `do` block, you mark code that can throw an error by writing `try` in front of it. Inside the `catch` block, the error is automatically given the name `error` unless you give it a different name.

```swift
do {
    let printerResponse = try send(job: 1040, toPrinter: "Bi Sheng")
    print(printerResponse)
} catch {
    print(error)
}
// Prints "Job sent"
```

**Experiment**

> Change the printer name to `"Never Has Toner"`, so that the `send(job:toPrinter:)` function throws an error.

You can provide multiple `catch` blocks that handle specific errors. You write a pattern after `catch` just as you do after `case` in a switch.

```swift
do {
    let printerResponse = try send(job: 1440, toPrinter: "Gutenberg")
    print(printerResponse)
} catch PrinterError.onFire {
    print("I'll just put this over here, with the rest of the fire.")
} catch let printerError as PrinterError {
    print("Printer error: \(printerError).")
} catch {
    print(error)
}
// Prints "Job sent"
```

**Experiment**

> Add code to throw an error inside the `do` block. What kind of error do you need to throw so that the error is handled by the first `catch` block? What about the second and third blocks?

Another way to handle errors is to use `try?` to convert the result to an optional. If the function throws an error, the specific error is discarded and the result is `nil`. Otherwise, the result is an optional containing the value that the function returned.

```swift
let printerSuccess = try? send(job: 1884, toPrinter: "Mergenthaler")
let printerFailure = try? send(job: 1885, toPrinter: "Never Has Toner")
```
Use `defer` to write a block of code that is executed after all other code in the function, just before the function returns. The code is executed regardless of whether the function throws an error. You can use `defer` to write setup and cleanup code next to each other, even though they need to be executed at different times.

```swift
var fridgeIsOpen = false
let fridgeContent = ["milk", "eggs", "leftovers"]

func fridgeContains(_ food: String) -> Bool {
    fridgeIsOpen = true
    defer {
        fridgeIsOpen = false
    }

    let result = fridgeContent.contains(food)
    return result
}
fridgeContains("banana")
print(fridgeIsOpen)
// Prints "false"
```

Generics
--------

Write a name inside angle brackets to make a generic function or type.

```swift
func makeArray<Item>(repeating item: Item, numberOfTimes: Int) -> [Item] {
    var result = [Item]()
    for _ in 0..<numberOfTimes {
        result.append(item)
    }
    return result
 }
 makeArray(repeating: "knock", numberOfTimes: 4)
```

You can make generic forms of functions and methods, as well as classes, enumerations, and structures.

```swift
// Reimplement the Swift standard library's optional type
enum OptionalValue<Wrapped> {
    case none
    case some(Wrapped)
}
var possibleInteger: OptionalValue<Int> = .none
possibleInteger = .some(100)
```

Use `where` right before the body to specify a list of requirements—for example, to require the type to implement a protocol, to require two types to be the same, or to require a class to have a particular superclass.

```swift
func anyCommonElements<T: Sequence, U: Sequence>(_ lhs: T, _ rhs: U) -> Bool where T.Element: Equatable, T.Element == U.Element {
    for lhsItem in lhs {
        for rhsItem in rhs {
            if lhsItem == rhsItem {
                return true
            }
        }
    }
    return false
 }
anyCommonElements([1, 2, 3], [3])
```

**Experiment**

> Modify the `anyCommonElements(_:_:)` function to make a function that returns an array of the elements that any two sequences have in common.

Writing `<T: Equatable>` is the same as writing `<T> ... where T: Equatable`.
