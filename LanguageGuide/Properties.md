Propriedades

Propriedades
==========

Propriedades associam valores com uma classe, estrutura, ou enumeração em particular. Propriedades armazenadas guardam constantes e valores variáveis como parte de uma instância, enquanto propriedades computadas calculam (ao invés de armazenar) um valor. Propriedades computadas estão disponíveis em classes, estruturas e enumerações. Propriedades armazenadas estão disponíveis somente em classes e estruturas.

Propriedades armazenadas e computadas são usualmente associadas com instâncias de um tipo em particular. No entanto, propriedades também podem ser associadas com o próprio tipo. Essas propriedades são conhecidas como propriedades de tipo.

Além disso, você pode definir *property observers* para observar mudanças no valor de uma propriedade, que podem responder com ações personalizadas. *Property observers* podem ser adicionados a propriedades armazenadas que você definiu, e também propriedades que uma subclasse herdou da sua superclasse.

Você também pode usar um *property wrapper* para reusar código no *getter* e *setter* de múltiplas propriedades.

Propriedades Armazenadas
-----------------

Na sua forma mais simples, uma propriedade armazenada é uma constante ou variável que é armazenada como parte de uma instância de uma classe, ou estrutura. Propriedades armazenadas podem ser *propriedades armazenadas variáveis* (indicadas pela palavra-chave `var`) ou *propriedades armazenadas constantes* (indicadas pela palavra-chave `let`).

