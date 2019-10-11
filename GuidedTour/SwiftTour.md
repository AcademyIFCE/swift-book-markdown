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

<!-- [//]: # (There’s an even simpler way to include values in strings: Write the value in parentheses, and write a backslash (`\`) before the parentheses. For example:) -->


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

<!-- Create arrays and dictionaries using brackets (`[]`), and access their elements by writing the index or key in brackets. A comma is allowed after the last element. -->

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

Objetos e Classes
-------------------

Use `class` seguido pelo nome da classe para criar uma classe. A declaração de uma propriedade em uma classe é escrita do mesmo jeito que uma declaração de uma constante ou variável, exceto que está no contexto de uma classe. Da mesma forma, as declarações de métodos e funções são escritas da mesma forma.

```swift
class Shape {
    var numberOfSides = 0
    func simpleDescription() -> String {
        return "Uma forma com \(numberOfSides) lados."
    }
}
```

**Experimente**

> Adicione uma propriedade constante com `let`, e adicione outro método que recebe um argumento.

Crie uma instância de uma classe colocando parênteses depois do nome da classe. Use a sintaxe de ponto para acessar propriedades e métodos da instância.

```swift
var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
```
 
Esta versão da classe `Shape` está faltando algo muito importane: um inicializador para configurar a classe quando uma instância é criada. Use `init` para criar uma.

```swift
class NamedShape {
    var numberOfSides: Int = 0
    var name: String

    init(name: String) {
        self.name = name
    }

    func simpleDescription() -> String {
        return "Uma forma com \(numberOfSides) lados."
    }
}
```

Perceba como `self` é usado para diferenciar a propriedade `name` do argumento `name` para o inicializador. Os argumentos para o inicializador são passados como uma chamada de uma funcão quando você cria uma instância da classe. Cada propriedade precisa de um valor designado -em sua declaração(como em `numberOfSides`) ou no inicializador(como em `name`).

Use `deinit` para criar um desinicializador se você precisa executar alguma limpeza antes que o objeto seja desalocado.

As subclasses incluem o nome da superclasse depois do nome da classe, separada por uma vírgula. Não há nenhum requisito para que classes herdem alguma classe raiz padrão, então você pode incluir ou omitir a superclasse quando necessário.

Métodos em uma subclasse que substituem a implementação da superclasse são marcados com `override` —a substituição de um método por acidente, sem `override`, é detectada pelo compilador como um erro. O compilador também detecta métodos com `override` que na verdade não substituem nenhum método na superclasse.

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
        return "Um quadrado com lados de tamanho \(sideLength)."
    }
}
let test = Square(sideLength: 5.2, name: "meu quadrado teste")
test.area()
test.simpleDescription()
```

**Experimente**

> Faça outra subclasse de `NamedShape` chamada `Circle` que recebe um raio e um nome como argumentos para o inicializador. Implemente os métodos `area()` e `simpleDescription()` na classe `Circle`.  

Além das propriedades simples que são armazenadas, propriedades podem ter um *getter* e um *setter*.

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
        return "Um triângulo equilátero com lados de tamanho \(sideLength)."
    }
}
var triangle = EquilateralTriangle(sideLength: 3.1, name: "um triângulo")
print(triangle.perimeter)
// Imprime "9.3"
triangle.perimeter = 9.9
print(triangle.sideLength)
// Imprime "3.3000000000000003"
``` 
No *setter* do `perimeter`, o novo valor tem o nome implícito `newValue`. Você pode definir um valor explícito entre parênteses depois de `set`.

Note que o inicializador para a classe `EquilateralTriangle` tem três etapas distintas:

1. Configurando o valor das propriedades que a subclasse declara.

2. Chamando o inicializador da superclasse.

3. Mudando o valor das propriedades definida pela superclasse. Qualquer trabalho de configuração adicional que usa métodos, *getters* ou *setters* também podem ser feitas nesse momento.

