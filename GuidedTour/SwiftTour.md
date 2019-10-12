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

Você pode usar `if` e `let` juntos para trabalhar com valores que podem não existir. Esses valores são representados como optionals. Um valor optional contem um valor ou contem `nil` para indicar que o valor não existe. Escreva uma interrogação (`?`) após o tipo do valor para indicar o valor como optional.

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

**Experimente**

> Mudar `optionalName` para `nil`. Qual a saudação que você vai ter? Adicione uma condição `else` que mude a saudação se `optionalValue` for `nil`.

Se o valor optional é `nil`, a condicional é `false` e o código nas chaves é pulado. Caso contrário, o valor optional é desempacotado e atribuída para a constante após o `let`, que faz o valor desempacotado acessível dentro do bloco de código.

Outra maneira de manipular valores optional é prover um valor padrão usando o operador `??`. Se o valor do optional estiver faltando, o valor padrão é usado.

```swift
let nickName: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickName ?? fullName)"
```

Switches suportam qualquer tipo de dado e uma grande variedade de operações de comparação, eles não são limitado a inteiros e testes de igualdade.

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

**Experimente**

> Tente remover o caso padrão. Qual o erro que você recebe?

Perceba como `let` pode ser usado em um padrão para atribuir o valor que corresponde o padrão para uma constante.

Após executar o código dentro do switch case que coincidiu, o programa sai da declaração do switch. A execução não continua para o proximo case, então não há necessidade de usar break explicitamente no switch, no final de casa código dos cases.

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

**Experimente**

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

Funções e Closures
----------------------

Use `func` para declarar uma função. Chame uma função ao escrever seu nome seguido da lista de argumentos entre parênteses. Use `->` para separar os nomes e tipos dos parâmetros do tipo de retorno da função.

```swift
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet(person: "Bob", day: "Tuesday")
```

**Experimento**

> Remova o parâmetro `day`. Adicione um parâmetro para incluir o especial do almoço de hoje na saudação.

Por padrão, funções usam os nomes dos seus parâmetros como rótulos para os seus argumentos. Escreva um rótulo de argumento customizado antes do nome do parâmetro, ou escreva `_` para não usar um rótulo de argumento.

```swift
func greet(_ person: String, on day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet("John", on: "Wednesday")
```

Use uma tupla para criar um valor composto—por exemplo, para retornar múltiplos valores de uma função. Os elementos de uma tupla podem ser referenciados ou por nome ou por número.

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
// Imprime "120"
print(statistics.2)
// Imprime "120"
```

Funções podem ser aninhadas. Funções aninhadas tem acesso a variáveis que foram declaradas na função externa. Você pode usar funções aninhadas para organizar o código numa função que é longa ou complexa.

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

Funções são um tipo de primeira classe. Isso significa que uma função pode retornar outra função.

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

Uma função pode receber outra função como um de seus argumentos.

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

Funções são na verdade um tipo especial de closures: blocos de código que podem ser chamados depois. O código dentro de uma closure tem acesso a coisas como variáveis e funções que estava disponíveis no escopo onde a closure foi criada, mesmo se a closure está em um escopo diferente quando é executada.

Você já viu um exemplo disso com funções aninhadas. Você pode escrever uma closure sem um nome ao circundar o código com (`{}`). Use `in` para separar os argumentos e o tipo de retorno do corpo.

```swift
numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
```

**Experimento**

> Reescreva a closure para retornar zero para todos os números ímpares.

Você tem diversas opções para escrever closures de forma mais concisa. Quando o tipo de uma closure já é conhecido, como o callback para um delegate, você pode omitir o tipo dos seus parâmetros, seu tipo de retorno, ou ambos. Closures de expressão única retornam implicitamente o valor de sua única expressão.

```swift
let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)
// Imprime "[60, 57, 21, 36]"
```

Você pode se referir aos parâmteros por número ao invés do nome, essa abordagem é especialmente útil em closures muito curtas. Uma closure passada como o último argumento para uma função pode aparecer imediatamente depois do parênteses. Quando uma closure é o único argumento de uma função, você pode omitir os parênteses completamente.

```swift
let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
// Imprime "[20, 19, 12, 7]"
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

Métodos em uma subclasse que substituem a implementação da superclasse são marcados com `override` a substituição de um método por acidente, sem `override`, é detectada pelo compilador como um erro. O compilador também detecta métodos com `override` que na verdade não substituem nenhum método na superclasse.

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
Enquanto estiver trabalhando com valores optional, você pode escrever `?` antes de operações como métodos, propriedades e assinaturas. Se o valor antes de `?` for `nil`, tudo depois de `?` é ignorado e o valor de toda a expressão é `nil`.

Caso contrário, o valor optional é desempacotado, e tudo depois de `?` age sobre o valor desempacotado. Em ambos os casos, o valor de toda a expressão é um valor optional.


```swift
let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
let sideLength = optionalSquare?.sideLength
``` 

Enumerations and Structures
---------------------------

Use `enum` para criar uma enumeração, como classes e todos os outros tipos nomeados, enumerações podem ter metódos associados a eles.

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

**Experimente**

> Escreva uma função que compare dois `Rank` através da comparação de seus raw values.

Por padrão, Swift atribui raw values começando do zero e incrementando um a cada vez, porém você pode modificar esse comportamento explicitando valores. No exemplo acima, `Ace` é explicitamente dado o valor de `1`, e o resto dos raw values são atribuidos em ordem. Você pode também utilizar strings ou floating-point numbers como o raw type de uma enumeração. Use a propriedade `rawValue` para acessar o raw value de um case de enumeração.