Você pode fornecer um valor *default* para uma propriedade armazenada como parte da sua definição, como descrito em [Default Property Values](Initialization.xhtml#default-property-values). Você também pode definir e modificar o valor inicial de uma propriedade armazenada durante a inicialização. Isso é verdade até mesmo para propriedades armazenadas constantes, como descrito em [Assigning Constant Properties During Initialization](Initialization.xhtml#assigning-constant-properties-during-initialization).

O exemplo abaixo define uma estrutura chamada `FixedLengthRange`, que descreve um intervalo de números inteiros cujo comprimento do intervalo não pode ser alterado após a criação:

```swift
struct FixedLengthRange {
    var firstValue: Int
    let length: Int
}
var rangeOfThreeItems = FixedLengthRange(firstValue: 0, length: 3)
// o intervalo representa os valores inteiros 0, 1, e 2
rangeOfThreeItems.firstValue = 6
// o intervalo agora representa os valores inteiros 6, 7 e 8
```

Instâncias de `FixedLengthRange` possuem uma propriedade armazenada variável chamada `firstValue` e uma propriedade armazenada constante chamada `length`. No exemplo acima, `length` é inicializada quando o novo intervalo é criado e não pode ser mudada depois, porque é uma propriedade constante.

### Propriedades Armazenadas de Instâncias de Estrutura Constante

Se você criar uma instância de uma estrutura e atribuir essa instância a uma constante, não poderá modificar as propriedades da instância, mesmo que elas tenham sido declaradas como propriedades variáveis:

```swift
let rangeOfFourItems = FixedLengthRange(firstValue: 0, length: 4)
// esse intervalo representa os valores inteiro 0, 1, 2 e 3
rangeOfFourItems.firstValue = 6
// isso vai reportar um erro, mesmo firstValue sendo uma propriedade variável
```

Por `rangeOfFourItems` ser declarada como uma constante (com a palavra-chave `let`), não é possível alterar a sua propriedade `firstValue`, mesmo `firstValue` sendo uma propriedade variável.

Esse comportamento é devido a estruturas serem *value types*. Quando uma instância de um *value type* é indicada como constante, todas as suas propriedades também são.

O mesmo não é verdade para classes, que são *reference types*. Se você atribuir uma instância de um *reference type* a uma constante, ainda poderá alterar as propriedades variáveis dessa instância.

### Propriedades Computadas *Lazy*

Uma propriedade computada *lazy* é uma propriedade cujo valor inicial não é calculado até o seu primeiro uso. Uma propriedade computada é indicada como *lazy* escrevendo o modificador `lazy` antes da sua declaração.

**Nota**

> Você deve sempre declarar uma propriedade *lazy* como variável (com a palavra-chave `var`), porque o seu valor inicial pode não ser recuperado até depois que a inicialização da instância seja concluída. As propriedades constantes devem sempre ter um valor antes que a inicialização seja concluída e, portanto, não podem ser declaradas como *lazy*.

Propriedades *lazy* são úteis quando o valor inicial de uma propriedade é dependente de fatores externos cujos valores não são conhecidos até depois que a inicialização da instância seja concluída. Propriedades *lazy* também são úteis quando o valor inicial de uma propriedade requer um *setup* inicial complexo ou computacionalmente custoso que não deve ser executado a menos, ou até, que seja necessário.

O exemplo abaixo usa uma propriedade armazenada *lazy* para evitar a inicialização desnecessária de uma classe complexa. O exemplo define duas classes chamadas `DataImporter` e `DataManager`, nenhuma das quais é mostrada na íntegra:

```swift
class DataImporter {
    /*
    DataImporter é uma classe para importar dados de um arquivo externo.
    Presume-se que a classe leve um tempo não trivial para inicializar.
    */
    var filename = "data.txt"
    // a classe DataImporter forneceria a funcionalidade de importação de dados aqui.
}

class DataManager {
    lazy var importer = DataImporter()
    var data = [String]()
    // a classe DataManager forneceria a funcionalidade de importação de dados aqui.
}

let manager = DataManager()
manager.data.append("Some data")
manager.data.append("Some more data")
// a instância de DataImporter para a propriedade importer ainda não foi criada.
```

A classe `DataManager` possui uma propriedade armazenada chamada `data`, que é inicializada com uma *array* vazia de valores `String`. Embora o restante da sua funcionalidade não seja mostrado, o propósito dessa classe `DataManager` é generenciar e fornecer acesso a essa *array* de `String`. 

Parte da funcionalidade da classe `DataManager` é a habilidade de importar dados de um arquivo. Essa funcionalidade é fornecida pela classe `DataImporter`, e presume-se que leva um tempo não trivial para inicializar. Isso pode ser porque a instância de `DataImporter` precisa abrir um arquivo e ler o conteúdo para a memória quando a instância de `DataImporter` é inicializada.

É possível para uma instância de `DataManager` gerenciar os seus dados sem nunca importar dados de um arquivo, logo não é necessário criar uma nova instância de `DataImporter` quando o próprio `DataManager` é criado. Em vez disso, faz mais sentido criar a instância de `DataImporter` se e quando for usada pela primeira vez.

Como está marcada com o modificador `lazy`, a instância` DataImporter` da propriedade `importer` é criada apenas quando a propriedade ` importer` é acessada pela primeira vez, como quando a propriedade `filename` é consultada:

```swift
print(manager.importer.filename)
// a instância de DataImporter para a propriedade importer agora foi criada
// Imprime "data.txt"
```

**Nota**

> Se uma propriedade indicada com o modificador `lazy` é acessada por múltiplas *threads* simultaneamente e a propriedade ainda não foi inicializada, não há garantia de que ela será inicializada apenas uma vez.

### Propriedades Armazenadas e Variáveis de Instância

Se você tem experiência com a linguaguem Objective-C, pode saber que ela  fornece duas maneiras de armazenar valores e referências como parte de uma instância de classe. Além das propriedades, você pode usar variáveis de instância como um *backup* para os valores armazenados em uma propriedade.

Swift unifica esses conceitos em uma única declaração de propriedade. Uma propriedade em Swift não possui uma variável de instância correspondente e o armazenamento de *backup* de uma propriedade não é acessado diretamente. Essa abordagem evita confusão sobre como o valor é acessado em diferentes contextos e simplifica a declaração da propriedade em uma única declaração definitiva. Todas as informações sobre a propriedade, incluindo nome, tipo e características de gerenciamento de memória, são definidas em um único local como parte da definição do tipo.

Computed Properties
-------------------

In addition to stored properties, classes, structures, and enumerations can define *computed properties*, which do not actually store a value. Instead, they provide a getter and an optional setter to retrieve and set other properties and values indirectly.

```swift
struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}
var square = Rect(origin: Point(x: 0.0, y: 0.0),
size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
print("square.origin is now at (\(square.origin.x), \(square.origin.y))")
// Prints "square.origin is now at (10.0, 10.0)"
```

This example defines three structures for working with geometric shapes:

*   `Point` encapsulates the x- and y-coordinate of a point.
    
*   `Size` encapsulates a `width` and a `height`.
    
*   `Rect` defines a rectangle by an origin point and a size.
    

The `Rect` structure also provides a computed property called `center`. The current center position of a `Rect` can always be determined from its `origin` and `size`, and so you don’t need to store the center point as an explicit `Point` value. Instead, `Rect` defines a custom getter and setter for a computed variable called `center`, to enable you to work with the rectangle’s `center` as if it were a real stored property.

The example above creates a new `Rect` variable called `square`. The `square` variable is initialized with an origin point of `(0, 0)`, and a width and height of `10`. This square is represented by the blue square in the diagram below.

The `square` variable’s `center` property is then accessed through dot syntax (`square.center`), which causes the getter for `center` to be called, to retrieve the current property value. Rather than returning an existing value, the getter actually calculates and returns a new `Point` to represent the center of the square. As can be seen above, the getter correctly returns a center point of `(5, 5)`.

The `center` property is then set to a new value of `(15, 15)`, which moves the square up and to the right, to the new position shown by the orange square in the diagram below. Setting the `center` property calls the setter for `center`, which modifies the `x` and `y` values of the stored `origin` property, and moves the square to its new position.

![../_images/computedProperties_2x.png](../_images/computedProperties_2x.png)

### Shorthand Setter Declaration

If a computed property’s setter doesn’t define a name for the new value to be set, a default name of `newValue` is used. Here’s an alternative version of the `Rect` structure that takes advantage of this shorthand notation:

```swift
struct AlternativeRect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set {
            origin.x = newValue.x - (size.width / 2)
            origin.y = newValue.y - (size.height / 2)
        }
    }
}
```

### Shorthand Getter Declaration

If the entire body of a getter is a single expression, the getter implicitly returns that expression. Here’s an another version of the `Rect` structure that takes advantage of this shorthand notation and the shorthand notation for setters:

```swift
struct CompactRect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            Point(x: origin.x + (size.width / 2), y: origin.y + (size.height / 2))
        }
        set {
            origin.x = newValue.x - (size.width / 2)
            origin.y = newValue.y - (size.height / 2)
        }
    }
}
```

Omitting the `return` from a getter follows the same rules as omitting `return` from a function, as described in [Functions With an Implicit Return](Functions.md#functions-with-an-implicit-return).

### Read-Only Computed Properties

A computed property with a getter but no setter is known as a *read-only computed property*. A read-only computed property always returns a value, and can be accessed through dot syntax, but cannot be set to a different value.

**Note**

>You must declare computed properties—including read-only computed properties—as variable properties with the `var` keyword, because their value is not fixed. The `let` keyword is only used for constant properties, to indicate that their values cannot be changed once they are set as part of instance initialization.

You can simplify the declaration of a read-only computed property by removing the `get` keyword and its braces:

```swift
struct Cuboid {
    var width = 0.0, height = 0.0, depth = 0.0
    var volume: Double {
        return width * height * depth
    }
}
let fourByFiveByTwo = Cuboid(width: 4.0, height: 5.0, depth: 2.0)
print("the volume of fourByFiveByTwo is \(fourByFiveByTwo.volume)")
// Prints "the volume of fourByFiveByTwo is 40.0"
```

This example defines a new structure called `Cuboid`, which represents a 3D rectangular box with `width`, `height`, and `depth` properties. This structure also has a read-only computed property called `volume`, which calculates and returns the current volume of the cuboid. It doesn’t make sense for `volume` to be settable, because it would be ambiguous as to which values of `width`, `height`, and `depth` should be used for a particular `volume` value. Nonetheless, it is useful for a `Cuboid` to provide a read-only computed property to enable external users to discover its current calculated volume.

Property Observers
------------------

Property observers observe and respond to changes in a property’s value. Property observers are called every time a property’s value is set, even if the new value is the same as the property’s current value.

You can add property observers to any stored properties you define, except for lazy stored properties. You can also add property observers to any inherited property (whether stored or computed) by overriding the property within a subclass. You don’t need to define property observers for nonoverridden computed properties, because you can observe and respond to changes to their value in the computed property’s setter. Property overriding is described in [Overriding](Inheritance.md#overriding).

You have the option to define either or both of these observers on a property:

*   `willSet` is called just before the value is stored.
    
*   `didSet` is called immediately after the new value is stored.
    

If you implement a `willSet` observer, it’s passed the new property value as a constant parameter. You can specify a name for this parameter as part of your `willSet` implementation. If you don’t write the parameter name and parentheses within your implementation, the parameter is made available with a default parameter name of `newValue`.

Similarly, if you implement a `didSet` observer, it’s passed a constant parameter containing the old property value. You can name the parameter or use the default parameter name of `oldValue`. If you assign a value to a property within its own `didSet` observer, the new value that you assign replaces the one that was just set.

**Note**

>The `willSet` and `didSet` observers of superclass properties are called when a property is set in a subclass initializer, after the superclass initializer has been called. They are not called while a class is setting its own properties, before the superclass initializer has been called.

For more information about initializer delegation, see [Initializer Delegation for Value Types](Initialization.md#initializer-delegation-for-value-types) and [Initializer Delegation for Class Types](Initialization.md#initializer-delegation-for-class-types).

Here’s an example of `willSet` and `didSet` in action. The example below defines a new class called `StepCounter`, which tracks the total number of steps that a person takes while walking. This class might be used with input data from a pedometer or other step counter to keep track of a person’s exercise during their daily routine.

```swift
class StepCounter {
    var totalSteps: Int = 0 {
    willSet(newTotalSteps) {
        print("About to set totalSteps to \(newTotalSteps)")
}
    didSet {
        if totalSteps > oldValue {
        print("Added \(totalSteps - oldValue) steps")
            }
        }
    }
}
let stepCounter = StepCounter()
stepCounter.totalSteps = 200
// About to set totalSteps to 200
// Added 200 steps
stepCounter.totalSteps = 360
// About to set totalSteps to 360
// Added 160 steps
stepCounter.totalSteps = 896
// About to set totalSteps to 896
// Added 536 steps
```

The `StepCounter` class declares a `totalSteps` property of type `Int`. This is a stored property with `willSet` and `didSet` observers.

The `willSet` and `didSet` observers for `totalSteps` are called whenever the property is assigned a new value. This is true even if the new value is the same as the current value.

This example’s `willSet` observer uses a custom parameter name of `newTotalSteps` for the upcoming new value. In this example, it simply prints out the value that is about to be set.

The `didSet` observer is called after the value of `totalSteps` is updated. It compares the new value of `totalSteps` against the old value. If the total number of steps has increased, a message is printed to indicate how many new steps have been taken. The `didSet` observer does not provide a custom parameter name for the old value, and the default name of `oldValue` is used instead.

**Note**

>If you pass a property that has observers to a function as an in-out parameter, the `willSet` and `didSet` observers are always called. This is because of the copy-in copy-out memory model for in-out parameters: The value is always written back to the property at the end of the function. For a detailed discussion of the behavior of in-out parameters, see [In-Out Parameters](../ReferenceManual/Declarations.xhtml#ID545).

Property Wrappers
-----------------

A property wrapper adds a layer of separation between code that manages how a property is stored and the code that defines a property. For example, if you have properties that provide thread-safety checks or store their underlying data in a database, you have to write that code on every property. When you use a property wrapper, you write the management code once when you define the wrapper, and then reuse that management code by applying it to multiple properties.

To define a property wrapper, you make a structure, enumeration, or class that defines a `wrappedValue` property. In the code below, the `TwelveOrLess` structure ensures that the value it wraps always contains a number less than or equal to 12. If you ask it to store a larger number, it stores 12 instead.

```swift
@propertyWrapper
struct TwelveOrLess {
    private var number = 0
    var wrappedValue: Int {
        get { return number }
        set { number = min(newValue, 12) }
    }
}
```

The setter ensures that new values are less than 12, and the getter returns the stored value.

**Note**

>The declaration for `number` in the example above marks the variable as `private`, which ensures `number` is used only in the implementation of `TwelveOrLess`. Code that’s written anywhere else accesses the value using the getter and setter for `wrappedValue`, and can’t use `number` directly. For information about `private`, see [Access Control](AccessControl.md).

You apply a wrapper to a property by writing the wrapper’s name before the property as an attribute. Here’s a structure that stores a small rectangle, using the same (rather arbitrary) definition of “small” that’s implemented by the `TwelveOrLess` property wrapper:

```swift
struct SmallRectangle {
    @TwelveOrLess var height: Int
    @TwelveOrLess var width: Int
}

var rectangle = SmallRectangle()
print(rectangle.height)
// Prints "0"

rectangle.height = 10
print(rectangle.height)
// Prints "10"

rectangle.height = 24
print(rectangle.height)
// Prints "12"
```

The `height` and `width` properties get their initial values from the definition of `TwelveOrLess`, which sets `TwelveOrLess.number` to zero. Storing the number 10 into `rectangle.height` succeeds because it’s a small number. Trying to store 24 actually stores a value of 12 instead, because 24 is too large for the property setter’s rule.

When you apply a wrapper to a property, the compiler synthesizes code that provides storage for the wrapper and code that provides access to the property through the wrapper. (The property wrapper is responsible for storing the wrapped value, so there’s no synthesized code for that.) You could write code that uses the behavior of a property wrapper, without taking advantage of the special attribute syntax. For example, here’s a version of `SmallRectangle` from the previous code listing that wraps its properties in the `TwelveOrLess` structure explicitly, instead of writing `@TwelveOrLess` as an attribute:

```swift
struct SmallRectangle {
    private var _height = TwelveOrLess()
    private var _width = TwelveOrLess()
    var height: Int {
        get { return _height.wrappedValue }
        set { _height.wrappedValue = newValue }
    }
    var width: Int {
        get { return _width.wrappedValue }
        set { _width.wrappedValue = newValue }
    }
}
```

The `_height` and `_width` properties store an instance of the property wrapper, `TwelveOrLess`. The getter and setter for `height` and `width` wrap access to the `wrappedValue` property.

### Setting Initial Values for Wrapped Properties

The code in the examples above sets the initial value for the wrapped property by giving `number` an initial value in the definition of `TwelveOrLess`. Code that uses this property wrapper, can’t specify a different initial value for a property that’s wrapped by `TwelveOrLess`—for example, the definition of `SmallRectangle` can’t give `height` or `width` initial values. To support setting an initial value or other customization, the property wrapper needs to add an initializer. Here’s an expanded version of `TwelveOrLess` called `SmallNumber` that defines initializers that set the wrapped and maximum value:

```swift
@propertyWrapper
    struct SmallNumber {
    private var maximum: Int
    private var number: Int

    var wrappedValue: Int {
        get { return number }
        set { number = min(newValue, maximum) }
    }

    init() {
        maximum = 12
        number = 0
    }
    init(wrappedValue: Int) {
        maximum = 12
        number = min(wrappedValue, maximum)
    }
    init(wrappedValue: Int, maximum: Int) {
        self.maximum = maximum
        number = min(wrappedValue, maximum)
    }
}
```

The definition of `SmallNumber` includes three initializers—`init()`, `init(wrappedValue:)`, and `init(wrappedValue:maximum:)`—which the examples below use to set the wrapped value and the maximum value. For information about initialization and initializer syntax, see [Initialization](Initialization.md).

When you apply a wrapper to a property and you don’t specify an initial value, Swift uses the `init()` initializer to set up the wrapper. For example:

```swift
struct ZeroRectangle {
    @SmallNumber var height: Int
    @SmallNumber var width: Int
}

var zeroRectangle = ZeroRectangle()
print(zeroRectangle.height, zeroRectangle.width)
// Prints "0 0"
```

The instances of `SmallNumber` that wrap `height` and `width` are created by calling `SmallNumber()`. The code inside that initializer sets the initial wrapped value and the initial maximum value, using the default values of zero and 12. The property wrapper still provides all of the initial values, like the earlier example that used `TwelveOrLess` in `SmallRectangle`. Unlike that example, `SmallNumber` also supports writing those initial values as part of declaring the property.

When you specify an initial value for the property, Swift uses the `init(wrappedValue:)` initializer to set up the wrapper. For example:

```swift
struct UnitRectangle {
    @SmallNumber var height: Int = 1
    @SmallNumber var width: Int = 1
}

var unitRectangle = UnitRectangle()
print(unitRectangle.height, unitRectangle.width)
// Prints "1 1"
```

When you write `= 1` on a property with a wrapper, that’s translated into a call to the `init(wrappedValue:)` initializer. The instances of `SmallNumber` that wrap `height` and `width` are created by calling `SmallNumber(wrappedValue: 1)`. The initializer uses the wrapped value that’s specified here, and it uses the default maximum value of 12.

When you write arguments in parentheses after the custom attribute, Swift uses the initializer that accepts those arguments to set up the wrapper. For example, if you provide an initial value and a maximum value, Swift uses the `init(wrappedValue:maximum:)` initializer:

```swift
struct NarrowRectangle {
    @SmallNumber(wrappedValue: 2, maximum: 5) var height: Int
    @SmallNumber(wrappedValue: 3, maximum: 4) var width: Int
}

var narrowRectangle = NarrowRectangle()
print(narrowRectangle.height, narrowRectangle.width)
// Prints "2 3"

narrowRectangle.height = 100
narrowRectangle.width = 100
print(narrowRectangle.height, narrowRectangle.width)
// Prints "5 4"
```

The instance of `SmallNumber` that wraps `height` is created by calling `SmallNumber(wrappedValue: 2, maximum: 5)`, and the instance that wraps `width` is created by calling `SmallNumber(wrappedValue: 3, maximum: 4)`.

By including arguments to the property wrapper, you can set up the initial state in the wrapper or pass other options to the wrapper when it’s created. This syntax is the most general way to use a property wrapper. You can provide whatever arguments you need to the attribute, and they’re passed to the initializer.

When you include property wrapper arguments, you can also specify an initial value using assignment. Swift treats the assignment like a `wrappedValue` argument and uses the initializer that accepts the arguments you include. For example:

```swift
struct MixedRectangle {
    @SmallNumber var height: Int = 1
    @SmallNumber(maximum: 9) var width: Int = 2
}

var mixedRectangle = MixedRectangle()
print(mixedRectangle.height)
// Prints "1"

mixedRectangle.height = 20
print(mixedRectangle.height)
// Prints "12"
```

The instance of `SmallNumber` that wraps `height` is created by calling `SmallNumber(wrappedValue: 1)`, which uses the default maximum value of 12. The instance that wraps `width` is created by calling `SmallNumber(wrappedValue: 2, maximum: 9)`.

### Projecting a Value From a Property Wrapper

In addition to the wrapped value, a property wrapper can expose additional functionality by defining a *projected value*—for example, a property wrapper that manages access to a database can expose a `flushDatabaseConnection()` method on its projected value. The name of the projected value is the same as the wrapped value, except it begins with a dollar sign (`$`). Because your code can’t define properties that start with `$` the projected value never interferes with properties you define.

In the `SmallNumber` example above, if you try to set the property to a number that’s too large, the property wrapper adjusts the number before storing it. The code below adds a `projectedValue` property to the `SmallNumber` structure to keep track of whether the property wrapper adjusted the new value for the property before storing that new value.

```swift
@propertyWrapper
struct SmallNumber {
    private var number = 0
    var projectedValue = false
    var wrappedValue: Int {
        get { return number }
        set {
            if newValue > 12 {
                number = 12
                projectedValue = true
            } else {
                number = newValue
                projectedValue = false
            }
        }
    }
}
struct SomeStructure {
    @SmallNumber var someNumber: Int
}
var someStructure = SomeStructure()

someStructure.someNumber = 4
print(someStructure.$someNumber)
// Prints "false"

someStructure.someNumber = 55
print(someStructure.$someNumber)
// Prints "true"
```

Writing `s.$someNumber` accesses the wrapper’s projected value. After storing a small number like four, the value of `s.$someNumber` is `false`. However, the projected value is `true` after trying to store a number that’s too large, like 55.

A property wrapper can return a value of any type as its projected value. In this example, the property wrapper exposes only one piece of information—whether the number was adjusted—so it exposes that Boolean value as its projected value. A wrapper that needs to expose more information can return an instance of some other data type, or it can return `self` to expose the instance of the wrapper as its projected value.

When you access a projected value from code that’s part of the type, like a property getter or an instance method, you can omit `self.` before the property name, just like accessing other properties. The code in the following example refers to the projected value of the wrapper around `height` and `width` as `$height` and `$width`:

```swift
enum Size {
    case small, large
}

struct SizedRectangle {
    @SmallNumber var height: Int
    @SmallNumber var width: Int

    mutating func resize(to size: Size) -> Bool {
        switch size {
        case .small:
            height = 10
            width = 20
        case .large:
            height = 100
            width = 100
        }
    return $height || $width
    }
}
```

Because property wrapper syntax is just syntactic sugar for a property with a getter and a setter, accessing `height` and `width` behaves the same as accessing any other property. For example, the code in `resize(to:)` accesses `height` and `width` using their property wrapper. If you call `resize(to: .large)`, the switch case for `.large` sets the rectangle’s height and width to 100. The wrapper prevents the value of those properties from being larger than 12, and it sets the projected value to `true`, to record the fact that it adjusted their values. At the end of `resize(to:)`, the return statement checks `$height` and `$width` to determine whether the property wrapper adjusted either `height` or `width`.

Global and Local Variables
--------------------------

The capabilities described above for computing and observing properties are also available to *global variables* and *local variables*. Global variables are variables that are defined outside of any function, method, closure, or type context. Local variables are variables that are defined within a function, method, or closure context.

The global and local variables you have encountered in previous chapters have all been *stored variables*. Stored variables, like stored properties, provide storage for a value of a certain type and allow that value to be set and retrieved.

However, you can also define *computed variables* and define observers for stored variables, in either a global or local scope. Computed variables calculate their value, rather than storing it, and they are written in the same way as computed properties.

**Note**

>Global constants and variables are always computed lazily, in a similar manner to [Lazy Stored Properties](#lazy-stored-properties). Unlike lazy stored properties, global constants and variables do not need to be marked with the `lazy` modifier.
>
>Local constants and variables are never computed lazily.

Type Properties
---------------

Instance properties are properties that belong to an instance of a particular type. Every time you create a new instance of that type, it has its own set of property values, separate from any other instance.

You can also define properties that belong to the type itself, not to any one instance of that type. There will only ever be one copy of these properties, no matter how many instances of that type you create. These kinds of properties are called *type properties*.

Type properties are useful for defining values that are universal to *all* instances of a particular type, such as a constant property that all instances can use (like a static constant in C), or a variable property that stores a value that is global to all instances of that type (like a static variable in C).

Stored type properties can be variables or constants. Computed type properties are always declared as variable properties, in the same way as computed instance properties.

**Note**

>Unlike stored instance properties, you must always give stored type properties a default value. This is because the type itself does not have an initializer that can assign a value to a stored type property at initialization time.
>
>Stored type properties are lazily initialized on their first access. They are guaranteed to be initialized only once, even when accessed by multiple threads simultaneously, and they do not need to be marked with the `lazy` modifier.

### Type Property Syntax

In C and Objective-C, you define static constants and variables associated with a type as *global* static variables. In Swift, however, type properties are written as part of the type’s definition, within the type’s outer curly braces, and each type property is explicitly scoped to the type it supports.

You define type properties with the `static` keyword. For computed type properties for class types, you can use the `class` keyword instead to allow subclasses to override the superclass’s implementation. The example below shows the syntax for stored and computed type properties:

```swift
struct SomeStructure {
    static var storedTypeProperty = "Some value."
    static var computedTypeProperty: Int {
        return 1
    }
}
enum SomeEnumeration {
    static var storedTypeProperty = "Some value."
    static var computedTypeProperty: Int {
        return 6
    }
}
class SomeClass {
    static var storedTypeProperty = "Some value."
    static var computedTypeProperty: Int {
        return 27
}
class var overrideableComputedTypeProperty: Int {
    return 107
    }
}
```

**Note**

>The computed type property examples above are for read-only computed type properties, but you can also define read-write computed type properties with the same syntax as for computed instance properties.

### Querying and Setting Type Properties

Type properties are queried and set with dot syntax, just like instance properties. However, type properties are queried and set on the *type*, not on an instance of that type. For example:

```swift
print(SomeStructure.storedTypeProperty)
// Prints "Some value."
SomeStructure.storedTypeProperty = "Another value."
print(SomeStructure.storedTypeProperty)
// Prints "Another value."
print(SomeEnumeration.computedTypeProperty)
// Prints "6"
print(SomeClass.computedTypeProperty)
// Prints "27"
```

The examples that follow use two stored type properties as part of a structure that models an audio level meter for a number of audio channels. Each channel has an integer audio level between `0` and `10` inclusive.

The figure below illustrates how two of these audio channels can be combined to model a stereo audio level meter. When a channel’s audio level is `0`, none of the lights for that channel are lit. When the audio level is `10`, all of the lights for that channel are lit. In this figure, the left channel has a current level of `9`, and the right channel has a current level of `7`:

![../_images/staticPropertiesVUMeter_2x.png](../_images/staticPropertiesVUMeter_2x.png)

The audio channels described above are represented by instances of the `AudioChannel` structure:

```swift
struct AudioChannel {
    static let thresholdLevel = 10
    static var maxInputLevelForAllChannels = 0
    var currentLevel: Int = 0 {
        didSet {
            if currentLevel > AudioChannel.thresholdLevel {
                // cap the new audio level to the threshold level
                currentLevel = AudioChannel.thresholdLevel
            }
            if currentLevel > AudioChannel.maxInputLevelForAllChannels {
                // store this as the new overall maximum input level
                AudioChannel.maxInputLevelForAllChannels = currentLevel
            }
        }
    }
}
```

The `AudioChannel` structure defines two stored type properties to support its functionality. The first, `thresholdLevel`, defines the maximum threshold value an audio level can take. This is a constant value of `10` for all `AudioChannel` instances. If an audio signal comes in with a higher value than `10`, it will be capped to this threshold value (as described below).

The second type property is a variable stored property called `maxInputLevelForAllChannels`. This keeps track of the maximum input value that has been received by *any* `AudioChannel` instance. It starts with an initial value of `0`.

The `AudioChannel` structure also defines a stored instance property called `currentLevel`, which represents the channel’s current audio level on a scale of `0` to `10`.

The `currentLevel` property has a `didSet` property observer to check the value of `currentLevel` whenever it is set. This observer performs two checks:

*   If the new value of `currentLevel` is greater than the allowed `thresholdLevel`, the property observer caps `currentLevel` to `thresholdLevel`.
    
*   If the new value of `currentLevel` (after any capping) is higher than any value previously received by *any* `AudioChannel` instance, the property observer stores the new `currentLevel` value in the `maxInputLevelForAllChannels` type property.
    

**Note**

>In the first of these two checks, the `didSet` observer sets `currentLevel` to a different value. This does not, however, cause the observer to be called again.

You can use the `AudioChannel` structure to create two new audio channels called `leftChannel` and `rightChannel`, to represent the audio levels of a stereo sound system:

```swift
var leftChannel = AudioChannel()
var rightChannel = AudioChannel()
```

If you set the `currentLevel` of the *left* channel to `7`, you can see that the `maxInputLevelForAllChannels` type property is updated to equal `7`:

```swift
leftChannel.currentLevel = 7
print(leftChannel.currentLevel)
// Prints "7"
print(AudioChannel.maxInputLevelForAllChannels)
// Prints "7"
```

If you try to set the `currentLevel` of the *right* channel to `11`, you can see that the right channel’s `currentLevel` property is capped to the maximum value of `10`, and the `maxInputLevelForAllChannels` type property is updated to equal `10`:

```swift
rightChannel.currentLevel = 11
print(rightChannel.currentLevel)
// Prints "10"
print(AudioChannel.maxInputLevelForAllChannels)
// Prints "10"
```