Se você não precisa calcular a propriedade mas ainda precisa fornecer o código que é executado antes e depois de definir um novo valor, use `willSet` e `didSet`. O código que você fornece é executado quando o valor é alterado fora do inicializador. Por exemplo, a classe abaixo garante que o tamanho do lado do triângulo é sempre o mesmo que o tamanho do lado do quadrado.

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
var triangleAndSquare = TriangleAndSquare(size: 10, name: "outro teste de forma")
print(triangleAndSquare.square.sideLength)
// Imprime "10.0"
print(triangleAndSquare.triangle.sideLength)
// Imprime "10.0"
triangleAndSquare.square = Square(sideLength: 50, name: "quadrado maior")
print(triangleAndSquare.triangle.sideLength)
// Imprime "50.0"
``` 
Enquanto estiver trabalhando com valores opcionais, você pode escrever `?` antes de operações como métodos, propriedades e assinaturas. Se o valor antes de `?` for `nil`, tudo depois de `?` é ignorado e o valor de toda a expressão é `nil`.

Caso contrário, o valor opcional é desempacotado, e tudo depois de `?` age sobre o valor desempacotado. Em ambos os casos, o valor de toda a expressão é um valor opcional.


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

Protocolos e Extensões
------------------------

Use `protocol` para declarar um protocolo.

```swift
protocol ExampleProtocol {
    var simpleDescription: String { get }
    mutating func adjust()
}
``` 

Classes, *enums* e *structs* todos podem adotar protocolos.

```swift
class SimpleClass: ExampleProtocol {
    var simpleDescription: String = "Uma classe muito simples"
    var anotherProperty: Int = 69105
    func adjust() {
        simpleDescription += " Agora 100% ajustado."
    }
}
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription

struct SimpleStructure: ExampleProtocol {
    var simpleDescription: String = "Uma simples estrutura"
    mutating func adjust() {
        simpleDescription += " (ajustada)"
    }
}
var b = SimpleStructure()
b.adjust()
let bDescription = b.simpleDescription
``` 

**Experimente**

> Adicione outro requisito ao `ExampleProtocol`. Qual mudanças que você precisa mudar na `SimpleClass` e na `SimpleStructure` para que elas ainda conforme com o protocolo?

Note que o uso da *keyword* `mutating` na declaração de `SimpleStructure` é usado para marcar um método que modifica essa *struct*. A declaração de `SimpleClass` não precisa que nenhum de seus métodos sejam marcados como *mutating* porque os métodos de uma classe sempre podem  modificar a classe.

Use `extension` para adicionar funcionalidades para um tipo existente, como novos métodos e propriedades computadas. Você pode usar uma extensão para adicionar um protocolo que conforme com um tipo que é declarado em outro lugar, ou até mesmo para um tipo que você importa de uma biblioteca ou *framework*.

```swift
extension Int: ExampleProtocol {
    var simpleDescription: String {
        return "O número \(self)"
    }
    mutating func adjust() {
        self += 42
    }
 }
print(7.simpleDescription)
// Imprime "O número 7"
```

**Experimente**

> Escreva uma *extension* para o tipo `Double` que adiciona uma propriedade  `absoluteValue`.

Você pode usar um nome de um protocolo apenas como qualquer outro tipo nomeado—por exemplo, para criar uma coleção de objetos que tenham tipos distintos, mas que todos conformam com um único protocolo. Quando você trabalha com valores cujo tipo é um tipo *protocol*, métodos fora da definição do protocolo não estão disponíveis.

```swift
 let protocolValue: ExampleProtocol = a
 print(protocolValue.simpleDescription)
 // Imprime "Uma classe muito simples. Agora 100% ajustada."
 // print(protocolValue.anotherProperty) // Descomente para ver o erro
```
Mesmo que a variável `protocolValue` tem um tipo *runtime* da `SimpleClass`, o compilador a trata como o tipo fornecido do `ExampleProtocol`. Isso signfica que você não pode acessar acidentalemente métodos ou propriedades que a classe implementa, além  da conformidade do protocolo.

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
