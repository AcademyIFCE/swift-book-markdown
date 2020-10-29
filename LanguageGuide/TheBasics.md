 The Basics

The Basics
==========

Swift é uma nova linguagem de programação para desenvolvimento de aplicações iOS, macOS, watchOS, e tvOS. Porém, você vai se sentir familiar com Swift por causa de sua experiencia de desenvolvimento em C e Objective-C.

Swift fornece sua própria versão de todos os tipos fundamentais de C e Objective-C, incluindo `Int` para inteiros, `Double` e `Float` para valores de ponto flutuante, `Bool` para valores Booleanos, e `String` para dados de texto. Swift também fornece versões poderosas dos três tipos primário de coleção, `Array`, `Set`, e `Dicionário`, como descrito em [Collection Types](CollectionTypes.xhtml).

Como C, Swift usa variáveis para guardar e referenciar valores com um nome identificador. Swift também faz uso extensivo de variáveis cujos valores não podem ser mudados. Estas são conhecidas como constantes, e são muito mais poderosas do que as constantes em C. Constantes são usadas em Swift para fazer o código mais seguro e de objetivo mais claro quando você trabalha com valores que não precisam mudar.

Em adição aos tipos familiares, Swift introduz tipos avançados não contidos em Objective-C, como túplas. Túplas possibilita você a criar e repassar grupos de valores. Você pode usar uma túpla para retornar múltiplos valores de uma função como um único valor composto.

Swift também introduz tipos opcionais, os quais podem lidar com a falta de valor. Opcionais quer dizer que "_tem_ um valor aqui e é igual a _x_" ou "_não tem_ um valor aqui". Usar opcionais é parecido com usar `nil` com ponteiros em Objective-C, mas eles funcionam para muitos tipos, não so classes. Opcionais não são apenas mais seguros quanto também são mais expressivos do que ponteiros para `nil` em Objective-C, eles estão a fonte de muitas das características mais poderosas da Swift.

Swift é uma linguagem de _tipo-seguro_, o que quer dizer que a linguagem ajuda voce a ser mais claro nos tipos dos valores que seu código usa. Se uma parte do seu código requer uma `String`, segurança de tipos previne você passar um `Int` sem querer. Igualmente, segurança de tipos previne você de passar uma `String` opcional para um bloco de código que requer uma `String` não opcional. Segurança de tipo ajuda você a encontrar e consertar erros o mais cedo possível no processo de desenvolvimento.

Constants and Variables
-----------------------

Constantes e variáveis associam um nome ( tal qual `maximumNumberOfLoginAttempts` ou `welcomeMessage` ) com um valor de um tipo específico ( tal qual o número `10` ou a string `"Hello"`). O valor de uma _constant_ não pode ser modificado uma vez que é atribuído, enquanto uma _variável_ pode ter um valor diferente atribuído no futuro.

### Declarando Constantes e Variáveis

Constantes e variáveis devem ser declaradas antes de serem utilizadas. Você declara constantes com a palavra chave `let` e variáveis com a palavra chave `var`. Aqui um exemplo de como constantes e variáveis podem ser utilizadas para guardar o número de tentativas de login que um usuário realizou:

```swift
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```
Esse código pode ser lido como:

"Declara uma nova constante chamada `maximumNumberOfLoginAttempts`, atribuindo a ela o valor de `10`. Então, declara uma nova variável chamada `currentLoginAttempt`, atribuindo a ela um valor inicial de `0`."

Nesse exemplo, o número máximo de tentativas de login é declarado como uma constante, porque o valor máximo nunca muda. O número atual de tentaivas de login é declarado como uma váriavel, porque esse valor deve ser incrementado toda vez após uma tentativa falha de login.

Você pode declarar múltiplas constantes ou múltiplas variáveis em uma única linha, separada por vírgulas:

```swift
var x = 0.0, y = 0.0, z = 0.0
````

**Nota**

> Se um valor armazenado no seu código não for ser modificado, sempre declare ele como uma constante, com a palavra chave `let`. Use variáveis apenas para armazenar valores que precisam ter a capacidade de mudar.

### Anotação de tipos

Você pode fornecer uma _type annotation_ (anotação de tipo) quando você declara uma constante ou variável, para deixar claro o tipo de valores que a constante ou variável pode armazenar. Escreva uma anotação de tipo colocando dois pontos após o nome da constante ou variável, seguido de um espaço, seguido pelo nome do tipo a ser usado.

Esse exemplo fornece uma anotação de tipo para a variável chamada `welcomeMessage`, para indicar que essa variável pode armazenar valores do tipo `String`:

```swift
var welcomeMessage: String
```

Os dois pontos na declaração significam "...do tipo..." então o código acima pode ser lido como:

"Declara uma variável chamada `welcomeMessage` que é do tipo `String`."

A frase "do tipo `String`" significa "pode armazernar qualquer `String`." Pense nisso como "o tipo da coisa" que pode ser armazenada.

A variável `welcomeMessage` agora pode ter qualquer string atribuida sem qualquer erro: 

```swift
welcomeMessage = "Hello"
````

Você pode definir múltiplas variáveis do mesmo tipo em uma só linha, separadas por vírgula, com uma única anotação de tipo ao fim do nome da última váriavel:

```swift
var red, green, blue: Double
````

**Nota**

> É rara a necessidade de escrever a anotação do tipo na prática. Se você fornecer um valor inicial para uma constante ou variável no momento que ela for definida, o Swift pode quase sempre inferir o tipo a ser usado por aquela constante ou variável, como descrito em [Segurança e Inferência de tipos](#ID322). No exemplo `welcomeMessage` acima, nenhum valor inicial é fornecido, então o tipo da `welcomeMessage` é especificado através da notação de tipo, ao invés de ser inferido a partir de uma valor inicial.

### Nomeando Constantes e Variáveis

Nomes de constantes e variávels pode conter quase todos os caracteres possíveis, incluindo caracteres Unicode:

```swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
````

Nomes de constantes e variáveis não podem conter caracteres de espaço em branco, simbolos matemáticos, setas, valores Unicodes escalares de uso privado, ou caracteres de desenho de linha ou caixa (line- and box-drawing). Nem podem começar com um número, apesar de que números podem ser incluidos em qualquer outro canto dentro do nome. 

Uma vez que você declara uma constante ou variável de um certo tipo, você não pode declara-la novamente com o mesmo nome, ou mudar seu valor para armazenar um tipo diferente. Nem pode modificar uma constante para uma variável ou uma variável para uma constante.

**Nota**

