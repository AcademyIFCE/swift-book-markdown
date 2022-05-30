Strings e Caracteres
======================
Uma _string_ é uma sequência de caracteres, como por exemplo: `"hello, world"` ou `"albatross"`. Strings no Swift são representadas pelo tipo `String`. Os conteúdos de uma `String` podem ser acessados de várias maneiras, inclusive como uma lista de valores do tipo `Character`.

Os tipos `String` e `Character` do Swift fornecem uma maneira rápida, compatível com Unicode de trabalhar com textos no seu código. A sintaxe para criação e manipulação de uma _string_ é descomplicada e legível, com uma sintaxe literal de _string_ que é similar à do C. Concatenação de _strings_ é tão simples quanto combinar duas _strings_ com o operador `+`, e a mutabilidade de uma _string_ é gerenciada pela escolha entre uma constante ou uma variável, assim como qualquer outro valor em Swift. Você também pode usar _strings_ para a inserção de constantes, variáveis, literais e expressões formando _strings_ maiores, em um processo conhecido como interpolação de _strings_. Isso facilita a criação de valores de _string_ personalizados para exibição, armazenamento e _prints_.

Apesar da simplicidade da sintaxe, o tipo `String` do Swift é uma implementação rápida e moderna de _string_. Toda _string_ é composta por caracteres Unicode de codificação independente e fornece suporte para acessar esses caracteres em várias representações Unicode.

**Nota**

