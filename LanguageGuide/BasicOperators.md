 Basic Operators  

Operadores Básicos
===============

Um _operador_ é um símbolo ou frase especial que você utiliza para checar, mudar ou combinar valores. Por exemplo, o operador de adição (`+`) soma dois números, como em `let i = 1 + 2`, e o operador lógico AND (`&&`) combina dois valores Booleanos, como em `if enteredDoorCode && passedRetinaScan`.

Swift suporta a maioria dos operadores padrão de C e melhora várias _capabilities_ para eliminar erros comuns de código. O operador de atribuição (`=`) não retorna um valor, para previnir que seja usado erroneamente quando é previsto o uso do operador igual a (`==`). Operadores aritméticos (`+`, `-`, `*`, `/`, `%` e assim por diante) detectam e proibem o _overflow_ de valores, para evitar resultados inesperados quando for trabalhar com números que se tornam maiores ou menores que o intervalo de valores permitidos pelo tipo que os armazena. Você pode optar pelo _overflow_ de valores utilizando os operadores de _overflow_ do Swift, como descrito em [Overflow Operators](AdvancedOperators.xhtml#ID37).

Swift também provê operadores de intervalo que não são encontrados em C , como `a..<b` e `a...b`, como um atalho para expressar uma faixa de valores.

Este capítulo descreve os operadores mais comuns em Swift. [Advanced Operators](AdvancedOperators.xhtml) fala sobre os operadores avançados em Swift, e descreve como definir seus próprios operadores e implementar os operadores padrão para seus tipos customizados.

Terminologia
-----------

Operadores podem ser unários, binários, ou ternários:

*   Operadores _unários_ operam em um único objeto (como em `-a`). Operadores unários _prefixados_ aparecem imediatamente antes do seu objeto (como em `!b`), e operadores unários _postfix_ aparecem imediatamente depois do objeto (como em `c!`).

*   Operadores _binários_ operam em dois objetos (como em `2 + 3`) e são _infix_ porque eles aparecem entre os objetos.
    
*   Operadores _ternários_ operam em três objetos. Como em C, Swift possui apenas um operador ternário: o operador ternário de condição (`a ? b : c`).
    

Os valores que os operadores afetam são chamados de _operandos_. Na expressão `1 + 2`, o símbolo `+` é um operador binário e seus dois operandos são os valores `1` e `2`.

Operador de Atribuição
-------------------

O _operador de atribuição_ (`a = b`) inicializa ou atualiza o valor de `a` com o valor de `b`:

```swift
let b = 10
var a = 5
a = b
// a agora é igual a 10
```

Se o lado direito da atribuição for uma tupla com múltiplos valores, seus elementos podem ser decompostos em várias constantes ou váriaveis de uma vez só:

```swift
let (x, y) = (1, 2)
// x é igual a 1, e y é igual a 2
```

Diferentemente do operador de atribuição em C e Objective-C, o operador de atribuição em Swift não retorna um valor. A declaração abaixo não é válida:

```swift
if x = y {
    // Isto não é válido, porque x = y não retorna um valor.
}
```

Esta característica previne que o operador de atribuição (`=`) seja usado por acidente quando o operador igual a (`==`) é o desejado. Ao fazer `if x = y` inválido, Swift ajuda você a evitar erros deste tipo no seu código.

Operadores Aritméticos
--------------------

Swift suporta os quatro _operadores aritméticos_ padrão para todos os tipos de número:

*   Adição (`+`)
    
*   Subtração (`-`)
    
*   Multiplicação (`*`)
    
*   Divisão (`/`)
    
```swift
1 + 2 // igual a 3
5 - 3 // igual a 2
2 * 3 // igual a 6
10.0 / 2.5 // igual a 4.0
```

Diferentemente dos operadores em C e Objective-C, os operadores aritméticos em Swift não permitem o _overflow_ de valores por padrão. Você pode optar pelo _overflow_ de valores utilizando os operadores de _overflow_ do Swift (como em `a &+ b`). Veja [Overflow Operators](AdvancedOperators.xhtml#ID37).

O operador de adição também é suportado para concatenação de `String`:

```swift
"hello, " + "world" // igual a "hello, world"
```

### Operador Resto

O _operador resto_ (`a % b`) computa quantos múltiplos de `b` cabem em `a` e retorna o valor que sobrou (conhecido como _resto_).

**Nota**

> O operador resto (`%`) também é conhecido como o _operador módulo_ em outras linguagens. No entanto, seu comportamento em Swift para números negativos significa que, rigorosamente falando, é um resto em vez de uma operação módulo.

Veja como o operador resto funciona: Para calcular `9 % 4`, você primeiro descobre quantos `4` cabem dentro de `9`:

![../_images/remainderInteger_2x.png](../_images/remainderInteger_2x.png)

Você pode encaixar dois `4` dentro do `9`, e o resto é `1` (indicado em laranja).

Em Swift, isso seria escrito como:

```swift
9 % 4 // igual a 1
```

Para determinar a resposta para `a % b`, o operador `%` calcula a seguinte equação e retorna o `resto` como sua saída:

`a` = (`b` x `algum multiplicador`) + `resto`

onde `algum multiplicador` é o maior número de múltiplos de `b` que cabem dentro de `a`.

Inserindo `9` e `4` nesta equação gera:

`9` = (`4` x `2`) + `1`

O mesmo método é aplicado quando calculando o resto para um valor negativo de `a`:

```swift
-9 % 4 // igual a -1
```

Inserindo `-9` e `4` na equação gera:

`-9` = (`4` x `-2`) + `-1`

dando um valor restante de `-1`.

O sinal de `b` é ignorado para valores negativos de `b`. Isso significa que `a % b` e `a % -b` sempre dão a mesma resposta.

### Operador Unário Menos

O sinal de um valor numérico pode ser alternado usando um `-` prefixo, conhecido como o _operador unário menos_:

```swift
let three = 3
let minusThree = -three // minusThree é igual a -3
let plusThree = -minusThree // plusThree é igual a 3, ou "menos menos três"
```

O operador unário menos (`-`) é anexado diretamente antes do valor que opera, sem nenhum espaço em branco.

### Operador Unário Mais

O _operador unário mais_ (`+`) simplesmente retorna o valor no qual opera, sem nenhuma mudança:

```swift
let minusSix = -6
let alsoMinusSix = +minusSix // alsoMinusSix é igual a -6
```

Apesar do operador unário mais não fazer nada, você pode usá-lo para dar simetria ao seu código para números positivos quando também estiverem usando o operador unário menos para números negativos.

Operadores Compostos de Atribuição
-----------------------------

Como em C, Swift oferece _operadores compostos de atribuição_ que combinam atribuição (`=`) com outra operação. Um exemplo é o _operador aditivo de atribuição_ (`+=`):

```swift
var a = 1
a += 2
// a agora é igual a 3
```

A expressão `a += 2` é uma abreviação para `a = a + 2`. Efetivamente, a adição e a atribuição são combinados em um único operador que realiza as duas tarefas ao mesmo tempo.

**Nota**

> Os operadores compostos de atribuição não retornam um valor. Por exemplo, você não pode escrever`let b = a += 2`.

Para mais informações sobre os operadores fornecidos pela biblioteca padrão do Swift, veja [Operator Declarations](https://developer.apple.com/documentation/swift/operator_declarations).

Operadores de Comparação
--------------------

Swift suporta todos os _operadores de comparação_ padrão do C:

*   Igual a (`a == b`)
    
*   Não igual a / Diferente de (`a != b`)
    
*   Maior que (`a > b`)
    
*   Menor que (`a < b`)
    
*   Maior ou igual a (`a >= b`)
    
*   Menor ou igual a (`a <= b`)
    

**Nota**

> Swift também fornece dois _operadores identidade_ (`===` and `!==`), que podem ser utilizados para testar se duas referências de objeto ambas referem-se à mesma instância de objeto. Para mais informações, veja [Identity Operators](ClassesAndStructures.xhtml#ID90).

Cada um dos operadores de comparação retorna um valor do tipo `Bool` para indicar se a afirmação é verdadeira ou não:

```swift
1 == 1 // true porque 1 é igual a 1
2 != 1 // true porque 2 não é igual a 1
2 > 1 // true porque 2 é maior que 1
1 < 2 // true porque 1 é menor que 2
1 >= 1 // true porque 1 é maior ou igual a 1
2 <= 1 // false porque 2 não é menor ou igual a 1
```

Operadores de comparação são normalmente utilizados em estruturas condicionais, como na estrutura `if`:

```swift
let name = "world"
if name == "world" {
    print("hello, world")
} else {
    print("I'm sorry \\(name), but I don't recognize you")
}
// Imprime "hello, world", porque nome é, de fato, igual a "world".
```

Para mais sobre a estrutura `if`, veja [Control Flow](ControlFlow.xhtml).

Você pode comparar duas tuplas se elas tiverem o mesmo tipo e o mesmo número de valores. Tuplas são comparadas da esquerda para a direita, um valor por vez, até que a comparação encontre dois valores que sejam diferentes. Estes dois valores são comparados, e o resultado desta comparação determina o resultado geral da comparação da tupla. Se todos os elementos são iguais, então as próprias tuplas são iguais. Por exemplo:

```swift
(1, "zebra") < (2, "apple") // true porque 1 é menor que 2; "zebra" e "apple" não são comparados
(3, "apple") < (3, "bird") // true porque 3 é igual a 3, e "apple" é menor que "bird"
(4, "dog") == (4, "dog") // true porque 4 é igual a 4, e "dog" é igual a "dog"
```

No exemplo acima, você pode ver o comportamento da comparação da esquerda à direita na primeira linha. Porque `1` é menor que `2`, `(1, "zebra")` é considerado menor que `(2, "apple")`, independente de quaisquer outros valores nas tuplas. Não importa se `"zebra"` não é menor que `"apple"`, porque a comparação já foi determinda pelo primeiro elemento das tuplas. No entanto, quando o primeiro elemento das tuplas são o mesmo elemento, o segundo elemento das tuplas _são_ comparados—isso é o que acontece na segunda e terceira linha.

Tuplas podem ser comparadas com um dado operador apenas se o operador pode ser aplicado a cada valor nas suas respectivas tuplas. Por exemplo, como demonstrado no código abaixo, você pode comparar duas tuplas do tipo `(String, Int)` porque ambos os valores `String` e `Int` podem ser comparados usando o operador `<`. Em contraste, duas tuplas do tipo `(String, Bool)` não podem ser comparados com o operador `<` porque o operador `<` não pode ser aplicado a valores do tipo `Bool`.

```swift
("blue", -1) < ("purple", 1) // OK, calculado para true
("blue", false) < ("purple", true) // Erro porque < não pode comparar valores Booleanos
```

**Nota**

> A biblioteca padrão do Swift inclui operadores de comparação para tuplas com menos de sete elementos. Para comparar tuplas com sete ou mais elementos, você mesmo precisa implementar os operadores de comparação.

Operador Ternário Condicional
----------------------------

O _operador ternário condicional_ é um operador especial com três partes, que toma a forma `question ? answer1 : answer2`. É um atalho para avaliar uma ou duas expressões baseado se `question` é verdadeiro ou falso. Se `question` é verdadeiro, ele avalia `answer1` e retorna o seu valor; caso contrário, ele avalia `answer2` e retorna seu valor.

O operador ternário condicional é uma forma curta para o código abaixo:

```swift
if question {
    answer1
} else {
    answer2
}
```

Aqui está um exemplo, que calcula a altura para uma linha da tabela. A altura da tabela deve ser 50 pontos mais alta que a altura do conteúdo se a linha tiver um cabeçalho, e 20 pontos mais alta se a linha não tiver cabeçalho:

```swift
let contentHeight = 40
let hasHeader = true
let rowHeight = contentHeight + (hasHeader ? 50 : 20)
// rowHeight é igual a 90
```

O exemplo acima é uma abreviação para o código abaixo:

```swift
let contentHeight = 40
let hasHeader = true
let rowHeight: Int
if hasHeader {
    rowHeight = contentHeight + 50
} else {
    rowHeight = contentHeight + 20
}
9.  // rowHeight é igual a 90
```

O uso do operador ternário condicional no primeiro exemplo significa que `rowHeight` pode ser atribuido ao valor correto em uma única linha de código, que é mais concisa que o código usado no segundo exemplo.

O operador ternário condicional fornece uma abreviação eficiente para decidir quais das duas expressões considerar. Use o operador ternário condicional com cuidado, no entanto. Sua concisão pode levar a um código díficil de ler caso usado em excesso. Evite combinar multiplas instâncias do operador ternário condicional em uma declaração composta.

Operador Nil-Coalescing
-----------------------

O _operador nil-coalescing_ (`a ?? b`) desempacota um `a` optional se ele conter um valor, ou retorna um valor padrão `b` se `a` for `nil`. A expressão `a` é sempre de um tipo optional. A expressão `b` precisa corresponder ao tipo armazenado dentro de `a`.

O operador nil-coalescing é uma forma curta de escrever o código abaixo:

```swift
a != nil ? a! : b
```

O código acima usada um operador ternário condicional e _forced unwrapping_ (`a!`) para acessar o valor empacotado dentro de `a` quando `a` não for `nil`, e, caso contrário, retornar `b`. O operador nil-coalescing fornece uma forma mais elegante de encapsular esta checagem condicional e desempacotá-la em uma forma concisa e legível.

**Nota**

> Se o valor de `a` é diferente de `nil`, o valor de `b` não é avaliado. Isto é conhecido como uma _avaliação curto-circuito_.

O exemplo abaixo usa o operador nil-coalescing para escolher entre o nome de uma cor padrão e o nome de uma cor definida pelo usuário:

```swift
let defaultColorName = "red"
var userDefinedColorName: String? // padrão é nil

var colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName é nil, então colorNameToUse é definido para o padrão de "red"
```

A variável `userDefinedColorName` é definida como uma `String` optional, com um valor padrão de `nil`. Como `userDefinedColorName` é de um tipo optional, você pode usar o operador nil-coalescing para levar em consideração o seu valor. No exemplo acima, o operador é usado para determinar um valor inicial para uma variável do tipo `String` chamada `colorNameToUse`. Como `userDefinedColorName` é `nil`, a expressão `userDefinedColorName ?? defaultColorName` retorna o valor de `defaultColorName`, ou `"red"`.

Se você atribuir um valor diferente de `nil` para `userDefinedColorName` e realizar novamente a checagem do operador nil-coalescing, o valor empacotado dentro de `userDefinedColorName` é utilizado ao invés do padrão:

```swift
userDefinedColorName = "green"
colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName não é nil, então colorNameToUse é definido como "green"
```

Operadores de Intervalo
---------------

Swift inclui vários _operadores de intervalo_, que são atalhos para expressar uma faixa de valores.

### Operador de Intervalo Fechado

O _operador de intervalo fechado_ (`a...b`) define um intervalo que vai de `a` até `b`, e inclui os valores de `a` e `b`. O valor de `a` não pode ser maior que `b`.

O operador de intervalo fechado é útil quando se está iterando sobre um intervalo no qual você quer usar todos os valores, como com um loop `for`\-`in`:

```swift
for index in 1...5 {
    print("\\(index) times 5 is \\(index \* 5)")
}
// 1 vezes 5 é 5
// 2 vezes 5 é 10
// 3 vezes 5 é 15
// 4 vezes 5 é 20
// 5 vezes 5 é 25
```

Para mais sobre loops `for`-`in`, veja [Control Flow](ControlFlow.xhtml).

### Operador de Intervalo Semiaberto

O _operador de intervalo semiaberto_ (`a..<b`) define um alcance indo de `a` até `b`, mas não inclui `b`. Diz-se ser _semiaberto_ porque contêm o primeiro valor, mas não o seu valor final. Assim como o operador de intervalo fechado, o valor de `a` não pode ser maior que o de `b`. Se o valor de `a` for igual ao de `b`, então o intervalo resultante será vazio.

Intervalos semiabertos são particulamente úteis quando se trabalha com listas baseadas em zero como _arrays_, onde é útil contar até (mas sem incluir) o tamanho da lista:

```swift
let names = \["Anna", "Alex", "Brian", "Jack"\]
let count = names.count
for i in 0..<count {
    print("Person \\(i + 1) is called \\(names\[i\])")
}
// Pessoa 1 se chama Anna
// Pessoa 2 se chama Alex
// Pessoa 3 se chama Brian
// Pessoa 4 se chama Jack
```

Note que o _array_ contêm quatro itens, mas `0..<count` ´so conta até `3` (o índice do último item no _array_), porque é um intervalo semiaberto. Para mais sobre _arrays_, veja [Arrays](CollectionTypes.xhtml#ID107).

### Intervalo Unilateral

O operador de intervalo fechado tem uma forma alternativa para intervalos que continuam o mais longe possível em uma direção—por exemplo, um intervalo que inclui todos os elementos de um _array_ a partir do índice 2. Nesses casos, você pode omitir o valor de um lado do operador de intervalo. Este tipo de intervalo é chamado de _intervalo unilateral_ porque o operador possui um valor apenas em um lado. Por exemplo:

```swift
for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian
```

O operador de intervalo semiaberto também possui uma forma unilateral escrita apenas com o seu valor final. Assim como quando você inclui um valor em ambos os lados, o valor final não é parte do intervalo. Por exemplo:

```swift
for name in names[..<2] {
    print(name)
}
// Anna
// Alex
```

Intervalos unilaterais podem ser usados em outros contextos, não apenas em coleções, listas e sequências. Você não pode iterar sobre um intervalo unilateral que omita o primeiro valor, porque não se sabe por onde a iteração deve começar. Você _pode_ iterar sobre um intervalo unilateral que omite seu valor final; no entanto, devido ao intervalo continuar indefinidamente, tenha certeza que você adicione uma condição de término para o loop. Você também pode checar se um intervalo unilateral contém um valor específico, como mostrado no código abaixo.

```swift
let range = ...5
range.contains(7) // false
range.contains(4) // true
range.contains(-1) // true
```

Operadores Lógicos
-----------------

_Operadores lógicos_ modificam ou combinam os valores lógicos Booleanos `true` e `false`. Swift suporta os três operadores lógicos padrão encontrados nas linguagens baseadas em C:

*   NÃO Lógico (`!a`)
    
*   E Lógico (`a && b`)
    
*   OU Lógico (`a || b`)
    

### Operador NÃO Lógico

O _operador NÃO lógico_ (`!a`) inverte um valor booleano de modo que `true` se torna `false`, e `false` se torna `true`.

O operador NÃO lógico é um operador prefixado, e aparece imediatamente ante do valor no qual se opera, sem nenhum espaço em branco. Ele pode ser lido como “não `a`”, como visto no seguinte exemplo:

```swift
let allowedEntry = false
if !allowedEntry {
    print("ACCESS DENIED")
}
// Imprime "ACCESS DENIED"
```

A frase `if !allowedEntry` pode ser lida como “se não permitida a entrada.” A linha subsequente só é executada se “entrada não permitida” for true; isto é, se `allowedEntry` for `false`.

Como neste exemplo, uma escolha cuidadosa dos nomes das variáveis e constantes Booleanas pode ajudar a manter o código legível e conciso, enquanto evita dupla negação ou declarações lógicas confusas.

### Operador E Lógico

O _operador E lógico_ (`a && b`) cria expressões lógicas onde ambos os valores devem ser `true` para a expressão como um todo também seja `true`.

Se qualquer valor for `false`, a expressão como um todo também será `false`. Na verdade, se o _primeiro_ valor for `false`, o segundo valor nem será avaliado, porque ele não é capaz de fazer com que toda a expressão seja igual a `true`. Isso é conhecido como _short-circuit evaluation_.

Este exemplo considera dois valores do tipo `Bool` e só permite acesso se ambos os valores forem `true`:

```swift
let enteredDoorCode = true
let passedRetinaScan = false
if enteredDoorCode && passedRetinaScan {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Imprime "ACCESS DENIED"
```

### Operador OU Lógico

O _operador OU lógico_ (`a || b`) é um operador _infix_ feito de duas barras verticais adjacentes. Você o utiliza para criar expressões lógicas nas quais apenas _um_ dos dois valores tem que ser `true` para a expressão como um todo ser `true`.

Como o operador E lógico acima, o operador OU lógico usa _short-circuit evaluation_ para considerar suas expressões. Se o lado esquerdo de uma expressão OU lógica for `true`, o lado direito não é avaliado, porque não pode mudar a saída da expressão como um todo.

No exemplo abaixo, o primeiro valor do tipo `Bool` (`hasDoorKey`) é `false`, mas o segundo valor (`knowsOverridePassword`) é `true`. Porque um valor é `true`, a expressão como um todo também é avaliada como `true`, e o acesso é permitido:

```swift
let hasDoorKey = false
let knowsOverridePassword = true
if hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Imprime "Welcome!"
```

### Combinando Operadores Lógicos

Você pode combinar múltiplos operadores lógicos para criar expressões compostas mais longas:

```swift
if enteredDoorCode && passedRetinaScan || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Imprime "Welcome!"
```

O exemplo acima usa múltiplos operadores `&&` e `||` para criar uma expressão composta mais longa. No entanto, os operadores `&&` e `||` ainda operam apenas dois valores, então isso realmente são três expressões menores encadeadas juntas: O exemplo pode ser lido como:

Se nós entrarmos o código certo da porta (`enteredDoorCode`) e passarmos no _scan_ de retina (`passedRetinaScan`), ou se nós tivermos uma chave da porta válida (`hasDoorKey`), ou se conhecermos a senha de acesso em caso de emergência (`knowsOverridePassword`), então permita o acesso.

Baseado nos valores de `enteredDoorCode`, `passedRetinaScan`, e `hasDoorKey`, as duas primeiras subexpressões são `false`. No entanto a senha de acesso em caso de emergência é conhecida, então toda a expressão composta ainda é avaliada como `true`.

**Nota**

> Os operadores lógicos do Swift `&&` e `||` são associativos à esquerda, significando que expressões compostas com múltiplos operadores lógicos avaliam primeiro a subexpressão mais a esquerda.

### Parênteses Explícitos

Ás vezes é útil incluir parênteses onde eles não estritamente necessários, para fazer com que uma expressão complexa seja mais fácil de ser lida. No exemplo acima da porta de acesso, é útil adicionar parênteses na primeira parte da expressão composta para fazer sua intenção explícita:

```swift
if (enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Imprime "Welcome!"
```

Os parênteses deixam claro que os primeiros dois valores são considerados como parte de um possível estado separado na lógica como um todo. A saída da expressão composta não muda, mas a intenção no geral é clara ao leitor. Legibilidade é sempre preferida acima de brevidade; use parênteses onde eles ajudem a deixar suas intenções claras.