Use o inicializador `init?(rawValue:)` para construir uma instância de uma enumeração a partir de um raw value. Ele irá retornar o case que corresponde ao raw value ou `nil` se não houver um `Rank` correspondente.

```swift
if let convertedRank = Rank(rawValue: 3) {
    let threeDescription = convertedRank.simpleDescription()
}
```

Os case values de uma enumeração são valores reais, não apenas outra maneira de escrever seus raw values. Na verdade, em cases onde não existem raw values significativos, você não precisa forncer um.

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

**Experimente**

> Adicione o metódo `color()` ao `Suit` que retorna "black" para spades e clubs, e retorna "red" para hearts e diamonds.

Perceba as duas maneiras que o case `hearts` da enumeração é referido acima: Quando atribuímos um valor a constante `heart`, o case da enumeração `Suits.hearts` é referido pelo seu nome completo porque a constante não tem um tipo específico explicitado. Dentro do switch, o case da enumeração é referido através da sua forma abreviada `.hearts` pois o valor do `self` já é conhecido como um `Suit`. Você pode utilizar a forma abreviada toda vez que o tipo do valor já é conhecido.

Se a enumeração tiver raw values, esses valores são determinados como parte da declaração, o que significa que todas as instâncias de um case específico de uma enumeração sempre tem o mesmo raw value. Outra escolha para cases de uma enumeração é ter associated values com o case, esses valores são determinados quando você constrói uma instância, e eles podem ser diferentes para cada instância de um case da enumeração. Você pode pensar nos associated values se comportando como stored properties de uma instância do case de uma enumeração. Por exemplo, considere o caso de solicitar os tempos de pôr do sol(sunset) e nascer do sol (sunrise) de um servidor. O servidor vai responder com a informação solicitada ou com a descrição de o que deu errado.

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

**Experimente**

> Adicione um terceiro case ao `ServerResponse` e ao switch.

Perceba como os tempos de pôr do sol(sunset) e nascer do sol (sunrise) são extraídos do valor do `ServerResponse` como parte do valor correspondente comparando os cases do switch.

Use `struct` para criar uma structure. Structures possuem muitos dos comportamentos de classes, incluíndo metódos e inicializadores. Uma das diferenças mais importantes entre structures e classes é que structures são sempre copiadas quando passadas no código, já classes são passadas por referência.

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

**Experimente**

> Escreva uma função que retorne um array contendo o deck completo de cartas, com uma carta de cada combinação de rank e suit.

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

Tratamento de Erros
--------------

Você representa erros usando qualquer tipo que adota o protocolo `Error`.

```swift
enum PrinterError: Error {
    case outOfPaper
    case noToner
    case onFire
}
```

Use `throw` para disparar um erro e `throws` para marcar uma função que pode disparar um error. Se você disparar um error em uma função, a função retorna imediatamente e o código que chamou a função trata o error.


```swift
func send(job: Int, toPrinter printerName: String) throws -> String {
    if printerName == "Never Has Toner" {
        throw PrinterError.noToner
    }
    return "Job sent"
}
```
Existem várias maneiras de tratar erros. Uma maneira é usar `do`\-`catch`. Dentro do bloco `do`, você marca o código que pode lançar um error ao escrever `try` na frente dele. Dentro do bloco `catch`, o erro recebe automaticamente o nome `error` a não ser que você dê um nome diferente.


```swift
do {
    let printerResponse = try send(job: 1040, toPrinter: "Bi Sheng")
    print(printerResponse)
} catch {
    print(error)
}
// Prints "Job sent"
```


**Experimente**

> Mude o nome do printer para `"Never Has Toner"`, para que a função `send(job:toPrinter:)` dispare um error.

Você pode fornecer múltiplos blocos de `catch` que tratam errors específicos. Você escreve um pattern após o `catch` da mesma maneira que você faz após o `case` em um switch.

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
// Imprime "Job sent"
```


**Experimente**

> Adicione um código para disparar um error dentro do bloco `do`. Que tipo de error você precisa disparar para que o error seja tratado dentro do primeiro bloco de `catch`? E o segundo e terceiro bloco?

Outra maneira de tratar errors é usando o `try?` para converter o resultado em um optional. Se a função disparar um error, o error específico é descartado e o resultado é `nil`. Se não, o resultado é um optional contendo o valor retornado pela função.


```swift
let printerSuccess = try? send(job: 1884, toPrinter: "Mergenthaler")
let printerFailure = try? send(job: 1885, toPrinter: "Never Has Toner")
```

Use `defer` para escrever um bloco de código que é executado após todos os outros códigos na função, logo antes da função retornar. O código é executado mesmo se a função disparar um error. Você pode usar `defer` para escrever o código setup e o cleanup próximo um ao outro, mesmo quando eles devem ser executados em momentos diferentes.

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
// Imprime "false"
```

Generics
--------

Escreva um nome dentro de parênteses angulares para criar uma função ou tipo genérico.

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

Você pode criar formas genericas de funções e métodos, bem como classes, enums, and structs.

```swift
// Reimplementando o tipo opcional da biblioteca padrão da Swift
enum OptionalValue<Wrapped> {
    case none
    case some(Wrapped)
}
var possibleInteger: OptionalValue<Int> = .none
possibleInteger = .some(100)
```

Use `where` logo antes do corpo para especificar uma lista de requisito, por exemplo, para exigir que um tipo implemente um protocolo, para exigir que dois tipos sejam iguais, ou para exigir que uma classe tenha uma superclasse em particular.

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

**Experimento**

> Modifique a função `anyCommonElements(_:_:)` para criar uma função que retorne um array dos elementos que qualquer uma das duas sequências tenham em comun.

Escrever `<T: Equatable>` é o mesmo que escrever  `<T> ... where T: Equatable`.