> O tipo `String` do Swift é ligado com a classe `NSString` do Foundation. Foundation também estende `String` para expor métodos definidos pelo `NSString`. Isso significa, se você importar o Foundation, poderá acessar esses métodos de `NSString` com `String` sem "casting".
Para mais informações sobre o uso de `String` com Foundation e Cocoa, veja [Bridging Between String and NSString](https://developer.apple.com/documentation/swift/string#2919514).

Literais de String
---------------

Você pode incluir valores `String` predefinidos em seu código como _literais de string_. Um literal de string é uma sequência de caracteres entre aspas duplas (`"`).

Use um literal de string como valor inicial para uma constante ou variável:

```swift
let someString = "Some string literal value"
```

Note que Swift infere um tipo de `String` para a constante `someString` porque ela é inicializada com um valor literal de string.

### Literais de String Multilinha

Se você precisar de uma string que se estenda por várias linhas, use um literal de string multilinha—uma sequência de caracteres entre três aspas duplas:

```swift
let quotation = """
The White Rabbit put on his spectacles. "Where shall I
      begin,
please your Majesty?" he asked.

"Begin at the beginning," the King said gravely, "and go on
till you come to the end; then stop."
"""
```

Um literal de string multilinha inclui todas as linhas entre as aspas de abertura e fechamento. A string começa na primeira linha após as aspas de abertura (`"""`) e termina na linha antes das aspas de fechamento, o que significa que nenhuma das strings abaixo começa ou termina com uma quebra de linha:

```swift
let singleLineString = "These are the same."
let multilineString = """
These are the same.
"""
```

Quando seu código-fonte inclui uma quebra de linha dentro de um literal de string multilinha, essa quebra de linha também aparece no valor da string. Se você quer usar quebras de linha para tornar seu código-fonte mais fácil de ler, mas não quer que elas façam parte do valor da string, escreva uma barra invertida (`\`) no final dessas linhas:

```swift  
let softWrappedQuotation = """
The White Rabbit put on his spectacles.  "Where shall I
      begin, \
please your Majesty?" he asked.

"Begin at the beginning," the King
      said gravely, "and go on \
till you come to the end; then
      stop."
"""
```

Para fazer uma string literal multilinha que começa ou termina com uma quebra de linha, escreva uma linha em branco como a primeira ou a última linha. Por exemplo:

```swift  
let lineBreaks = """

This string starts with a line break.
It also ends with a line break.

"""
```

Uma string multilinha pode ser identada para corresponder ao código ao redor. O espaço em branco antes das aspas de fechamento (`"""`) informa qual espaço deve ser ignorado antes de todas as outras linhas. No entanto, se você escrever um espaço em branco no início de uma linha além do que está antes das aspas de fechamento, esse espaço em branco _é_ incluído.

![../_images/multilineStringWhitespace_2x.png](../_images/multilineStringWhitespace_2x.png)

No exemplo acima, embora todo o literal de string multilinha esteja identado, a primeira e a última linhas não começam com espaço em branco. A linha do meio tem mais identação do que as aspas de fechamento, portanto, ela começa com esse recuo extra de quatro espaços.

### Caracteres Especiais em Literais de String

Literais de string podem incluir os seguintes caracteres especiais:

* Os caracteres especiais de escape `\0` (caractere nulo), `\\` (barra invertida), `\t` (tab horizontal), `\n` (quebra de linha), `\r` (carriage return), `\"` (aspas duplas) e `\'` (aspas simples)

* Um valor escalar Unicode arbitrário, escrito como `\u{`_n_`}`, onde _n_ é um número hexadecimal de 1–8 dígitos (Unicode é discutido em [Unicode](#ID293) abaixo)


O código a seguir mostra quatro exemplos desses caracteres especiais. A constante `wiseWords` contém duas aspas duplas escapadas. As constantes `dollarSign`,` blackHeart` e `sparklingHeart` demonstram o formato escalar Unicode:

```swift  
let wiseWords = "\"Imagination is more important than knowledge\" - Einstein"
// "Imagination is more important than knowledge" - Einstein
let dollarSign = "\u{24}" // $, Unicode scalar U+0024
let blackHeart = "\u{2665}" // ♥, Unicode scalar U+2665
let sparklingHeart = "\u{1F496}" // 💖, Unicode scalar U+1F496
```
Como os literais de string multilinha usam três aspas duplas em vez de apenas uma, você pode inserir aspa dupla (`"`) dentro da string sem escapá-la. Para incluir o texto `"""` em uma string multilinha, escape pelo menos uma das aspas. Por exemplo:

```swift  
let threeDoubleQuotationMarks = """
Escaping the first quotation mark \"""
Escaping all three quotation marks \"\"\"
"""
```
### Delimitadores Estendidos de String

Você pode colocar um literal de string dentro de _delimitadores estendidos_ para incluir caracteres especiais em uma string sem invocar seu efeito. Você coloca sua string entre aspas (`"`) e envolve-a com sinais numéricos (`#`). Por exemplo, imprimir a string literal `#"Linha 1\nLinha 2"#` imprime a sequência de caracteres da quebra de linha (`\n`) em vez de imprimir a string em duas linhas.

Se você precisar dos efeitos especiais de um caractere em uma literal de string, adicione sinais numéricos depois do caractere de escape (`\`), de forma que a quantidade seja a mesma que a de dentro da string. Por exemplo, se sua string é `#"Linha 1\nLinha 2"#` e você deseja quebrar a linha, você pode usar `#"Linha 1\#nLinha 2"#` em seu lugar. Da mesma forma, `###"Line1\###nLine2"###` também quebra a linha.

Literais de string criadas usando delimitadores estendidos também podem ser literais de string multilinha. Você pode usar delimitadores estendidos para incluir o texto `"""` em uma string multilinha, substituindo o comportamento padrão que termina o literal. Por exemplo:

```swift  
let threeMoreDoubleQuotationMarks = #"""
Here are three more double quotes: """
"""#
```
Inicializando uma String Vazia
----------------------------

Para criar uma `String` vazia como ponto de partida para construir uma string mais longa, atribua um literal de string vazia a uma variável ou inicialize uma nova instância de `String` com a sintaxe do inicializador:

```swift  
var emptyString = ""        // literal de string vazia
var anotherEmptyString = String()     // sintaxe do inicializador
// essas duas strings estão vazias e são equivalentes uma à outra
```
Descubra se um valor `String` está vazio verificando sua propriedade booleana `isEmpty`:

```swift  
if emptyString.isEmpty {
  print("Nada para ver aqui")
}
// Prints "Nada para ver aqui"
```

Mutabilidade da String
-----------------

Você indica se uma determinada `String` pode ser modificada (ou _mutada_) atribuindo-a a uma variável (nesse caso, ela pode ser modificada) ou a uma constante (neste caso, não pode ser modificada):

```swift
var variableString = "Horse"
variableString += " and carriage"
// variableString agora é "Horse and carriage"

let constantString = "Highlander"
constantString += " and another Highlander"
// isso reporta um erro em tempo de compilação - uma string constante não pode ser modificada
```

**Nota**

> Esta abordagem é diferente da mutação de string em Objective-C e Cocoa, onde você escolhe entre duas classes (`NSString` e `NSMutableString`) para indicar se uma string pode sofrer mutação.

Strings São *Value Types*
-----------------------

O tipo `String` é um _value type_. Se você criar um novo valor `String`, esse valor `String` será _copiado_ quando for passado para uma função ou método, ou quando for atribuído a uma constante ou variável. Em cada caso, uma nova cópia do valor `String` existente é criada e a nova cópia é passada ou atribuída, não a versão original. Os *value types*  são descritos em [Struturas e Enumerações são Value Types](ClassesAndStructures.xhtml#ID88).

O comportamento *copy-by-default* da `String` no Swift garante que quando uma função ou método passa um valor `String`, fica claro que você possui aquele valor `String` exato, independentemente de onde ele veio. Você pode ter certeza de que a string passada não será modificada, a menos que você mesmo a modifique.

Nos bastidores, o compilador do Swift otimiza o uso de string para que a cópia real ocorra apenas quando for absolutamente necessário. Isso significa que você sempre obtém um ótimo desempenho ao trabalhar com strings como *value types*.

Trabalhando com Caracteres
-----------------------

Você pode acessar os valores individuais do tipo `Character` de um tipo `String` iterando sobre a string com um laço `for`\-`in`:

```swift  
for character in "Dog!🐶" {
print(character)
}
// D
// o
// g
// !
// 🐶
```
O laço `for`\-`in` é descrito em [For-In Loops](LanguageGuide/ControlFlow.md#for-in-loops).

Como alternativa, você pode criar uma constante ou variável `Character` independente a partir de um literal de string de caractere único, fornecendo uma anotação do tipo `Character`:

```swift  
let exclamationMark: Character = "!"
```
Os valores `String` podem ser construídos passando uma _array_ de valores `Character` como um argumento para seu inicializador:

```swift  
let catCharacters: [Character] = \["C", "a", "t", "!", "🐱"]
let catString = String(catCharacters)
print(catString)
// Prints "Cat!🐱"
```

Concatenando Strings e Caracteres
------------------------------------

Valores `String` podem ser somados (ou _concatenados_) com o operador de adição (`+`) para criar um novo valor `String`:

```swift  
let string1 = "hello"
let string2 = " there"
var welcome = string1 + string2
// welcome now equals "hello there"
```
Você também pode acrescentar um valor `String` à uma variável `String` existente com o operador de atribuição de adição (`+=`):

```swift  
var instruction = "look over"
instruction += string2
// instruction now equals "look over there"
```
Você pode adicionar um valor `Character` à uma variável `String` com o método `append()` do tipo `String`:

```swift  
let exclamationMark: Character = "!"
welcome.append(exclamationMark)
// welcome now equals "hello there!"
```

**Nota**

>Você não pode anexar um `String` ou` Character` a uma variável `Character` existente, porque um valor `Character` deve conter apenas um único caractere.

Se você estiver usando literais de string de múltiplas linhas para construir as linhas de uma string mais longa, você quer que cada linha da string termine com uma quebra de linha, incluindo a última linha. Por exemplo:

```swift  
let badStart = """
one
two
"""
let end = """
three
"""
print(badStart + end)
// Prints two lines:
// one
// twothree

let goodStart = """
one
two

"""
print(goodStart + end)
// Prints three lines:
// one
// two
// three
```

No código acima, concatenar `badStart` com` end` produz uma string de duas linhas, que não é o resultado desejado. Como a última linha de `badStart` não termina com uma quebra de linha, essa linha é combinada com a primeira linha de` end`. Em contraste, ambas as linhas de `goodStart` terminam com uma quebra de linha, então, quando combinado com `end`, o resultado tem três linhas, como esperado.

Interpolação de String
--------------------

_Interpolação de string_ é uma forma de construir uma novo valor de `String` com uma mistura de constantes, variáveis, literais, e expressões colocando seus valores dentro de um literal de string. Você pode usar interpolação em literais de string de uma única linha ou multilinha. Cada item que você insere no literal de string é envolvido em um par de parênteses, precedido por uma barra invertida (`\`):

```swift  
let multiplier = 3
let message = "\(multiplier) times 2.5 is \(Double(multiplier) * 2.5)"
// message is "3 times 2.5 is 7.5"
```

No exemplo acima, o valor de `multiplier` é inserido em um literal de string como `\(multiplier)`. Essa lacuna é substituída pelo real valor de `multiplier` quando a interpolação de string é avaliada para criar uma string de fato.

O valor de `multiplier` também é parte de uma expressão maior posterior na string. Essa expressão calcula o valor de `Double(multiplier) * 2.5` e insere o resultado (`7.5`) na string. Nesse caso, a expressão é escrita como `\(Double(multiplier) * 2.5)` quando é incluída no literal de string.

Você pode usar delimitadores extendidos de strings para criar strings contendo caracteres que seriam de outra forma tratados como uma interpolação de string. Por exemplo:

```swift  
print(#"Write an interpolated string in Swift using \(multiplier)."#)
// Imprime "Write an interpolated string in Swift using \(multiplier)."
```

Para usar interpolação de string dentro de uma string que usa delimitadores extendidos, iguale o número de `#` antes da barra invertida ao número de `#` no começo e final da string. Por exemplo:

```swift  
print(#"6 times 7 is \#(6 * 7)."#)
// Imprime "6 times 7 is 42."
```

**Nota**

> A expressão que você escreve dentro de uma string interpolada não pode conter uma barra invertida(`\`), uma quebra ou avanço de linha sem escaping. De qualquer forma, elas podem conter outros literais de string.

Unicode
-------

_Unicode_ is an international standard for encoding, representing, and processing text in different writing systems. It enables you to represent almost any character from any language in a standardized form, and to read and write those characters to and from an external source such as a text file or web page. Swift’s `String` and `Character` types are fully Unicode-compliant, as described in this section.

### Unicode Scalar Values

Behind the scenes, Swift’s native `String` type is built from _Unicode scalar values_. A Unicode scalar value is a unique 21-bit number for a character or modifier, such as `U+0061` for `LATIN SMALL LETTER A` (`"a"`), or `U+1F425` for `FRONT-FACING BABY CHICK` (`"🐥"`).

Note that not all 21-bit Unicode scalar values are assigned to a character—some scalars are reserved for future assignment or for use in UTF-16 encoding. Scalar values that have been assigned to a character typically also have a name, such as `LATIN SMALL LETTER A` and `FRONT-FACING BABY CHICK` in the examples above.

### Extended Grapheme Clusters

Every instance of Swift’s `Character` type represents a single _extended grapheme cluster_. An extended grapheme cluster is a sequence of one or more Unicode scalars that (when combined) produce a single human-readable character.

Here’s an example. The letter `é` can be represented as the single Unicode scalar `é` (`LATIN SMALL LETTER E WITH ACUTE`, or `U+00E9`). However, the same letter can also be represented as a _pair_ of scalars—a standard letter `e` (`LATIN SMALL LETTER E`, or `U+0065`), followed by the `COMBINING ACUTE ACCENT` scalar (`U+0301`). The `COMBINING ACUTE ACCENT` scalar is graphically applied to the scalar that precedes it, turning an `e` into an `é` when it’s rendered by a Unicode-aware text-rendering system.

In both cases, the letter `é` is represented as a single Swift `Character` value that represents an extended grapheme cluster. In the first case, the cluster contains a single scalar; in the second case, it’s a cluster of two scalars:

```swift  
let eAcute: Character = "\u{E9}"    // é
let combinedEAcute: Character = "\u{65}\u{301}"      // e followed by ́
// eAcute is é, combinedEAcute is é
```
Extended grapheme clusters are a flexible way to represent many complex script characters as a single `Character` value. For example, Hangul syllables from the Korean alphabet can be represented as either a precomposed or decomposed sequence. Both of these representations qualify as a single `Character` value in Swift:

```swift
let precomposed: Character = "\u{D55C}"   // 한
let decomposed: Character = "\u{1112}\u{1161}\u{11AB}"    // ᄒ, ᅡ, ᆫ
// precomposed is 한, decomposed is 한
```

Extended grapheme clusters enable scalars for enclosing marks (such as `COMBINING ENCLOSING CIRCLE`, or `U+20DD`) to enclose other Unicode scalars as part of a single `Character` value:


```swift
let enclosedEAcute: Character = "\u{E9}\u{20DD}"
// enclosedEAcute is é⃝
```

Unicode scalars for regional indicator symbols can be combined in pairs to make a single `Character` value, such as this combination of `REGIONAL INDICATOR SYMBOL LETTER U` (`U+1F1FA`) and `REGIONAL INDICATOR SYMBOL LETTER S` (`U+1F1F8`):

```swift
let regionalIndicatorForUS: Character = "\u{1F1FA}\u{1F1F8}"
// regionalIndicatorForUS is 🇺🇸
```

Counting Characters
-------------------

To retrieve a count of the `Character` values in a string, use the `count` property of the string:

```swift
let unusualMenagerie = "Koala 🐨, Snail 🐌, Penguin 🐧, Dromedary 🐪"
print("unusualMenagerie has \(unusualMenagerie.count) characters")
// Prints "unusualMenagerie has 40 characters"
```

Note that Swift’s use of extended grapheme clusters for `Character` values means that string concatenation and modification may not always affect a string’s character count.

For example, if you initialize a new string with the four-character word `cafe`, and then append a `COMBINING ACUTE ACCENT` (`U+0301`) to the end of the string, the resulting string will still have a character count of `4`, with a fourth character of `é`, not `e`:

```swift
var word = "cafe"
print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in cafe is 4"

word += "\u{301}" // COMBINING ACUTE ACCENT, U+0301

print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in café is 4"
```

**Note**

>Extended grapheme clusters can be composed of multiple Unicode scalars. This means that different characters—and different representations of the same character—can require different amounts of memory to store. Because of this, characters in Swift don’t each take up the same amount of memory within a string’s representation. As a result, the number of characters in a string can’t be calculated without iterating through the string to determine its extended grapheme cluster boundaries. If you are working with particularly long string values, be aware that the `count` property must iterate over the Unicode scalars in the entire string in order to determine the characters for that string.
<br /> The count of the characters returned by the `count` property isn’t always the same as the `length` property of an `NSString` that contains the same characters. The length of an `NSString` is based on the number of 16-bit code units within the string’s UTF-16 representation and not the number of Unicode extended grapheme clusters within the string.

Accessing and Modifying a String
--------------------------------

You access and modify a string through its methods and properties, or by using subscript syntax.

### String Indices

Each `String` value has an associated _index type_, `String.Index`, which corresponds to the position of each `Character` in the string.

As mentioned above, different characters can require different amounts of memory to store, so in order to determine which `Character` is at a particular position, you must iterate over each Unicode scalar from the start or end of that `String`. For this reason, Swift strings can’t be indexed by integer values.

Use the `startIndex` property to access the position of the first `Character` of a `String`. The `endIndex` property is the position after the last character in a `String`. As a result, the `endIndex` property isn’t a valid argument to a string’s subscript. If a `String` is empty, `startIndex` and `endIndex` are equal.

You access the indices before and after a given index using the `index(before:)` and `index(after:)` methods of `String`. To access an index farther away from the given index, you can use the `index(_:offsetBy:)` method instead of calling one of these methods multiple times.

You can use subscript syntax to access the `Character` at a particular `String` index.

```swift
let greeting = "Guten Tag!"
greeting[greeting.startIndex]
// G
greeting[greeting.index(before: greeting.endIndex)]
// !
greeting[greeting.index(after: greeting.startIndex)]
// u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index]
// a
```

Attempting to access an index outside of a string’s range or a `Character` at an index outside of a string’s range will trigger a runtime error.

```swift
greeting[greeting.endIndex]    // Error
greeting.index(after: greeting.endIndex)     // Error
```

Use the `indices` property to access all of the indices of individual characters in a string.

```swift
for index in greeting.indices {
  print("\(greeting[index]) ", terminator: "")
}
// Prints "G u t e n T a g ! "
```

**Note**

>You can use the `startIndex` and `endIndex` properties and the `index(before:)`, `index(after:)`, and `index(_:offsetBy:)` methods on any type that conforms to the `Collection` protocol. This includes `String`, as shown here, as well as collection types such as `Array`, `Dictionary`, and `Set`.

### Inserting and Removing

To insert a single character into a string at a specified index, use the `insert(_:at:)` method, and to insert the contents of another string at a specified index, use the `insert(contentsOf:at:)` method.

```swift
var welcome = "hello"
welcome.insert("!", at: welcome.endIndex)
// welcome now equals "hello!"

welcome.insert(contentsOf: " there", at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there!"
```

To remove a single character from a string at a specified index, use the `remove(at:)` method, and to remove a substring at a specified range, use the `removeSubrange(_:)` method:

```swift
welcome.remove(at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there"

let range = welcome.index(welcome.endIndex, offsetBy: \-6)..<welcome.endIndex
welcome.removeSubrange(range)
// welcome now equals "hello"
```

**Note**

>You can use the `insert(_:at:)`, `insert(contentsOf:at:)`, `remove(at:)`, and `removeSubrange(_:)` methods on any type that conforms to the `RangeReplaceableCollection` protocol. This includes `String`, as shown here, as well as collection types such as `Array`, `Dictionary`, and `Set`.

Substrings
----------

When you get a substring from a string—for example, using a subscript or a method like `prefix(_:)`—the result is an instance of [`Substring`](https://developer.apple.com/documentation/swift/substring), not another string. Substrings in Swift have most of the same methods as strings, which means you can work with substrings the same way you work with strings. However, unlike strings, you use substrings for only a short amount of time while performing actions on a string. When you’re ready to store the result for a longer time, you convert the substring to an instance of `String`. For example:

```swift
let greeting = "Hello, world!"
let index = greeting.firstIndex(of: ",") ?? greeting.endIndex
let beginning = greeting[..<index]
// beginning is "Hello"

// Convert the result to a String for long-term storage.
let newString = String(beginning)
```

Like strings, each substring has a region of memory where the characters that make up the substring are stored. The difference between strings and substrings is that, as a performance optimization, a substring can reuse part of the memory that’s used to store the original string, or part of the memory that’s used to store another substring. (Strings have a similar optimization, but if two strings share memory, they are equal.) This performance optimization means you don’t have to pay the performance cost of copying memory until you modify either the string or substring. As mentioned above, substrings aren’t suitable for long-term storage—because they reuse the storage of the original string, the entire original string must be kept in memory as long as any of its substrings are being used.

In the example above, `greeting` is a string, which means it has a region of memory where the characters that make up the string are stored. Because `beginning` is a substring of `greeting`, it reuses the memory that `greeting` uses. In contrast, `newString` is a string—when it’s created from the substring, it has its own storage. The figure below shows these relationships:

![../_images/stringSubstring_2x.png](../_images/stringSubstring_2x.png)

**Note**

>Both `String` and `Substring` conform to the [`StringProtocol`]( developer.apple.com/documentation/swift/stringprotocol) protocol, which means it’s often convenient for string-manipulation functions to accept a `StringProtocol` value. You can call such functions with either a `String` or `Substring` value.

Comparing Strings
-----------------

Swift provides three ways to compare textual values: string and character equality, prefix equality, and suffix equality.

### String and Character Equality

String and character equality is checked with the “equal to” operator (`==`) and the “not equal to” operator (`!=`), as described in [Comparison Operators](BasicOperators.xhtml#ID70):

```swift
let quotation = "We're a lot alike, you and I."
let sameQuotation = "We're a lot alike, you and I."
if quotation == sameQuotation {
print("These two strings are considered equal")
}
// Prints "These two strings are considered equal"
```

Two `String` values (or two `Character` values) are considered equal if their extended grapheme clusters are _canonically equivalent_. Extended grapheme clusters are canonically equivalent if they have the same linguistic meaning and appearance, even if they’re composed from different Unicode scalars behind the scenes.

For example, `LATIN SMALL LETTER E WITH ACUTE` (`U+00E9`) is canonically equivalent to `LATIN SMALL LETTER E` (`U+0065`) followed by `COMBINING ACUTE ACCENT` (`U+0301`). Both of these extended grapheme clusters are valid ways to represent the character `é`, and so they’re considered to be canonically equivalent:

```swift
// "Voulez-vous un café?" using LATIN SMALL LETTER E WITH ACUTE
let eAcuteQuestion = "Voulez-vous un caf\u{E9}?"

// "Voulez-vous un café?" using LATIN SMALL LETTER E and COMBINING ACUTE ACCENT
let combinedEAcuteQuestion = "Voulez-vous un caf\u{65}\u{301}?"

if eAcuteQuestion == combinedEAcuteQuestion {
print("These two strings are considered equal")
}
// Prints "These two strings are considered equal"
```

Conversely, `LATIN CAPITAL LETTER A` (`U+0041`, or `"A"`), as used in English, is _not_ equivalent to `CYRILLIC CAPITAL LETTER A` (`U+0410`, or `"А"`), as used in Russian. The characters are visually similar, but don’t have the same linguistic meaning:

```swift
let latinCapitalLetterA: Character = "\u{41}"

let cyrillicCapitalLetterA: Character = "\u{0410}"

if latinCapitalLetterA != cyrillicCapitalLetterA {
print("These two characters are not equivalent.")
}
// Prints "These two characters are not equivalent."
```

**Note**

>String and character comparisons in Swift are not locale-sensitive.

### Prefix and Suffix Equality

To check whether a string has a particular string prefix or suffix, call the string’s `hasPrefix(_:)` and `hasSuffix(_:)` methods, both of which take a single argument of type `String` and return a Boolean value.

The examples below consider an array of strings representing the scene locations from the first two acts of Shakespeare’s _Romeo and Juliet_:

```swift
let romeoAndJuliet = [
  "Act 1 Scene 1: Verona, A public place",
  "Act 1 Scene 2: Capulet's mansion",
  "Act 1 Scene 3: A room in Capulet's mansion",
  "Act 1 Scene 4: A street outside Capulet's mansion",
  "Act 1 Scene 5: The Great Hall in Capulet's mansion",
  "Act 2 Scene 1: Outside Capulet's mansion",
  "Act 2 Scene 2: Capulet's orchard",
  "Act 2 Scene 3: Outside Friar Lawrence's cell",
  "Act 2 Scene 4: A street in Verona",
  "Act 2 Scene 5: Capulet's mansion",
  "Act 2 Scene 6: Friar Lawrence's cell"
]
```

You can use the `hasPrefix(_:)` method with the `romeoAndJuliet` array to count the number of scenes in Act 1 of the play:

```swift
var act1SceneCount = 0
for scene in romeoAndJuliet {
  if scene.hasPrefix("Act 1 ") {
      act1SceneCount += 1
    }
}
print("There are \(act1SceneCount) scenes in Act 1")
// Prints "There are 5 scenes in Act 1"
```

Similarly, use the `hasSuffix(_:)` method to count the number of scenes that take place in or around Capulet’s mansion and Friar Lawrence’s cell:

```swift
var mansionCount = 0
var cellCount = 0
for scene in romeoAndJuliet {
  if scene.hasSuffix("Capulet's mansion") {
    mansionCount += 1
  } else if scene.hasSuffix("Friar Lawrence's cell") {
    cellCount += 1
  }
}
print("\(mansionCount) mansion scenes; \(cellCount) cell scenes")
// Prints "6 mansion scenes; 2 cell scenes"
```

**Note**

>The `hasPrefix(_:)` and `hasSuffix(_:)` methods perform a character-by-character canonical equivalence comparison between the extended grapheme clusters in each string, as described in [String and Character Equality](#ID299).

Unicode Representations of Strings
----------------------------------

When a Unicode string is written to a text file or some other storage, the Unicode scalars in that string are encoded in one of several Unicode-defined _encoding forms_. Each form encodes the string in small chunks known as _code units_. These include the UTF-8 encoding form (which encodes a string as 8-bit code units), the UTF-16 encoding form (which encodes a string as 16-bit code units), and the UTF-32 encoding form (which encodes a string as 32-bit code units).

Swift provides several different ways to access Unicode representations of strings. You can iterate over the string with a `for`\-`in` statement, to access its individual `Character` values as Unicode extended grapheme clusters. This process is described in [Working with Characters](#ID290).

Alternatively, access a `String` value in one of three other Unicode-compliant representations:

*   A collection of UTF-8 code units (accessed with the string’s `utf8` property)

*   A collection of UTF-16 code units (accessed with the string’s `utf16` property)

*   A collection of 21-bit Unicode scalar values, equivalent to the string’s UTF-32 encoding form (accessed with the string’s `unicodeScalars` property)


Each example below shows a different representation of the following string, which is made up of the characters `D`, `o`, `g`, `‼` (`DOUBLE EXCLAMATION MARK`, or Unicode scalar `U+203C`), and the 🐶 character (`DOG FACE`, or Unicode scalar `U+1F436`):

```swift
let dogString = "Dog‼🐶"
```

### UTF-8 Representation

You can access a UTF-8 representation of a `String` by iterating over its `utf8` property. This property is of type `String.UTF8View`, which is a collection of unsigned 8-bit (`UInt8`) values, one for each byte in the string’s UTF-8 representation:

![../_images/UTF8_2x.png](../_images/UTF8_2x.png)

```swift
for codeUnit in dogString.utf8 {
  print("\(codeUnit) ", terminator: "")
}
print("")
// Prints "68 111 103 226 128 188 240 159 144 182 "
```

In the example above, the first three decimal `codeUnit` values (`68`, `111`, `103`) represent the characters `D`, `o`, and `g`, whose UTF-8 representation is the same as their ASCII representation. The next three decimal `codeUnit` values (`226`, `128`, `188`) are a three-byte UTF-8 representation of the `DOUBLE EXCLAMATION MARK` character. The last four `codeUnit` values (`240`, `159`, `144`, `182`) are a four-byte UTF-8 representation of the `DOG FACE` character.

### UTF-16 Representation

You can access a UTF-16 representation of a `String` by iterating over its `utf16` property. This property is of type `String.UTF16View`, which is a collection of unsigned 16-bit (`UInt16`) values, one for each 16-bit code unit in the string’s UTF-16 representation:

![../_images/UTF16_2x.png](../_images/UTF16_2x.png)

```swift
for codeUnit in dogString.utf16 {
  print("\(codeUnit) ", terminator: "")
}
print("")
// Prints "68 111 103 8252 55357 56374 "
```

Again, the first three `codeUnit` values (`68`, `111`, `103`) represent the characters `D`, `o`, and `g`, whose UTF-16 code units have the same values as in the string’s UTF-8 representation (because these Unicode scalars represent ASCII characters).

The fourth `codeUnit` value (`8252`) is a decimal equivalent of the hexadecimal value `203C`, which represents the Unicode scalar `U+203C` for the `DOUBLE EXCLAMATION MARK` character. This character can be represented as a single code unit in UTF-16.

The fifth and sixth `codeUnit` values (`55357` and `56374`) are a UTF-16 surrogate pair representation of the `DOG FACE` character. These values are a high-surrogate value of `U+D83D` (decimal value `55357`) and a low-surrogate value of `U+DC36` (decimal value `56374`).

### Unicode Scalar Representation

You can access a Unicode scalar representation of a `String` value by iterating over its `unicodeScalars` property. This property is of type `UnicodeScalarView`, which is a collection of values of type `UnicodeScalar`.

Each `UnicodeScalar` has a `value` property that returns the scalar’s 21-bit value, represented within a `UInt32` value:

![../_images/UnicodeScalar_2x.png](../_images/UnicodeScalar_2x.png)

```swift
for scalar in dogString.unicodeScalars {
  print("\(scalar.value) ", terminator: "")
}
print("")
// Prints "68 111 103 8252 128054 "
```

The `value` properties for the first three `UnicodeScalar` values (`68`, `111`, `103`) once again represent the characters `D`, `o`, and `g`.

The fourth `codeUnit` value (`8252`) is again a decimal equivalent of the hexadecimal value `203C`, which represents the Unicode scalar `U+203C` for the `DOUBLE EXCLAMATION MARK` character.

The `value` property of the fifth and final `UnicodeScalar`, `128054`, is a decimal equivalent of the hexadecimal value `1F436`, which represents the Unicode scalar `U+1F436` for the `DOG FACE` character.

As an alternative to querying their `value` properties, each `UnicodeScalar` value can also be used to construct a new `String` value, such as with string interpolation:

```swift
for scalar in dogString.unicodeScalars {
  print("\(scalar) ")
}
// D
// o
// g
// ‼
// 🐶
```
