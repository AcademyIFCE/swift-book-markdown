Enumerações
============

Uma *enumeração* define um tipo comum para um grupo de valores relacionados e habilita você a trabalhar com esses valores de modo a assegurar o tipo no seu código.

Se você está familiarizado com o C, vai saber que enumerações em C atribuem nomes realacionados a uma série de valores inteiros. Enumerações em Swift são muito mais flexíveis, e não precisam fornecer um valor para cada caso das enumerações. Se um valor (conhecido como valor *raw*) é fornecido para cada caso da enumeração, o valor pode ser uma string, um caractere, ou qualquer valor de tipo inteiro ou ponto flutuante.

Alternativamente, casos de uma enumeração podem específicar valores associados de tipo *any* para serem armazenados ao longo de cada diferente valor de caso, assim como uniões ou variantes fazem em outras linguagens. Você pode definir um conjunto comum de casos relacionados como parte de uma enumeração, cada um deles possui um conjunto de valores de tipo associado apropriado a ele.

Enumerações em Swift são tipos de primeira classe por direito próprio. Elas adotam muitas funcionalidades tradicionalmente suportadas somente por classes, tais quais propriedades computadas para fornecer informações adicionais sobre o valor atual da enumeração, e métodos de instância para fornecer funcionalidades relacionadas aos valores que a enumeração representa. Enumerações também podem definir inicializadores para fornecer um valor inicial de casos; podem ser estendidas para expandir suas funcionalidades além da implementação original; e podem assinar protocolos para fornecer funcionalidades padrão.

Para mais informações sobre essas capacidades veja [Propriedades](Properties.md), [Métodos](Methods.md), [Inicialização](Initialization.md), [Extensões](Extensions.md), e [Protocolos](Protocols.md).

Sintax de Enumerações
------------------

Você inicia enumerações com a palavra chave `enum` e coloca sua definição inteira dentro de um par de chaves:

```swift
enum AlgumaEnumeracao {
// definição da enumeração vai aqui
}
```

Aqui está um exemplo para os quatro pontos principais de uma bússola:

```swift
enum PontoBussola {
    case norte
    case sul
    case leste
    case oeste
}
```

Os valores definidos em uma enumeraçãos (assim como `norte`, `sul`, `leste` e `oeste`) são seus *casos de enumeração*. Você usa a palavra chave `case` para iniciar novos casos na enumeração.

**Nota**

>Casos de enumeração em Swift não possuem valores inteiros definidos por padrão, diferentemente de linguagens como C e Objective-C. No exemplo `PontoBussola` acima, `norte`, `sul`, `leste` e `oeste` não são implicitamente iguais a `0`, `1`, `2` e `3`. Invés disso, os diferentes casos de enumeração são valores por si próprio, com um tipo explicito definido de `PontoBussola`.

Múltiplos casos podem aparecer uma única linha, separados por vírgulas:

```swift
enum Planeta {
    case mercúrio, venus, terra, marte, jupiter, saturno, urano, netuno
}
```

Cada definição de enumeração define um novo tipo. Assim como outros tipos em Swift, seus nome (assim como `PontoBussola` e `Planeta`) começam com letra maiúscula. Forneça para enumerações nomes preferencialmente no singular do que no plural. assim serão lidas de forma auto explicativa:

```swift
var direcaoDaCabeca = PontoBussola.oeste
```

O tipo de `direcaoDaCabeca` é inferido quando esta é inicializada com um dos possíveis valores de `PontoBussola`. Uma vez que `direcaoDaCabeca` é declarado como um `PontoBussola`, você pode defini-la para um diferente valor de `PontoBussola` usando uma sintaxe mais curta:

```swift
direcaoDaCabeca = .oeste
```

O tipo de `direcaoDaCabeca` já é conhecido, então você pode dispensar o tipo ao definir seu valor. Isso torna o código altamente legível quando se trabalha com valores de enumeração explicitamente típados.

Correspondendo valores de Enumerações com blocos *Switch*
---------------------------------------------------

Você pode corresponder valores individuais de enumerações com blocos `switch`: 