> Se você precisar dar a uma constante ou variável o mesmo nome de uma palavra reservada do Swift, encapsule o nome com backticks (`` ` ``) quando utilizar ela como nome. Porém, evite usar palavras chaves como nome a não ser que você absolutamente não tenha outra escolha.

Você pode modificar os valores de uma variável existente para um outro valor de um tipo compatível. Nesse exemplo, o valor de `friendlyWelcome`é modificado de  `"Hello!"` para `"Bonjour!"`:  

```swift
var friendlyWelcome = "Hello!"
friendlyWelcome = "Bonjour!"
// friendlyWelcome is now "Bonjour!"
````

Ao contrário da variável, o valor de uma constante não pode ser modificado após atribuido. A tentiva de realizar essa modificação será relatado com um erro quando o código for ser compilado.

```swift
let languageName = "Swift"
languageName = "Swift++"
// This is a compile-time error: languageName cannot be changed.
```

### Imprimindo Constantes e Variáveis

Você pode imprimir o valor atual de uma constante ou váriavel usando a função  `print(_:separator:terminator:)`:

```swift
print(friendlyWelcome)
// Prints "Bonjour!"
```

A função  `print(_:separator:terminator:)` é uma função global que imprime um ou mais valores para um output apropriado. No Xcode por exemplo, a função  `print(_:separator:terminator:)`  imprime seu output no painel de "console" do Xcode. Os paramêtros `separator` e `terminator` possuem valores padrões, então podem ser omitidos na chamada da função. Por padrão, a função termina a linha impressa com uma quebra de linha. Para imprimir valores sem uma quebra de linha, passe uma string vazia como terminator — por exemplo, `print(someValue, terminator: "")`. Para informações sobre os paramêtros com valores padrões, veja  [Valores Padrões de Paramêtros](Functions.xhtml#ID169). 

Swift usa interpolação de string para incluir o nome de uma constante ou variável como um _placeholder_ em uma string mais longa para induzir o swift a trocar esse _placeholder_ pelo valor atual da constante ou variável. Envolva o nome entre parentêses e escape ele com uma barra invertida antes do parentêse de abertura:

```swift
print("The current value of friendlyWelcome is \\(friendlyWelcome)")
// Prints "The current value of friendlyWelcome is Bonjour!"
````

*Nota*

> Todas as opções de interpolação de Strings são descritas em [Interpolação de Strings](StringsAndCharacters.xhtml#ID292).

Comentários
--------

Use comentários para incluir texto não executável em seu código, como uma nota ou lembrete para você. Comentários são ignorados pelo compilador do Swift quando seu código é compilado.

Comentários no Swift são muito similares aos em C. Comentários de uma única linha começam com duas barras (`//`):

```swift
// This is a comment.
```

Comentários multi-linhas começa com uma barra seguida de um asterisco (`/*`) e acabam com um asterisco seguido de uma barra (`*/`):

```swift
/* This is also a comment
but is written over multiple lines. */
```

Ao contrário de comentários multilinha em C, comentários multilinha em Swift pode ser aninhados dentro de outros comentários multilinha. Você escreve comentários aninhados começando um bloclo multilinha e então começando um segundo bloco multilinha dentro do primeiro bloco. O segundo bloco então se fecha, seguido pelo primeiro bloco:

```swift
/* This is the start of the first multiline comment.
/* This is the second, nested multiline comment. */
This is the end of the first multiline comment. */
```

Comentários multilinha aninhados permitem comentar grandes blocos de código de maneira mais rápida e fácil, mesmo se o código já possuír comentários multilinhas.

Ponto e Vírgula
----------

Ao contrário de muitas outras linguagens, Swift não precisa que você escreva um ponto e vírgula (`;`)  ao fim de cada declaração em seu código, apesar de que você pode fazer isso se quiser. Contudo, ponto e vírgula são _necessários_ se você quiser escrever múltiplas declarações separadas em uma única linha: 

```swift
let cat = "🐱"; print(cat)
// Prints "🐱"
```

Integers
--------
_Intengers_ são números inteiros sem componentes fracionais, tais como `42` e `-23`. Integers são do tipo _signed_ (positivo, zero ou negativo) ou _unsigned_ (positivo ou zero).

Swift fornece intengers _signed_ e _unsigned_ em formato de 8, 16, 32 e 64 bits. Esses integers seguem uma convenção de nome similar ao C, na qual o integer _unsigned_ de 8-bits é do tipo `UInt8`, e um integer _signed_ de 32-bits é do tipo `UInt32`. Como todos os tipos em Swift, esses tipos de integers tem seus nomes capitalizados. 

### Limites dos Integer

Você pode acessar o valor mínimo e máximo de cada tipo de intenger através das propriedades `min` e `max` dele:

```swift
let minValue = UInt8.min // minValue is equal to 0, and is of type UInt8
let maxValue = UInt8.max // maxValue is equal to 255, and is of type UInt8
```

Os valores dessas propriedades são do tamanho apropriado do tipo de número(tal como `UInt8`no exemplo acima) e por isso podem ser usadas em expressões juntos com valores do mesmo tipo.

### Int

Na maioria dos casos, você não precisa pegar um tipo especifíco de tamanho de inteiro no seu código. Swift fornece um tipo adicional de integer o `Int`, que tem o mesmo tamanho nativo da palavra da plataforma atual:

*   Em uma plataforma 32-bit, `Int` tem o mesmo tamanho que o `Int32`.
    
*   Em uma plataforma 64-bit, `Int` tem o mesmo tamanho que o `Int64`.
    

A não ser que você precise trabalhar com um tipo específico de intenger, sempre use `Int`para valores integers no seu código. Isso adiciona consistência e interoperabilidade. Até mesmo em plataformas 32-bit, `Int`consegue armazenar valores entre `-2,147,483,648` e `2,147,483,647`, e é grande o suficiente para um grande intervalo de inteiros. 

### UInt

Swift também fornece um tipo intenger _unsigned_, `UInt`, que tem o mesmo tamanho nativo da palavra da plataforma atual:

*   Em uma plataforma 32-bit, `Int` tem o mesmo tamanho que o `UInt32`.
    
*   Em uma plataforma 64-bit, `Int` tem o mesmo tamanho que o `UInt64`.    

**Nota**

> Use `UInt` apenas quando você precisa especificamente de um tipo integer unsigned que tenha o mesmo tamanho nativo da palavra da plataforma atual. Se esse não for o caso `Int` é preferido, mesmo quando os valores a serem armazenados são não negativos. O uso consistente de `Int` para valores inteiros ajuda na interoperabilidade do código, evita a necessidade de conversão entre diferentes tipos de números, e combina com a inferência de tipo de inteiros, como descrito em   [Segurança e Inferência de Tipo](#ID322).

Números de Ponto Flutuante
----------------------
Números de ponto flutuante são números com um componente fracional, tais como `3.14159`, `0.1`, e `-273.15`. 

tipos de ponto flutuante podem representar um intervalo bem maior do que tipos integer, e podem aramazenar valores muito maiores ou menores do que o que pode ser armazenado em um `Int`. Swift fornece dois tipos de números de ponto flutuante _signed_. 

*   `Double` representa um número de ponto flutuante de  64-bit.
    
*   `Float` representa um número de ponto flutuante de  32-bit.
    

Nota

`Double` possuí uma precisão ed 15 dígitos decimais, enquanto a precisão de `Float` pode ser tão pequena quanto 6 dígitos decimais. O tipo apropriado de ponto flutuante depende da natureza do intervalo de valores que você precisa trabalhar no seu código. Em situações nas quais qualquer um dos tipos é apropriado `Double`é preferido.

*Type Safety* e Inferência de Tipo
------------------------------

Swift é uma linguagem *type-safe*. Uma linguagem *type safe* encoraja que você seja claro em relação aos tipos dos valores com que seu código trabalha. Se uma parte do código requer uma `String`, você não pode passar um `Int` por engano.

Por ser *type-safe*, Swift executa checagens de tipo quando compila seu código e sinaliza quaisquer tipos incompatíveis como erros. Isso permite que você detecte e corrija erros o mais cedo possível no processo de desenvolvimento.

A checagem de tipo ajuda a evitar erros ao trabalhar com diferentes tipos de valores. No entanto, isso não significa que você precisa especificar o tipo de cada constante e variável que você declara. Se você não especificar o tipo do valor de que precisa, Swift usa _inferência de tipo_ para descobrir o tipo apropriado. Inferência de tipo permite que um compilador deduza o tipo de uma expressão específica automaticamente ao compilar seu código, simplesmente examinando os valores fornecidos.

Por causa da inferência de tipo, Swift requer muito menos declarações de tipo do que linguagens como C ou Objective-C. Constantes e variáveis ainda são explicitamente digitadas, mas muito do trabalho de especificação de tipo é feito para você.

A inferência de tipo é particularmente útil quando você declara uma constante ou variável com um valor inicial. Isso geralmente é feito atribuindo um _valor literal_ (ou _literal_) à constante ou variável no momento em que você a declara. (Um valor literal é um valor que aparece diretamente em seu código-fonte, como `42` e` 3.14159` nos exemplos abaixo.)

Por exemplo, se você atribuir um valor literal de `42` a uma nova constante sem dizer de que tipo ela é, Swift infere que você deseja que a constante seja um ʻInt`, porque você a inicializou com um número que se parece com um inteiro:

```swift
let meaningOfLife = 42
// meaningOfLife é inferido como sendo do tipo Int
```

Da mesma forma, se você não especificar um tipo para um literal de ponto flutuante, Swift infere que você deseja criar um `Double`:

```swift
let pi = 3.14159
// pi é inferido como sendo do tipo Double
```

O Swift sempre escolhe `Double` (em vez de` Float`) ao inferir o tipo de números de ponto flutuante.

Se você combinar literais inteiros e de ponto flutuante em uma expressão, um tipo de `Double` será inferido a partir do contexto:

```swift
let anotherPi = 3 + 0.14159
// anotherPi é também inferido como sendo do tipo Double
```

O valor literal de `3` não tem nenhum tipo explícito por si só e, portanto, um tipo de saída apropriado de `Double` é inferido da presença de um literal de ponto flutuante como parte da adição.

Numeric Literals
----------------

Integer literals can be written as:

*   A _decimal_ number, with no prefix
    
*   A _binary_ number, with a `0b` prefix
    
*   An _octal_ number, with a `0o` prefix
    
*   A _hexadecimal_ number, with a `0x` prefix
    

All of these integer literals have a decimal value of `17`:

```swift
let decimalInteger = 17
let binaryInteger = 0b10001 // 17 in binary notation
let octalInteger = 0o21 // 17 in octal notation
let hexadecimalInteger = 0x11 // 17 in hexadecimal notation
```

Floating-point literals can be decimal (with no prefix), or hexadecimal (with a `0x` prefix). They must always have a number (or hexadecimal number) on both sides of the decimal point. Decimal floats can also have an optional _exponent_, indicated by an uppercase or lowercase `e`; hexadecimal floats must have an exponent, indicated by an uppercase or lowercase `p`.

For decimal numbers with an exponent of `exp`, the base number is multiplied by 10exp:

*   `1.25e2` means 1.25 x 10ˆ2, or `125.0`.
    
*   `1.25e-2` means 1.25 x 10ˆ2, or `0.0125`.
    

For hexadecimal numbers with an exponent of `exp`, the base number is multiplied by 2exp:

*   `0xFp2` means 15 x 22, or `60.0`.
    
*   `0xFp-2` means 15 x 2ˆ2, or `3.75`.
    

All of these floating-point literals have a decimal value of `12.1875`:

```swift
let decimalDouble = 12.1875
let exponentDouble = 1.21875e1
let hexadecimalDouble = 0xC.3p0
```

Numeric literals can contain extra formatting to make them easier to read. Both integers and floats can be padded with extra zeros and can contain underscores to help with readability. Neither type of formatting affects the underlying value of the literal:

```swift
let paddedDouble = 000123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```

Conversão de Tipo Numérico
-----------------------

Use o tipo `Int` para todas as constantes e variáveis inteiras de propósito geral em seu código, mesmo que sejam conhecidas como não negativas. Usar o tipo inteiro padrão em situações cotidianas significa que as constantes e variáveis inteiras são imediatamente interoperáveis em seu código e corresponderão ao tipo inferido para valores literais inteiros.

Use outros tipos inteiros apenas quando eles forem especificamente necessários para a tarefa em questão, por causa de dados explicitamente dimensionados de uma fonte externa, ou para desempenho, uso de memória ou outra otimização necessária. O uso de tipos de tamanho explícito nessas situações ajuda a detectar qualquer estouro de valor acidental e documenta implicitamente a natureza dos dados que estão sendo usados.

### Conversão de Inteiro

O intervalo de números que podem ser armazenado em uma constante ou variável inteira é diferente para cada tipo numérico. Uma constante ou variável `Int8` pode armazenar números entre `-128` e` 127`, enquanto uma constante ou variável `UInt8` pode armazenar números entre `0` e` 255`. Um número que não cabe em uma constante ou variável de um tipo inteiro de tamanho explícito é relatado como um erro quando seu código é compilado:


```swift
let cannotBeNegative: UInt8 = -1
// UInt8 não pode armazenar números negativos, e portanto irá relatar um erro
let tooBig: Int8 = Int8.max + 1
// Int8 não pode armazenar um número maior que seu valor máximo,
// e então isso também reportará um erro
```

Como cada tipo numérico pode armazenar um intervalo diferente de valores, você deve optar pela conversão de tipo numérico caso a caso. Essa abordagem evita erros de conversão ocultos e ajuda a tornar as intenções de conversão de tipo explícitas em seu código.

Para converter um tipo numérico específico em outro, você inicializa um novo número do tipo desejado com o valor existente. No exemplo abaixo, a constante `twoThousand` é do tipo `UInt16`, enquanto a constante `one` é do tipo `UInt8`. Eles não podem ser adicionados diretamente, porque não são do mesmo tipo. Em vez disso, este exemplo chama `UInt16(one)` para criar um novo `UInt16` inicializado com o valor de `one`, e usa este valor no lugar do original:

```swift
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```

Como os dois lados da adição agora são do tipo `UInt16`, a adição é permitida. A constante de saída (`twoThousandAndOne`) é inferida como sendo do tipo `UInt16`, porque é a soma de dois valores `UInt16`.

`AlgumTipo(deValorInicial)` é a maneira padrão de chamar o inicializador de um tipo em Swift e passar um valor inicial. Nos bastidores, `UInt16` tem um inicializador que aceita um valor `UInt8`, e então este inicializador é usado para fazer um novo `UInt16` a partir de um `UInt8` existente. Entretanto, você não pode passar _qualquer_ tipo—tem que ser um tipo para o qual `UInt16` fornece um inicializador. Estender os tipos existentes para fornecer inicializadores que aceitem novos tipos (incluindo suas próprias definições de tipo) é abordado em [Extensions](Extensions.xhtml).

### Conversão de Inteiro e Ponto Flutuante

As conversões entre os tipos numéricos inteiros e de ponto flutuante devem ser explicitadas:

```swift
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine
// pi é igual a 3,14159 e é inferido ser do tipo Double
```

Aqui, o valor da constante `three` é usado para criar um novo valor do tipo `Double`, de forma que ambos os lados da adição sejam do mesmo tipo. Sem essa conversão, a adição não seria permitida.

A conversão de ponto flutuante em inteiro também deve ser explicitada. Um tipo inteiro pode ser inicializado com um valor `Double` ou` Float`:

```swift
let integerPi = Int(pi)
// integerPi é igual a 3, e é inferido ser do tipo Int
```

Valores de ponto flutuante são sempre truncados quando usados para inicializar um novo valor inteiro dessa maneira. Isso significa que `4.75` se torna `4` e `-3.9` se torna `-3`.

**Nota**

> As regras para combinar constantes e variáveis numéricas são diferentes das regras para literais numéricos. O valor literal `3` pode ser adicionado diretamente ao valor literal `0,14159`, porque os literais de número não têm um tipo explícito por si só. Seu tipo é inferido apenas no ponto em que são avaliados pelo compilador.

Type Aliases
------------

_Type aliases_(apelidos) definem um nome alternativo para um tipo existente. Você pode definir apelidos para os seus tipos com a palavra chave `typealias`.

_Type aliases_ são utéis quando você quer referir um tipo existente por um nome que é contextualmente mais apropriado, tal como quando trabalhando com um dado de um tamanho específico de uma fonte externa:

```swift
typealias AudioSample = UInt16
```

Uma vez definido um _type alias_, você pode usar ele em qualquer canto que você usaria o nome origianal:

```swift
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound is now 0
```

Aqui `AudioSample` é definido como um _alias_(apelido) para `UInt16`. Por ser um _alias_, a chamada para o `AudioSample.min` na verdade chamará o `UInt16.min`, que provê um valor inicial de zero para a variável `maxAmplitudeFound`. 

Booleanos
--------

Swift tem um tipo básico booleano chamado de `Bool`. Valores booleanos são referidos como _lógicos_, pois eles podem ser apenas verdadeiro ou falso. Swift provê dois valores constantes de booleano, `true` e `false`:

```swift
let orangesAreOrange = true
let turnipsAreDelicious = false
```

Os tipos de `orangesAreOrange` e `turnipsAreDelicious` foram inferidos como `Bool`pelo fato de que foram iniciados como valores literais booleanos. Como `Int` e `Double` acima, você não precisa declarar variáveis ou constantes como `Bool` se você definir elas como `true` ou `false` assim que forem criadas. A inferência de tipo ajuda o código em Swift ser mais conciso e legível quando inicializamos constantes ou variáveis com outros valores cujo o tipo já é conhecido. 

Valores booleanos são particulamente utéis quando você trabalha com declarações condicionais como a declaração `if`:

```swift
if turnipsAreDelicious {
    print("Mmm, tasty turnips!")
} else {
    print("Eww, turnips are horrible.")
}
// Prints "Eww, turnips are horrible."
```

Declarações condicionais tais quais a declaração `if` são exploradas em mais detalhes em [Controle de fluxo](ControlFlow.xhtml). 

A segurança de tipo do Swift impede valores não booleanos de serem substituidos por `Bool`. O exemplo a seguir vai informar um erro em tempo de compilação: 

```swift
let i = 1
if i {
    // this example will not compile, and will report an error
}
```

Porém, a alternativa abaixo é válida:

```swift
let i = 1
if i == 1 {
    // this example will compile successfully
}
```

O resultado da comparação  `i == 1` é do tipo `Bool`, então esse segundo exemplo vai passar na checagem de tipo. Comparações como  `i == 1` são discutidas em [Operadores básicos](BasicOperators.xhtml). 

Como com outros exemplos de segurança de tipo em Swift, essa abordagem evita erros acidentais e garante que a intenção de uma parte específica do código é sempre clara.

Tuples
------

_Tuplas_ agrupam múltiplos valores em um único valor composto. Os valores dentro de uma tupla podem ser de qualquer tipo e não precisam ser do mesmo tipo entre si.

Nesse exemplo `(404, "Not Found")` é uma tupla que descreve um _HTTP status code_. O código de status HTTP é um valor especial que é retornado por um servidor toda vez que você faz uma requisição web. Um código de status `404 Not Found` é retornando quando a página pedida não existe.

let http404Error = (404, "Not Found")
// http404Error é do tipo  (Int, String), e igual (404, "Not Found")

A tupla  `(404, "Not Found")` agrupa um `Int` e uma `String`  para fornecer um código de status HTTP com dois valores separados: um número e uma descrição legível por humanos. Pode ser descrita como "uma tupla de tipo `(Int, String)`"

Você pode criar tuplas com a permutação de qualquer tipos, elas podem conter quantos tipos diferentes você quiser. Não há nada que impeça você de ter uma tupla de tipo `(Int, Int, Int)`, ou `(String, Bool)`, ou qualquer outra permutação que você desejar. 

Você pode _decompor_ o contéudo de uma tupla em variáveis e constantes separadas, que você pode acessar normalmente:

```swift
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// Imprime "The status code is 404"
print("The status message is \(statusMessage)")
// Imprime "The status message is Not Found"
````

Se você precisar apenas de alguns dos tipos da tupla, você pode ignorar parte dela com um underscore(`_`) quando você for decompor a tupla:

```swift
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// Imprime "The status code is 404"
```

Alternativamente, acesse os elementos individuais em uma tupla usando index começando do zero:

```swift
print("The status code is \(http404Error.0)")
// Imprime "The status code is 404"
print("The status message is \(http404Error.1)")
// Imprime "The status message is Not Found"
```

Você pode nomear individualmente elementos em uma tupla quando a tupla é definida:

```swift
let http200Status = (statusCode: 200, description: "OK")
```

Se você nomear os elementos em uma tupla, você pode usar os nomes dos elementos para acessar o valor desses elementos:

```swift
print("The status code is \(http200Status.statusCode)")
// Imprime "The status code is 200"
print("The status message is \(http200Status.description)")
// Imprime "The status message is OK"
```

Tuplas são particulamente utéis como retorno de valores de funções. A função que tenta requerir uma página web pode retornar a tupla do tipo `(Int, String)`  para descrever um sucesso ou uma falha na requisição da página. Retornando uma tupla com dois valores distintos, cada um de um tipo diferente, a função provê informações mais utéis sobre o seu resultado, do que se retornasse apenas um único valor, de um único tipo. Para mais informações, leia [Funções com múltiplos valores de retorno](Functions.xhtml#ID164)

**Nota**

> Tuplas são utéis para um grupo simples de valores relacionados. Elas não são recomendadas para a criação de estrutras complexas de dados. Se sua estrutra de dados é provável de ser mais complexa, modele isso como uma classe ou uma struct, ao invés de uma tupla. Para mais informações, veja [Structures e Classes](ClassesAndStructures.xhtml) 

Optionals
---------

You use _optionals_ in situations where a value may be absent. An optional represents two possibilities: Either there _is_ a value, and you can unwrap the optional to access that value, or there _isn’t_ a value at all.

**Note**

> The concept of optionals doesn’t exist in C or Objective-C. The nearest thing in Objective-C is the ability to return `nil` from a method that would otherwise return an object, with `nil` meaning “the absence of a valid object.” However, this only works for objects—it doesn’t work for structures, basic C types, or enumeration values. For these types, Objective-C methods typically return a special value (such as `NSNotFound`) to indicate the absence of a value. This approach assumes that the method’s caller knows there’s a special value to test against and remembers to check for it. Swift’s optionals let you indicate the absence of a value for _any type at all_, without the need for special constants.

Here’s an example of how optionals can be used to cope with the absence of a value. Swift’s `Int` type has an initializer which tries to convert a `String` value into an `Int` value. However, not every string can be converted into an integer. The string `"123"` can be converted into the numeric value `123`, but the string `"hello, world"` doesn’t have an obvious numeric value to convert to.

The example below uses the initializer to try to convert a `String` into an `Int`:

```swift
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber is inferred to be of type "Int?", or "optional Int"
```

Because the initializer might fail, it returns an _optional_ `Int`, rather than an `Int`. An optional `Int` is written as `Int?`, not `Int`. The question mark indicates that the value it contains is optional, meaning that it might contain _some_ `Int` value, or it might contain _no value at all_. (It can’t contain anything else, such as a `Bool` value or a `String` value. It’s either an `Int`, or it’s nothing at all.)

### nil

You set an optional variable to a valueless state by assigning it the special value `nil`:

```swift
var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value
```

**Note**

> You can’t use `nil` with non-optional constants and variables. If a constant or variable in your code needs to work with the absence of a value under certain conditions, always declare it as an optional value of the appropriate type.

If you define an optional variable without providing a default value, the variable is automatically set to `nil` for you:

```swift
var surveyAnswer: String?
// surveyAnswer is automatically set to nil
```

**Note**

> Swift’s `nil` isn’t the same as `nil` in Objective-C. In Objective-C, `nil` is a pointer to a nonexistent object. In Swift, `nil` isn’t a pointer—it’s the absence of a value of a certain type. Optionals of _any_ type can be set to `nil`, not just object types.

### If Statements and Forced Unwrapping

You can use an `if` statement to find out whether an optional contains a value by comparing the optional against `nil`. You perform this comparison with the “equal to” operator (`==`) or the “not equal to” operator (`!=`).

If an optional has a value, it’s considered to be “not equal to” `nil`:

```swift
if convertedNumber != nil {
    print("convertedNumber contains some integer value.")
}
// Prints "convertedNumber contains some integer value."
```

Once you’re sure that the optional _does_ contain a value, you can access its underlying value by adding an exclamation mark (`!`) to the end of the optional’s name. The exclamation mark effectively says, “I know that this optional definitely has a value; please use it.” This is known as _forced unwrapping_ of the optional’s value:

```swift
if convertedNumber != nil {
    print("convertedNumber has an integer value of \\(convertedNumber!).")
}
// Prints "convertedNumber has an integer value of 123."
```

For more about the `if` statement, see [Control Flow](ControlFlow.xhtml).

**Note**

> Trying to use `!` to access a nonexistent optional value triggers a runtime error. Always make sure that an optional contains a non-`nil` value before using `!` to force-unwrap its value.

### Optional Binding

You use _optional binding_ to find out whether an optional contains a value, and if so, to make that value available as a temporary constant or variable. Optional binding can be used with `if` and `while` statements to check for a value inside an optional, and to extract that value into a constant or variable, as part of a single action. `if` and `while` statements are described in more detail in [Control Flow](ControlFlow.xhtml).

Write an optional binding for an `if` statement as follows:

```swift
if let constantName = someOptional {
    statements
}
```

You can rewrite the `possibleNumber` example from the [Optionals](#ID330) section to use optional binding rather than forced unwrapping:

```swift
if let actualNumber = Int(possibleNumber) {
    print("The string \\"\\(possibleNumber)\\" has an integer value of \\(actualNumber)")
} else {
    print("The string \\"\\(possibleNumber)\\" could not be converted to an integer")
}
// Prints "The string "123" has an integer value of 123"
```

This code can be read as:

“If the optional `Int` returned by `Int(possibleNumber)` contains a value, set a new constant called `actualNumber` to the value contained in the optional.”

If the conversion is successful, the `actualNumber` constant becomes available for use within the first branch of the `if` statement. It has already been initialized with the value contained _within_ the optional, and so there’s no need to use the `!` suffix to access its value. In this example, `actualNumber` is simply used to print the result of the conversion.

You can use both constants and variables with optional binding. If you wanted to manipulate the value of `actualNumber` within the first branch of the `if` statement, you could write `if var actualNumber` instead, and the value contained within the optional would be made available as a variable rather than a constant.

You can include as many optional bindings and Boolean conditions in a single `if` statement as you need to, separated by commas. If any of the values in the optional bindings are `nil` or any Boolean condition evaluates to `false`, the whole `if` statement’s condition is considered to be `false`. The following `if` statements are equivalent:

```swift
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
// Prints "4 < 42 < 100"

if let firstNumber = Int("4") {
    if let secondNumber = Int("42") {
        if firstNumber < secondNumber && secondNumber < 100 {
            print("\(firstNumber) < \(secondNumber) < 100")
        }
    }
}
// Prints "4 < 42 < 100"
```

**Note**

> Constants and variables created with optional binding in an `if` statement are available only within the body of the `if` statement. In contrast, the constants and variables created with a `guard` statement are available in the lines of code that follow the `guard` statement, as described in [Early Exit](ControlFlow.xhtml#ID525).

### Implicitly Unwrapped Optionals

As described above, optionals indicate that a constant or variable is allowed to have “no value”. Optionals can be checked with an `if` statement to see if a value exists, and can be conditionally unwrapped with optional binding to access the optional’s value if it does exist.

Sometimes it’s clear from a program’s structure that an optional will _always_ have a value, after that value is first set. In these cases, it’s useful to remove the need to check and unwrap the optional’s value every time it’s accessed, because it can be safely assumed to have a value all of the time.

These kinds of optionals are defined as _implicitly unwrapped optionals_. You write an implicitly unwrapped optional by placing an exclamation mark (`String!`) rather than a question mark (`String?`) after the type that you want to make optional.

Implicitly unwrapped optionals are useful when an optional’s value is confirmed to exist immediately after the optional is first defined and can definitely be assumed to exist at every point thereafter. The primary use of implicitly unwrapped optionals in Swift is during class initialization, as described in [Unowned References and Implicitly Unwrapped Optional Properties](AutomaticReferenceCounting.xhtml#ID55).

An implicitly unwrapped optional is a normal optional behind the scenes, but can also be used like a non-optional value, without the need to unwrap the optional value each time it’s accessed. The following example shows the difference in behavior between an optional string and an implicitly unwrapped optional string when accessing their wrapped value as an explicit `String`:

```swift
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation mark

let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation mark
```

You can think of an implicitly unwrapped optional as giving permission for the optional to be unwrapped automatically whenever it’s used. Rather than placing an exclamation mark after the optional’s name each time you use it, you place an exclamation mark after the optional’s type when you declare it.

**Note**

> If an implicitly unwrapped optional is `nil` and you try to access its wrapped value, you’ll trigger a runtime error. The result is exactly the same as if you place an exclamation mark after a normal optional that doesn’t contain a value.

You can still treat an implicitly unwrapped optional like a normal optional, to check if it contains a value:

```swift
if assumedString != nil {
    print(assumedString!)
}
// Prints "An implicitly unwrapped optional string."
```

You can also use an implicitly unwrapped optional with optional binding, to check and unwrap its value in a single statement:

```swift
if let definiteString = assumedString {
    print(definiteString)
}
// Prints "An implicitly unwrapped optional string."
```

**Note**

> Don’t use an implicitly unwrapped optional when there’s a possibility of a variable becoming `nil` at a later point. Always use a normal optional type if you need to check for a `nil` value during the lifetime of a variable.

Error Handling
--------------

You use _error handling_ to respond to error conditions your program may encounter during execution.

In contrast to optionals, which can use the presence or absence of a value to communicate success or failure of a function, error handling allows you to determine the underlying cause of failure, and, if necessary, propagate the error to another part of your program.

When a function encounters an error condition, it _throws_ an error. That function’s caller can then _catch_ the error and respond appropriately.

```swift
func canThrowAnError() throws {
    // this function may or may not throw an error
}
```

A function indicates that it can throw an error by including the `throws` keyword in its declaration. When you call a function that can throw an error, you prepend the `try` keyword to the expression.

Swift automatically propagates errors out of their current scope until they’re handled by a `catch` clause.

```swift
do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```
A `do` statement creates a new containing scope, which allows errors to be propagated to one or more `catch` clauses.

Here’s an example of how error handling can be used to respond to different error conditions:

```swift
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```

In this example, the `makeASandwich()` function will throw an error if no clean dishes are available or if any ingredients are missing. Because `makeASandwich()` can throw an error, the function call is wrapped in a `try` expression. By wrapping the function call in a `do` statement, any errors that are thrown will be propagated to the provided `catch` clauses.

If no error is thrown, the `eatASandwich()` function is called. If an error is thrown and it matches the `SandwichError.outOfCleanDishes` case, then the `washDishes()` function will be called. If an error is thrown and it matches the `SandwichError.missingIngredients` case, then the `buyGroceries(_:)` function is called with the associated `[String]` value captured by the `catch` pattern.

Throwing, catching, and propagating errors is covered in greater detail in [Error Handling](ErrorHandling.xhtml).

Assertions and Preconditions
----------------------------

_Assertions_ and _preconditions_ are checks that happen at runtime. You use them to make sure an essential condition is satisfied before executing any further code. If the Boolean condition in the assertion or precondition evaluates to `true`, code execution continues as usual. If the condition evaluates to `false`, the current state of the program is invalid; code execution ends, and your app is terminated.

You use assertions and preconditions to express the assumptions you make and the expectations you have while coding, so you can include them as part of your code. Assertions help you find mistakes and incorrect assumptions during development, and preconditions help you detect issues in production.

In addition to verifying your expectations at runtime, assertions and preconditions also become a useful form of documentation within the code. Unlike the error conditions discussed in [Error Handling](#ID515) above, assertions and preconditions aren’t used for recoverable or expected errors. Because a failed assertion or precondition indicates an invalid program state, there’s no way to catch a failed assertion.

Using assertions and preconditions isn’t a substitute for designing your code in such a way that invalid conditions are unlikely to arise. However, using them to enforce valid data and state causes your app to terminate more predictably if an invalid state occurs, and helps make the problem easier to debug. Stopping execution as soon as an invalid state is detected also helps limit the damage caused by that invalid state.

The difference between assertions and preconditions is in when they’re checked: Assertions are checked only in debug builds, but preconditions are checked in both debug and production builds. In production builds, the condition inside an assertion isn’t evaluated. This means you can use as many assertions as you want during your development process, without impacting performance in production.

### Debugging with Assertions

You write an assertion by calling the [`assert(_:_:file:line:)`](https://developer.apple.com/documentation/swift/1541112-assert) \[https://developer.apple.com/documentation/swift/1541112-assert\] function from the Swift standard library. You pass this function an expression that evaluates to `true` or `false` and a message to display if the result of the condition is `false`. For example:

```swift
let age = \-3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 is not >= 0.
```

In this example, code execution continues if `age >= 0` evaluates to `true`, that is, if the value of `age` is nonnegative. If the value of `age` is negative, as in the code above, then `age >= 0` evaluates to `false`, and the assertion fails, terminating the application.

You can omit the assertion message—for example, when it would just repeat the condition as prose.

```swift
assert(age >= 0)
```

If the code already checks the condition, you use the [`assertionFailure(_:file:line:)`](https://developer.apple.com/documentation/swift/1539616-assertionfailure) \[https://developer.apple.com/documentation/swift/1539616-assertionfailure\] function to indicate that an assertion has failed. For example:

```swift
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```

### Enforcing Preconditions

Use a precondition whenever a condition has the potential to be false, but must _definitely_ be true for your code to continue execution. For example, use a precondition to check that a subscript is not out of bounds, or to check that a function has been passed a valid value.

You write a precondition by calling the [`precondition(_:_:file:line:)`](https://developer.apple.com/documentation/swift/1540960-precondition) \[https://developer.apple.com/documentation/swift/1540960-precondition\] function. You pass this function an expression that evaluates to `true` or `false` and a message to display if the result of the condition is `false`. For example:

```swift
// In the implementation of a subscript...
precondition(index > 0, "Index must be greater than zero.")
```

You can also call the [`preconditionFailure(_:file:line:)`](https://developer.apple.com/documentation/swift/1539374-preconditionfailure) \[https://developer.apple.com/documentation/swift/1539374-preconditionfailure\] function to indicate that a failure has occurred—for example, if the default case of a switch was taken, but all valid input data should have been handled by one of the switch’s other cases.

**Note**

> If you compile in unchecked mode (`-Ounchecked`), preconditions aren’t checked. The compiler assumes that preconditions are always true, and it optimizes your code accordingly. However, the `fatalError(_:file:line:)` function always halts execution, regardless of optimization settings.

You can use the `fatalError(_:file:line:)` function during prototyping and early development to create stubs for functionality that hasn’t been implemented yet, by writing `fatalError("Unimplemented")` as the stub implementation. Because fatal errors are never optimized out, unlike assertions or preconditions, you can be sure that execution always halts if it encounters a stub implementation.
