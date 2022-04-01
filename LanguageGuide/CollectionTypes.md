Collection Types  

Tipos de Coleções (Collection Types)
===

Swift fornece três tipos primários de coleções, conhecidos como arrays, sets (conjuntos), e dicionários, para armazenar coleções de valores. Arrays são coleções ordenadas de valores. Sets são coleções não ordenadas de valores únicos. Dicionários são coleções não ordenadas com associações de key-value (chave-valor).

![../_images/CollectionTypes_intro_2x.png](../_images/CollectionTypes_intro_2x.png)

Arrays, sets, e dicionários em Swift são sempre claros sobre o tipo de valores e chaves que eles podem armazenar. Isto significa que voce não pode inserir um valor de um tipo errado em uma coleção por engano. Isso também significa que voce pode confiar sobre o tipo de valores que você irá receber de uma coleção.

**Nota**

> Tipos Array, set e dicionário de Swift são implementados como _coleções genéricas_.; Para mais informações sobre tipos de coleções, veja [Generics](Generics.md).

Mutabilidade de Coleções
-------------------------

Se você criar um array, um set, ou um dicionário, e o atribuiu a uma variável, a coleção que é criada será *mutável*. Isso significa que você pode alterar (ou *mudar*) a coleção depois de criá-la ao adicionar, remover ou alterar os itens contidos na coleção. Se você adicionar um array, um set, ou um dicionário a uma constante, a coleção será *imutável*, e o seu tamanho e conteúdo não podem ser alterados.

**Nota**

> É uma boa prática criar coleções imutáveis em todos os casos onde não será necessário alterá-la. Ao fazer isso, torna mais fácil para você entender seu código e permite que o compilador do Swift otimize a performance das coleções que você criou.

Arrays
------

Um *array* armazena valores do mesmo tipo em uma lista ordenada. O mesmo valor pode aparecer em um array multiplas vezes em posições diferentes.

**Nota**