```swift
direcaoDaCabeca = .sul
switch direcaoDaCabeca {
    case .norte:
        print("Muitos planetas possuem um norte")
    case .sul:
        print("Cuidado com os pinguins")
    case .leste:
        print("Onde o sol se põe")
    case .oeste:
        print("Onde o céu é azul")
}
// Exibe "Cuidado com os pinguins"
```

Você pode ler esse código como sendo:
“Considere o valor de `direcaoDaCabeca`. No caso aonde é igual a `.norte`, exiba `"Muitos planetas possuem um norte"`. No caso aonde é igual a `.sul`, exiba `"Watch out for penguins"`.”

“Consider the value of `directionToHead`. In the case where it equals `.north`, print `"Lots of planets have a north"`. In the case where it equals `.south`, print `"Cuidado com os pinguins"`.”

…e assim sucessivamente.

Como é descrito em [Controle de fluxo](ControlFlow.md), um bloco `switch` precisa ser exaustivo quando considera casos de enumerações. Se o caso para `.oeste` for omitido, esse código não compila, pois ele não considera a lista completa de casos de `PontoBussola`. Exigindo exaustividade assegura-se que casos de enumerações não sejam acidentalmente omitidos.

Quando não é apropriado fornecer um `case` para todo caso da enumeração, você pode fornecer um caso `default` para cobrir quaisquer casos que não estejam explicitamente endereçados:

```swift
let algumPlaneta = Planeta.terra
switch algumPlaneta {
    case .terra:
        print("Lugar inofensivo")
    default:
        print("Não é um lugar seguro para humanos")
}
// Exibe "Lugar inofensivo"
```

Iterating over Enumeration Cases
--------------------------------

For some enumerations, it’s useful to have a collection of all of that enumeration’s cases. You enable this by writing `: CaseIterable` after the enumeration’s name. Swift exposes a collection of all the cases as an `allCases` property of the enumeration type. Here’s an example:

```swift
enum Beverage: CaseIterable {
    case coffee, tea, juice
}
let numberOfChoices = Beverage.allCases.count
print("\(numberOfChoices) beverages available")
// Prints "3 beverages available"
```

In the example above, you write `Beverage.allCases` to access a collection that contains all of the cases of the `Beverage` enumeration. You can use `allCases` like any other collection—the collection’s elements are instances of the enumeration type, so in this case they’re `Beverage` values. The example above counts how many cases there are, and the example below uses a `for` loop to iterate over all the cases.

```swift
for beverage in Beverage.allCases {
    print(beverage)
}
// coffee
// tea
// juice
```

The syntax used in the examples above marks the enumeration as conforming to the [`CaseIterable`](https://developer.apple.com/documentation/swift/caseiterable) protocol. For information about protocols, see [Protocols](Protocols.md).

Associated Values
-----------------

The examples in the previous section show how the cases of an enumeration are a defined (and typed) value in their own right. You can set a constant or variable to `Planet.earth`, and check for this value later. However, it’s sometimes useful to be able to store values of other types alongside these case values. This additional information is called an *associated value*, and it varies each time you use that case as a value in your code.

You can define Swift enumerations to store associated values of any given type, and the value types can be different for each case of the enumeration if needed. Enumerations similar to these are known as *discriminated unions*, *tagged unions*, or *variants* in other programming languages.

For example, suppose an inventory tracking system needs to track products by two different types of barcode. Some products are labeled with 1D barcodes in UPC format, which uses the numbers `0` to `9`. Each barcode has a number system digit, followed by five manufacturer code digits and five product code digits. These are followed by a check digit to verify that the code has been scanned correctly:

![../_images/barcode_UPC_2x.png](../_images/barcode_UPC_2x.png)

Other products are labeled with 2D barcodes in QR code format, which can use any ISO 8859-1 character and can encode a string up to 2,953 characters long:

![../_images/barcode_QR_2x.png](../_images/barcode_QR_2x.png)

It’s convenient for an inventory tracking system to store UPC barcodes as a tuple of four integers, and QR code barcodes as a string of any length.

In Swift, an enumeration to define product barcodes of either type might look like this:

```swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
```

This can be read as:

“Define an enumeration type called `Barcode`, which can take either a value of `upc` with an associated value of type (`Int`, `Int`, `Int`, `Int`), or a value of `qrCode` with an associated value of type `String`.”

This definition doesn’t provide any actual `Int` or `String` values—it just defines the *type* of associated values that `Barcode` constants and variables can store when they are equal to `Barcode.upc` or `Barcode.qrCode`.

You can then create new barcodes using either type:

```swift
var productBarcode = Barcode.upc(8, 85909, 51226, 3)
```

This example creates a new variable called `productBarcode` and assigns it a value of `Barcode.upc` with an associated tuple value of `(8, 85909, 51226, 3)`.

You can assign the same product a different type of barcode:

```swift
productBarcode = .qrCode("ABCDEFGHIJKLMNOP")
```

At this point, the original `Barcode.upc` and its integer values are replaced by the new `Barcode.qrCode` and its string value. Constants and variables of type `Barcode` can store either a `.upc` or a `.qrCode` (together with their associated values), but they can store only one of them at any given time.

You can check the different barcode types using a switch statement, similar to the example in [Matching Enumeration Values with a Switch Statement](#matching-enumeration-values-with-a-switch-statement). This time, however, the associated values are extracted as part of the switch statement. You extract each associated value as a constant (with the `let` prefix) or a variable (with the `var` prefix) for use within the `switch` case’s body:

```swift
switch productBarcode {
    case .upc(let numberSystem, let manufacturer, let product, let check):
        print("UPC: \(numberSystem), \(manufacturer), \(product), \(check).")
    case .qrCode(let productCode):
        print("QR code: \(productCode).")
}
// Prints "QR code: ABCDEFGHIJKLMNOP."
```

If all of the associated values for an enumeration case are extracted as constants, or if all are extracted as variables, you can place a single `var` or `let` annotation before the case name, for brevity:

```swift
switch productBarcode {
    case let .upc(numberSystem, manufacturer, product, check):
        print("UPC : \(numberSystem), \(manufacturer), \(product), \(check).")
    case let .qrCode(productCode):
        print("QR code: \(productCode).")
}
// Prints "QR code: ABCDEFGHIJKLMNOP."
```

Raw Values
----------

The barcode example in [Associated Values](#associated-values) shows how cases of an enumeration can declare that they store associated values of different types. As an alternative to associated values, enumeration cases can come prepopulated with default values (called *raw values*), which are all of the same type.

Here’s an example that stores raw ASCII values alongside named enumeration cases:

```swift
enum ASCIIControlCharacter: Character {
    case tab = "\t"
    case lineFeed = "\n"
    case carriageReturn = "\r"
}
```

Here, the raw values for an enumeration called `ASCIIControlCharacter` are defined to be of type `Character`, and are set to some of the more common ASCII control characters. `Character` values are described in [Strings and Characters](StringsAndCharacters.md).

Raw values can be strings, characters, or any of the integer or floating-point number types. Each raw value must be unique within its enumeration declaration.

**Note**

>Raw values are *not* the same as associated values. Raw values are set to prepopulated values when you first define the enumeration in your code, like the three ASCII codes above. The raw value for a particular enumeration case is always the same. Associated values are set when you create a new constant or variable based on one of the enumeration’s cases, and can be different each time you do so.

### Implicitly Assigned Raw Values

When you’re working with enumerations that store integer or string raw values, you don’t have to explicitly assign a raw value for each case. When you don’t, Swift automatically assigns the values for you.

For example, when integers are used for raw values, the implicit value for each case is one more than the previous case. If the first case doesn’t have a value set, its value is `0`.

The enumeration below is a refinement of the earlier `Planet` enumeration, with integer raw values to represent each planet’s order from the sun:

```swift
enum Planet: Int {
    case mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune
}
```

In the example above, `Planet.mercury` has an explicit raw value of `1`, `Planet.venus` has an implicit raw value of `2`, and so on.

When strings are used for raw values, the implicit value for each case is the text of that case’s name.

The enumeration below is a refinement of the earlier `CompassPoint` enumeration, with string raw values to represent each direction’s name:

```swift
enum CompassPoint: String {
    case north, south, east, west
}
```

In the example above, `CompassPoint.south` has an implicit raw value of `"south"`, and so on.

You access the raw value of an enumeration case with its `rawValue` property:

```swift
let earthsOrder = Planet.earth.rawValue
// earthsOrder is 3

let sunsetDirection = CompassPoint.west.rawValue
// sunsetDirection is "west"
```

### Initializing from a Raw Value

If you define an enumeration with a raw-value type, the enumeration automatically receives an initializer that takes a value of the raw value’s type (as a parameter called `rawValue`) and returns either an enumeration case or `nil`. You can use this initializer to try to create a new instance of the enumeration.

This example identifies Uranus from its raw value of `7`:

let possiblePlanet = Planet(rawValue: 7)
// possiblePlanet is of type Planet? and equals Planet.uranus

Not all possible `Int` values will find a matching planet, however. Because of this, the raw value initializer always returns an *optional* enumeration case. In the example above, `possiblePlanet` is of type `Planet?`, or “optional `Planet`.”

**Note**

>The raw value initializer is a failable initializer, because not every raw value will return an enumeration case. For more information, see [Failable Initializers](../ReferenceManual/Declarations.md#failable-initializers).

If you try to find a planet with a position of `11`, the optional `Planet` value returned by the raw value initializer will be `nil`:

```swift
let positionToFind = 11
if let somePlanet = Planet(rawValue: positionToFind) {
    switch somePlanet {
    case .earth:
        print("Mostly harmless")
    default:
        print("Not a safe place for humans")
    }
} else {
    print("There isn't a planet at position \(positionToFind)")
}
// Prints "There isn't a planet at position 11"
```

This example uses optional binding to try to access a planet with a raw value of `11`. The statement `if let somePlanet = Planet(rawValue: 11)` creates an optional `Planet`, and sets `somePlanet` to the value of that optional `Planet` if it can be retrieved. In this case, it isn’t possible to retrieve a planet with a position of `11`, and so the `else` branch is executed instead.

Recursive Enumerations
----------------------

A *recursive enumeration* is an enumeration that has another instance of the enumeration as the associated value for one or more of the enumeration cases. You indicate that an enumeration case is recursive by writing `indirect` before it, which tells the compiler to insert the necessary layer of indirection.

For example, here is an enumeration that stores simple arithmetic expressions:

```swift
enum ArithmeticExpression {
    case number(Int)
    indirect case addition(ArithmeticExpression, ArithmeticExpression)
    indirect case multiplication(ArithmeticExpression, ArithmeticExpression)
}
```

You can also write `indirect` before the beginning of the enumeration to enable indirection for all of the enumeration’s cases that have an associated value:

```swift
indirect enum ArithmeticExpression {
    case number(Int)
    case addition(ArithmeticExpression, ArithmeticExpression)
    case multiplication(ArithmeticExpression, ArithmeticExpression)
}
```

This enumeration can store three kinds of arithmetic expressions: a plain number, the addition of two expressions, and the multiplication of two expressions. The `addition` and `multiplication` cases have associated values that are also arithmetic expressions—these associated values make it possible to nest expressions. For example, the expression `(5 + 4) * 2` has a number on the right-hand side of the multiplication and another expression on the left-hand side of the multiplication. Because the data is nested, the enumeration used to store the data also needs to support nesting—this means the enumeration needs to be recursive. The code below shows the `ArithmeticExpression` recursive enumeration being created for `(5 + 4) * 2`:

```swift
let five = ArithmeticExpression.number(5)
let four = ArithmeticExpression.number(4)
let sum = ArithmeticExpression.addition(five, four)
let product = ArithmeticExpression.multiplication(sum, ArithmeticExpression.number(2))
```

A recursive function is a straightforward way to work with data that has a recursive structure. For example, here’s a function that evaluates an arithmetic expression:

```swift
func evaluate(_ expression: ArithmeticExpression) -> Int {
    switch expression {
    case let .number(value):
        return value
    case let .addition(left, right):
        return evaluate(left) + evaluate(right)
    case let .multiplication(left, right):
        return evaluate(left) \* evaluate(right)
    }
}

print(evaluate(product))
// Prints "18"
```

This function evaluates a plain number by simply returning the associated value. It evaluates an addition or multiplication by evaluating the expression on the left-hand side, evaluating the expression on the right-hand side, and then adding them or multiplying them.