> O tipo `Array` do Swift, é um tipo vinculado a classe `NSArray` da Foundation.
> 
> Para mais informações sobre `Array` com Foundation e Cocoa, veja [Bridging Between Array and NSArray](https://developer.apple.com/documentation/swift/array#2846730).

### Sintaxe Abreviada do Tipo Array

A notação completa do tipo do array em Swift é `Array<Element>`, onde `Element` é o tipo dos valores que o array é permitido armazenar. Você pode também escrever o tipo de um array de forma abreviada usando `[Element]`. Embora as duas formas funcionam de maneira identica, a forma abreviada é preferida e é usada em todo este guia quando se refere ao tipo de um array.

### Criando um Array Vazio

Você pode criar um array vazio de um certo tipo usando a sintaxe de inicialização: 

```swift
var someInts = [Int]()
print("someInts is of type [Int] with \(someInts.count) items.")
// Imprime "someInts is of type \[Int] with 0 items."
```
Note que o tipo da variável `someInts` é inferido como sendo `[Int]` a partir do tipo do inicializador.


Alternativamente, se o contexto já provê informação do tipo, tal como um argumento de função ou um variável ou constante já tipada, você pode instanciar um array vazio com um array literal vazio, escrevendo `[]` (um par de colchetes vazios):

```swift
someInts.append(3)
// someInts agora contem um valor do tipo Int
someInts = []
// someInts agora é um array vazio, mas ainda é do tipo [Int]. Ou seja, ele não está nil (equivalente a nulo), no entanto não possuem valores armazenados, e somente aceita valores do tipo Int em seu armazenamento.
```

### Criando um Array com Valor Padrão

O tipo `Array` do Swift também fornece um inicializador para riar um array de um certo tamanho, com todos os seus valores definidos para o mesmo valor padrão. Você pode passar para este inicializador o valor padrão o tipo apropriado ( chamado `repeating`): e o numero de vezes que o valor é repetido no novo array (chamado `count`):

```swift
var threeDoubles = Array(repeating: 0.0, count: 3)
// threeDoubles é do tipo [Double], e igual a [0.0, 0.0, 0.0]
```
### Criando um array por Adicionar Dois Arrays Juntos

Voce pode criar um novo array unindo dois outros já existentes arrays, com tipos compatíveis, usando o operador de adição (`+`). O tipo do novo array é inferido a partir do tipo dos dois arrays que você uniu.

```swift 
var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
// anotherThreeDoubles é do tipo [Double], e igual a [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles é inferido como [Double], e igual a [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]
```

#### Criando um Array com um Array Literal

Você também pode inicializar um array com um *array literal*, que é um jeito curto para escrever um ou mais valores como uma coleção array. Um array literal é escrito como uma lista de valores, separados por vírgula, e cercado por um par de colchetes:

> [value 1, value 2, value 3]

O exemplo abaixo criará um array chamado `shoopingList` para armazenar valores do tipo `String`:

```swift
var shoppingList: [String] = ["Eggs", "Milk"]
// shoppingList foi inicializado com dois items iniciais
```

A variável `shoppingList` é declarada como "um array de valores string", escrito como `[String]`. Portanto este array em particular possui especificamente um valor do tipo `String`, é permitido a ele armazenar somente valores `String`. Aqui, o array `shoppingList`é iniciado com dois valores `String` (`Eggs` e `Milk`), escrito como um array literal.

**Nota**

> O array `shoppingList` é declarado como uma variável (com a introdução de `var`) e não como uma constante (com a introdução de `let`) porque mais items são adicionados para a lista do shopping, como no exemplo abaixo.

Neste caso, o array literal contém dois valores `String`e nada mais.  Correspondendo ao tipo da declaração da variável `shoppingList` (um array que somente pode conter valores `String`), e então a atribuição do array literal é permitida como uma forma de inicializar `shoppingList` com dois items iniciais.

Agradeça a inferencia de tipo do Swift, você não precisa escrever o tipo do array se você não está inicializando com um array literal, contendo valores do mesmo tipo. A inicialização de `shoppingList`deverá ser escrita de forma curta: 

```swift
var shoppingList = ["Eggs", "Milk"]
```
Portanto, como todos os valores em um array literao são do mesmo tipo, Swift pode inferir que `[String]` [e o tipo correto para usar para a variável `shoppingList`.

### Acessar e modificar um Array

Acesse e modifique um array através de seus métodos e propriedades, ou usando sintaxe subscript.

Para saber o número de items de um array, verifique sua propriedade read-only (somente leitura) `count`: 

```swift
print("The shopping list contains \(shoppingList.count) items.")
// Imprimirá "The shopping list contains 2 items."
```
Use a propriedade Booleana `isEmpty` do array como um modo rápido para verificar se a propriedade `count` é igual a `0` (zero).

```swift
if shoppingList.isEmpty {
    print("The shopping list is empty.")
} else {
    print("The shopping list is not empty.")
}
// Imprimirá "The shopping list is not empty."
```
Voce pode adicionar um novo item no fim de um array, chamando o método `append(_:)` do array:

```swift
shoppingList.append("Flour")
// shoppingList agora contém 3 items, e now contains 3 items, e algém está fazendo panquecas
```
Alternativamente, acrescente um array de um ou mais items compatíveis com o operador de adição e atribuição (`+=`): 

```swift
shoppingList += ["Baking Powder"]
// shoppingList agora contém 4 items
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
// shoppingList agora contém 7 items
```
Recupere um valor de um array usando *sintaxe subscript*, passando o íncide do valor que você deseja recuperar, entre colchetes imediatamente depois do nome do array: 

```swift
var firstItem = shoppingList[0]
// firstItem é igual a "Eggs"
```

**Nota**
>O primeiro item em um array possui um índice de `0`, e não `1`. Arrays em Swift são sempre indexado por zero.

Você pode usar subscript para alterar um valor existente em um dado índice: 

```swift
shoppingList[0] = "Six eggs"
// O primeiro item na lista é agora "Six eggs" em vez de "Eggs"
```

Quando você usa subscript, o índice que você especificar precisa ser válido. Por exemplo, escrever `shoppingList[shoppingList.count] = "Salt"` tentando adicionar um item no final do array resultará em um erro em tempo de execução (runtime error).

Você também pode usar subscript para alterar um intervalo de valores de uma única vez, mesmo se o conjunto de valores na substituição possuem um tamanho diferente do intervalo daqueles que você está substituindo. O seguinte exemplo substitui `"Chocolate Spread"`, `"Cheese"`, e `"Butter"` com `"Bananas"` e `"Apples"`: 

```swift
shoppingList[4...6] = ["Bananas", "Apples"]
// shoppingList agora contém 6 items
```

Para inserir um item no array em um índice específico, use o método `insert(_:at:)` do array:

```swift
shoppingList.insert("Maple Syrup", at: 0)
// shoppingList agora contém 7 items
// "Maple Syrup" é agora o primeiro item na lista
```

Esta chamada ao método `insert (_: at:)` insere um novo item com um valor de `"Maple Syrup"` no início da lista de compras, indicado por um índice de `0`.

Similarmente, você remove um item do array com o método `remove(at:)`. Este método remove um item no índice específico, e retorna o item removido (Embora, você possa ignorar o valor retornado se você não precisa dele):

```swift
let mapleSyrup = shoppingList.remove(at: 0)
// o item que estava no índice 0 acabou de ser removido
// shoppingList agora contém 6 items, e não Maple Syrup
// a constante mapleSyrup é agora igual a string removida "Mapple Syrup"
```

**Nota**

>Se você tentar acessar ou modificar o valor em um índice que está além do limite do array, você irá disparar um erro em tempo de execução. Você pode verificar se um índice é válido antes de usá-lo comparando ele com o valor da propriedade `count`. O maior índice válido de um array é `count - 1` por que arrays são indexados a partir de zero, quando `count` é `0` (significa que o array está vazio), não sendo um índice válido.

Qualquer lacuna em um array é encerrado quando um item é removido, e então o valor no índice `0` é mais uma vez igual a `"Six eggs"`: 

```swift
firstItem = shoppingList[0]
// firstItem agora é igual a "Six eggs
```

Se você quer remover o item do final de um array, use o método `removeLast()` em vez do método `remove(at:)` para anular a necessidade de consultar a propriedade `count` do array. Assim como o método `remove(at:)`, `removeList()` retorna o item removido:

```swift
let apples = shoppingList.removeLast()
// o último item em um array acaba de ser removido
// shoppingList agora possui 5 items, e não apples
// a constante apples é agora igual a string removida "Apples"
```

### Iterando Sobre um Array

Você pode iterar sobre todo um conjunto de valores em um array com o laço de repetição `for`-`in`:


```swift
for item in shoppingList {
    print(item)
}
// Six eggs
// Milk
// Flour
// Baking Powder
// Bananas
```

Se você precisar do índice, do tipo Int, de cada item assim como o próprio valor, use o método `enumerated()` para iterar sobre o array. Para cada item no array, o método `enumarated()` retornará uma tupla composta de um inteiro e um item. O inteiro começará no zero e contará para cima para cada item; Se você enumerar sobre todo um array, esses inteiros corresponderão com os índices dos items. Você pode decompor a tupla em constantes temporárias ou variáveis como parte da iteração:  

```swift
for (index, value) in shoppingList.enumerated() {
    print("Item \\(index + 1): \\(value)")
}
// Item 1: Six eggs
// Item 2: Milk
// Item 3: Flour
// Item 4: Baking Powder
// Item 5: Bananas
```

Para mais informações sobre laço de repetição `for`\-`in`, veja [For-In Loops](ControlFlow.xhtml#ID121).

Sets
----

A *set* stores distinct values of the same type in a collection with no defined ordering. You can use a set instead of an array when the order of items is not important, or when you need to ensure that an item only appears once.

**Nota**

>Swift’s `Set` type is bridged to Foundation’s `NSSet` class.
>
>For more information about using `Set` with Foundation and Cocoa, see [Bridging Between Set and NSSet](https://developer.apple.com/documentation/swift/set#2845530).

### Hash Values for Set Types

A type must be *hashable* in order to be stored in a set—that is, the type must provide a way to compute a *hash value* for itself. A hash value is an `Int` value that is the same for all objects that compare equally, such that if `a == b`, it follows that `a.hashValue == b.hashValue`.

All of Swift’s basic types (such as `String`, `Int`, `Double`, and `Bool`) are hashable by default, and can be used as set value types or dictionary key types. Enumeration case values without associated values (as described in [Enumerations](Enumerations.md)) are also hashable by default.

**Nota**

>You can use your own custom types as set value types or dictionary key types by making them conform to the `Hashable` protocol from Swift’s standard library. Types that conform to the `Hashable` protocol must provide a gettable `Int` property called `hashValue`. The value returned by a type’s `hashValue` property is not required to be the same across different executions of the same program, or in different programs.
>
>Because the `Hashable` protocol conforms to `Equatable`, conforming types must also provide an implementation of the equals operator (`==`). The `Equatable` protocol requires any conforming implementation of `==` to be an equivalence relation. That is, an implementation of `==` must satisfy the following three conditions, for all values `a`, `b`, and `c`:
>
>*   `a == a` (Reflexivity)
>    
>*   `a == b` implies `b == a` (Symmetry)
>   
>*   `a == b && b == c` implies `a == c` (Transitivity)
>
>For more information about conforming to protocols, see [Protocols](Protocols.md).

### Set Type Syntax

The type of a Swift set is written as `Set<Element>`, where `Element` is the type that the set is allowed to store. Unlike arrays, sets do not have an equivalent shorthand form.

### Creating and Initializing an Empty Set

You can create an empty set of a certain type using initializer syntax:

```swift
var letters = Set<Character>()
print("letters is of type Set<Character> with \(letters.count) items.")
// Prints "letters is of type Set<Character> with 0 items."
```
**Nota**

>The type of the `letters` variable is inferred to be `Set<Character>`, from the type of the initializer.

Alternatively, if the context already provides type information, such as a function argument or an already typed variable or constant, you can create an empty set with an empty array literal:

```swift
letters.insert("a")
// letters now contains 1 value of type Character
letters = []
// letters is now an empty set, but is still of type Set<Character>
```

### Creating a Set with an Array Literal

You can also initialize a set with an array literal, as a shorthand way to write one or more values as a set collection.

The example below creates a set called `favoriteGenres` to store `String` values:

```swift
var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
// favoriteGenres has been initialized with three initial items
```

The `favoriteGenres` variable is declared as “a set of `String` values”, written as `Set<String>`. Because this particular set has specified a value type of `String`, it is *only* allowed to store `String` values. Here, the `favoriteGenres` set is initialized with three `String` values (`"Rock"`, `"Classical"`, and `"Hip hop"`), written within an array literal.

*Note*

>The `favoriteGenres` set is declared as a variable (with the `var` introducer) and not a constant (with the `let` introducer) because items are added and removed in the examples below.

A set type cannot be inferred from an array literal alone, so the type `Set` must be explicitly declared. However, because of Swift’s type inference, you don’t have to write the type of the set’s elements if you’re initializing it with an array literal that contains values of just one type. The initialization of `favoriteGenres` could have been written in a shorter form instead:
```swift
var favoriteGenres: Set = ["Rock", "Classical", "Hip hop"]
```

Because all values in the array literal are of the same type, Swift can infer that `Set<String>` is the correct type to use for the `favoriteGenres` variable.

### Accessing and Modifying a Set

You access and modify a set through its methods and properties.

To find out the number of items in a set, check its read-only `count` property:

```swift
print("I have \(favoriteGenres.count) favorite music genres.")
// Prints "I have 3 favorite music genres."
```

Use the Boolean `isEmpty` property as a shortcut for checking whether the `count` property is equal to `0`:

```swift
if favoriteGenres.isEmpty {
    print("As far as music goes, I'm not picky.")
} else {
    print("I have particular music preferences.")
}
// Prints "I have particular music preferences."
```

You can add a new item into a set by calling the set’s `insert(_:)` method:

```swift
favoriteGenres.insert("Jazz")
// favoriteGenres now contains 4 items
```

You can remove an item from a set by calling the set’s `remove(_:)` method, which removes the item if it’s a member of the set, and returns the removed value, or returns `nil` if the set did not contain it. Alternatively, all items in a set can be removed with its `removeAll()` method.

```swift
if let removedGenre = favoriteGenres.remove("Rock") {
    print("\(removedGenre)? I'm over it.")
} else {
    print("I never much cared for that.")
}
// Prints "Rock? I'm over it."
```

To check whether a set contains a particular item, use the `contains(_:)` method.

```swift
if favoriteGenres.contains("Funk") {
    print("I get up on the good foot.")
} else {
    print("It's too funky in here.")
}
// Prints "It's too funky in here."
```

### Iterating Over a Set

You can iterate over the values in a set with a `for`\-`in` loop.

```swift
for genre in favoriteGenres {
    print("\(genre)")
}
// Classical
// Jazz
// Hip hop
```

For more about the `for`-`in` loop, see [For-In Loops](ControlFlow.md#for-in-loops).

Swift’s `Set` type does not have a defined ordering. To iterate over the values of a set in a specific order, use the `sorted()` method, which returns the set’s elements as an array sorted using the `<` operator.

```swift
for genre in favoriteGenres.sorted() {
    print("\(genre)")
}
// Classical
// Hip hop
// Jazz
```

Performing Set Operations
-------------------------

You can efficiently perform fundamental set operations, such as combining two sets together, determining which values two sets have in common, or determining whether two sets contain all, some, or none of the same values.

### Fundamental Set Operations

The illustration below depicts two sets—`a` and `b`—with the results of various set operations represented by the shaded regions.

![../_images/setVennDiagram_2x.png](../_images/setVennDiagram_2x.png)

*   Use the `intersection(_:)` method to create a new set with only the values common to both sets.
    
*   Use the `symmetricDifference(_:)` method to create a new set with values in either set, but not both.
    
*   Use the `union(_:)` method to create a new set with all of the values in both sets.
    
*   Use the `subtracting(_:)` method to create a new set with values not in the specified set.
    
```swift
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]
```
### Set Membership and Equality

The illustration below depicts three sets—`a`, `b` and `c`—with overlapping regions representing elements shared among sets. Set `a` is a *superset* of set `b`, because `a` contains all elements in `b`. Conversely, set `b` is a *subset* of set `a`, because all elements in `b` are also contained by `a`. Set `b` and set `c` are *disjoint* with one another, because they share no elements in common.

![../_images/setEulerDiagram_2x.png](../_images/setEulerDiagram_2x.png)

*   Use the “is equal” operator (`==`) to determine whether two sets contain all of the same values.
    
*   Use the `isSubset(of:)` method to determine whether all of the values of a set are contained in the specified set.
    
*   Use the `isSuperset(of:)` method to determine whether a set contains all of the values in a specified set.
    
*   Use the `isStrictSubset(of:)` or `isStrictSuperset(of:)` methods to determine whether a set is a subset or superset, but not equal to, a specified set.
    
*   Use the `isDisjoint(with:)` method to determine whether two sets have no values in common.
    
```swift
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```
Dictionaries
------------

A *dictionary* stores associations between keys of the same type and values of the same type in a collection with no defined ordering. Each value is associated with a unique *key*, which acts as an identifier for that value within the dictionary. Unlike items in an array, items in a dictionary do not have a specified order. You use a dictionary when you need to look up values based on their identifier, in much the same way that a real-world dictionary is used to look up the definition for a particular word.

**Nota**

>Swift’s `Dictionary` type is bridged to Foundation’s `NSDictionary` class.
>
>For more information about using `Dictionary` with Foundation and Cocoa, see [Bridging Between Dictionary and NSDictionary](https://developer.apple.com/documentation/swift/dictionary#2846239).

### Dictionary Type Shorthand Syntax

The type of a Swift dictionary is written in full as `Dictionary<Key, Value>`, where `Key` is the type of value that can be used as a dictionary key, and `Value` is the type of value that the dictionary stores for those keys.

**Nota**

>A dictionary `Key` type must conform to the `Hashable` protocol, like a set’s value type.

You can also write the type of a dictionary in shorthand form as `[Key: Value]`. Although the two forms are functionally identical, the shorthand form is preferred and is used throughout this guide when referring to the type of a dictionary.

### Creating an Empty Dictionary

As with arrays, you can create an empty `Dictionary` of a certain type by using initializer syntax:

```swift
var namesOfIntegers = [Int: String]()
// namesOfIntegers is an empty \[Int: String\] dictionary
```

This example creates an empty dictionary of type `[Int: String]` to store human-readable names of integer values. Its keys are of type `Int`, and its values are of type `String`.

If the context already provides type information, you can create an empty dictionary with an empty dictionary literal, which is written as `[:]` (a colon inside a pair of square brackets):

```swift
namesOfIntegers[16] = "sixteen"
// namesOfIntegers now contains 1 key-value pair
namesOfIntegers = [:]
// namesOfIntegers is once again an empty dictionary of type [Int: String]
```

### Creating a Dictionary with a Dictionary Literal

You can also initialize a dictionary with a *dictionary literal*, which has a similar syntax to the array literal seen earlier. A dictionary literal is a shorthand way to write one or more key-value pairs as a `Dictionary` collection.

A *key-value pair* is a combination of a key and a value. In a dictionary literal, the key and value in each key-value pair are separated by a colon. The key-value pairs are written as a list, separated by commas, surrounded by a pair of square brackets:

>[key 1: value 1, key 2: value 2, key 3: value 3]

The example below creates a dictionary to store the names of international airports. In this dictionary, the keys are three-letter International Air Transport Association codes, and the values are airport names:

```swift
var airports: [String: String] = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
```

The `airports` dictionary is declared as having a type of `[String: String]`, which means “a `Dictionary` whose keys are of type `String`, and whose values are also of type `String`”.

**Nota**

>The `airports` dictionary is declared as a variable (with the `var` introducer), and not a constant (with the `let` introducer), because more airports are added to the dictionary in the examples below.

The `airports` dictionary is initialized with a dictionary literal containing two key-value pairs. The first pair has a key of `"YYZ"` and a value of `"Toronto Pearson"`. The second pair has a key of `"DUB"` and a value of `"Dublin"`.

This dictionary literal contains two `String: String` pairs. This key-value type matches the type of the `airports` variable declaration (a dictionary with only `String` keys, and only `String` values), and so the assignment of the dictionary literal is permitted as a way to initialize the `airports` dictionary with two initial items.

As with arrays, you don’t have to write the type of the dictionary if you’re initializing it with a dictionary literal whose keys and values have consistent types. The initialization of `airports` could have been written in a shorter form instead:

```swift
var airports = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
```

Because all keys in the literal are of the same type as each other, and likewise all values are of the same type as each other, Swift can infer that `[String: String]` is the correct type to use for the `airports` dictionary.

### Accessing and Modifying a Dictionary

You access and modify a dictionary through its methods and properties, or by using subscript syntax.

As with an array, you find out the number of items in a `Dictionary` by checking its read-only `count` property:

```swift
print("The airports dictionary contains \(airports.count) items.")
// Prints "The airports dictionary contains 2 items."
```

Use the Boolean `isEmpty` property as a shortcut for checking whether the `count` property is equal to `0`:

```swift
if airports.isEmpty {
    print("The airports dictionary is empty.")
} else {
    print("The airports dictionary is not empty.")
}
// Prints "The airports dictionary is not empty."
```

You can add a new item to a dictionary with subscript syntax. Use a new key of the appropriate type as the subscript index, and assign a new value of the appropriate type:

```swift
airports["LHR"] = "London"
// the airports dictionary now contains 3 items
```

You can also use subscript syntax to change the value associated with a particular key:

```swift
airports["LHR"] = "London Heathrow"
// the value for "LHR" has been changed to "London Heathrow"
```

As an alternative to subscripting, use a dictionary’s `updateValue(_:forKey:)` method to set or update the value for a particular key. Like the subscript examples above, the `updateValue(_:forKey:)` method sets a value for a key if none exists, or updates the value if that key already exists. Unlike a subscript, however, the `updateValue(_:forKey:)` method returns the *old* value after performing an update. This enables you to check whether or not an update took place.

The `updateValue(_:forKey:)` method returns an optional value of the dictionary’s value type. For a dictionary that stores `String` values, for example, the method returns a value of type `String?`, or “optional `String`”. This optional value contains the old value for that key if one existed before the update, or `nil` if no value existed:

```swift
if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
    print("The old value for DUB was \(oldValue).")
}
// Prints "The old value for DUB was Dublin."
```

You can also use subscript syntax to retrieve a value from the dictionary for a particular key. Because it is possible to request a key for which no value exists, a dictionary’s subscript returns an optional value of the dictionary’s value type. If the dictionary contains a value for the requested key, the subscript returns an optional value containing the existing value for that key. Otherwise, the subscript returns `nil`:

```swift
if let airportName = airports["DUB"] {
    print("The name of the airport is \(airportName).")
} else {
    print("That airport is not in the airports dictionary.")
}
// Prints "The name of the airport is Dublin Airport."
```

You can use subscript syntax to remove a key-value pair from a dictionary by assigning a value of `nil` for that key:

```swift
airports["APL"] = "Apple International"
// "Apple International" is not the real airport for APL, so delete it
airports["APL"] = nil
// APL has now been removed from the dictionary
```

Alternatively, remove a key-value pair from a dictionary with the `removeValue(forKey:)` method. This method removes the key-value pair if it exists and returns the removed value, or returns `nil` if no value existed:

```swift
if let removedValue = airports.removeValue(forKey: "DUB") {
    print("The removed airport's name is \(removedValue).")
} else {
    print("The airports dictionary does not contain a value for DUB.")
}
// Prints "The removed airport's name is Dublin Airport."
```

### Iterating Over a Dictionary

You can iterate over the key-value pairs in a dictionary with a `for`-`in` loop. Each item in the dictionary is returned as a `(key, value)` tuple, and you can decompose the tuple’s members into temporary constants or variables as part of the iteration:

```swift
for (airportCode, airportName) in airports {
    print("\(airportCode): \(airportName)")
}
// LHR: London Heathrow
// YYZ: Toronto Pearson
```
For more about the `for`-`in` loop, see [For-In Loops](ControlFlow.md#for-in-loops).

You can also retrieve an iterable collection of a dictionary’s keys or values by accessing its `keys` and `values` properties:

```swift
for airportCode in airports.keys {
print("Airport code: \(airportCode)")
}
// Airport code: LHR
// Airport code: YYZ

for airportName in airports.values {
print("Airport name: \(airportName)")
}
// Airport name: London Heathrow
// Airport name: Toronto Pearson
```

If you need to use a dictionary’s keys or values with an API that takes an `Array` instance, initialize a new array with the `keys` or `values` property:

```swift
let airportCodes = [String](airports.keys)
// airportCodes is ["LHR", "YYZ"]

let airportNames = [String](airports.values)
// airportNames is ["London Heathrow", "Toronto Pearson"]
```

Swift’s `Dictionary` type does not have a defined ordering. To iterate over the keys or values of a dictionary in a specific order, use the `sorted()` method on its `keys` or `values` property.