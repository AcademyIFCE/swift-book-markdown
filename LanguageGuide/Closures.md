
 Closures
 
 Closures
 ========

*Closures* são blocos auto-contidos de código que podem ser passadas e utilizadas no seu código. *Closures* em Swift são similares a blocos em C/Objective-C e a *lambdas* em outras linguagem de programação.
 
*Closures* podem capturar e armazenar referências de qualquer constante e variável do contexto no qual ele foi definido. Isto é conhecido como *closing over* de constantes e variáveis. Swift cuida de todo o gerenciamento de memória para você.
 

 **Nota**

 > Não se preocupe se você não está acostumado com o conceito de captura. Isto é explicado em detalhes mais abaixo em  [Capturando Valores](#capturing-values).

 *Global* e *Nested functions* , como introduzido em [Funções](Functions.md), são na realidade um tipo especial de *closures*. *Closures* assumem três formas:

 *   *Global Function* são *closures* que possuem nome e não podem capturar nenhum valor.
     
 *   *Nested functions* são *closures* que possuem nome e podem capturar valores da função que a engloba.
     
 *   *Expressões Closure* não possuem nome e escritas em sintaxe mais simplificada que pode capturar valores do contexto onde é declarada.
     

 *Expressões Closure* em Swift possuem uma escrita limpa e clara, com otimizações que incentivam uma sintaxe enxuta nos cenários mais comuns. Estas otimizações incluem:

 *   Inferir parâmetros e tipos de retorno do contexto
     
 *   Tipo de retorno implícito quando o corpo da *closure* possui apenas uma linha
 
 
Expressões Closure
=======

*Nested functions*, como introduzido em [Nested Functions](Functions.md#nested-functions), é um modo conveniente de nomear e definir blocos auto-contidos de código como parte de uma função maior. Entretanto, algumas vezes é útil escrever uma versão mais curta da estrutura similiar a funções sem a sua declaração completa e nome. Isto é bastante usado quando vocˆ3 trabalha com funções ou métodos que recebem outras funções como parâmetro.
 
*Expressões Closure* é uma maneira de escrever *closures* de modo enxuto e com sintaxe simples. *Expressões Closure* fornecem várias otimizações de sintaxe para a escrita de *closures*  de forma resumida sem perder clareza. Os exemplos abaixo ilustram estas otimizações utilizando o método `sorted(by:)`, onde em todos os casos realizam a mesmas ação, porém com escrita cada vez mais sucinta.
 
### O Método Sorted

A biblioteca padrão do Swift fornece um método chamado `sorted(by:)`, o qual ordena os valores de um *array* baseado no retorno da *closure* de ordenação. Ao completar o processo de ordenação, o método `sorted(by:)` retorna um novo *array* do mesmo tipo e tamanho do antigo, porém com os elementos com a ordem de acordo com o requisitado. O *array* original não é modificado pelo método. 

O exemplo abaixo usa o método `sorted(by:)` para ordenar um *array* de `String` na ordem contrária a alfabética. Este é o *array* inicial:

```swift
let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
```

O método `sorted(by:)` recebe uma *closure* que possui dois argumentos do mesmo tipo do *array* e retorna um `Bool` que indica quando o primeiro valor deve ficar antes ou depois do segundo valor quando o *array* estiver reordenado. A *closure* deve retornar `true` se o primeiro valor deva ficar *antes* do segundo valor e `false` caso o contrário seja desejado.

Este exemplo esta ordenando um *array* de `String` então a *closure* de ordenação precisa ser uma função do tipo `(String, String) -> Bool`.

Um dos modos de fornecer uma *closure* é escrevendo uma função normal do tipo esperado pelo parâmetro e então passar como argumento do método `sorted(by:)`:

```swift
func backward(_ s: String, _ s2: String) -> Bool {
    return s > s2
}
var reversedNames = names.sorted(by: backward)
// reversedNames é igual a ["Ewa", "Daniella", "Chris", "Barry", "Alex"]
```

Se a primeira string (`s`) for maior que a segunda string (`s2`) a função `backward(_:_:)` irá retornar `true`, fazendo com que `s` fique antes de `s2` no *array* ordenado. Em relação a caracteres em uma string, "maior que" significa "estar a frente na ordem alfabética que". Isto significa que a letra `"B"` é "maior que" a letra `"A"`, logo `"Tom"` é maior que a string `"Tim"`. Por isso, em uma ordenação contrária da ordem alfabética `"Barry"` fica antes de `"Alex"`. 

Entretanto, este é um modo verboso de escrever uma simples expressão (`a > b`). Neste exemplo, seria mais adequado escrever uma expressão simplificada usando a sintaxe de Expressões *Closure*.

### Sintaxe de Expressões *Closure*

Sintaxe de Expressões *Closure* possui a seguinte forma:

>{ (parameters) -> return type in
>
>statements
>
>}

Os *parâmetros* em uma expressão *closure* podem ser do tipo *in-out*, porém não podem possuir um valor padrão. Parâmetros *variadic* podem ser utilizado caso você adicione um nome ao argumento. Tuplas também podem ser utilizadas como tipos de parâmetros e retorno.

O exemplo abaixo mostra uma expressão *closure* que implementa o mesmo que a função `backward(_:_:)`, mostrada acima:

```swift
reversedNames = names.sorted(by: { (s: String, s2: String) -> Bool in
    return s > s2
})
```

Perceba que a declaração dos parâmetros e tipo de retorno para este tipo de *closure* é idêntica a declaração da função `backward(_:_:)`. Em ambos os casos, foi escrito como `(s: String, s2: String) -> Bool`. Entretanto, para a expressão *closure* mais simples, os tipos de parâmetros e retorno são escritos *dentro* das chaves.

O início do corpo da *closure* é iniciado pela palavra reservada `in`. Esta palavra reservada indica que a definição dos parâmetros e retorno da *closure* terminaram, e o que o corpo da *closure* esta prestes a começar.

Como o corpo da *closure* é pequeno, é possível até escrever ele em uma única linha:

```swift
reversedNames = names.sorted(by: { (s: String, s2: String) -> Bool in return s > s2 } )
```

Isto ilustra  que a chamada do método `sorted(by:)` continua a mesma. Um par de parênteses continua envolvendo todos os argumentos do método. Porém, este argumento agora é uma *closure*.

### Inferindo Tipos do Contexto

Em razão da *closure* ser passada como um argumento para o método, o Swift pode inferir os tipos de seus parâmetros e retorno. O método `sorted(by:)` é chamado de um *array* de *strings*, então o argumento deve ser uma função do tipo `(String, String) -> Bool`. Isto significa que os tipos `(String, String)` e `Bool` não precisam ser explicitamente escritos na definição de uma expressão closure. Todos os tipos podem ser inferidos, a seta de retorno (`->`) e os parênteses ao redor do nome dos parâmetros também podem ser omitidos:

```swift
reversedNames = names.sorted(by: { s, s2 in return s > s2 } )
```

É sempre possível inferir os tipos dos parâmetros e do retorno quando passamos uma *closure* para uma função ou método. Por conta disto você nunca precisa escrever uma *closure* diretamente na função na sua forma completa quando ela é passada como função ou parâmetro de um método.

No entanto, você ainda pode explicitar os tipos se você quiser, e é interessante fazê-lo se isto for evitar ambiguidade para os leitores do código. No caso da *closure* do método `sorted(by:)` é claro que na sua implementação é onde a ordenação de fato acontece, e é seguro para o leitor assumir que os parâmetros da *closure* são do tipo `String` já que o *array* que esta sendo ordenado possui elementos do tipo `String`.

### Retorno Implícito de *Closures* de Única Expressão

*Closures* de Única Expressão retorna o resultado da instrução omitindo a palavra reservada `return` na declaração, como está no exemplo abaixo:

```swift
reversedNames = names.sorted(by: { s, s2 in s > s2 } )
```

Neste exemplo o tipo do parametro do método `sorted(by:)` deixa claro que o tipo do retorno é `Bool`. Como o corpo da *closure* contém apenas uma expressão (`s > s2`) que já retorna um valor do tipo `Bool`, não há ambiguidade e por conta disso pode-se omitir a palavra reservada `return`.

### Argumentos com nomes abreviados

O Swift automaticamente fornece argumentos com nomes abreviados para *closures* escritas diretamente, neste caso é possível acessar os valores dos parâmetros da *closures* utilizando nomes `$0`, `$1`, `$2` e etc.

Se você utilizar este tipo de nomenclatura de argumentos na sua *closure*, você pode omitir a lista de parâmetros durante a sua implementação, assim o número e tipo do argumento será inferido de acordo com a assinatura da *closure*. A palavra reservada `in` também pode ser omitida.

```swift
reversedNames = names.sorted(by: { $0 > $1 } )
```
No exemplo acima `$0` and `$1` fazem referência ao primeiro e segundo parâmetro da *closure* respectivamente. 

### Operator Methods

Há ainda uma maneira mais enxuta de escrever o mesmo exemplo acima. Em Swift o tipo `String` define a implementação do operador Maior Que (`>`) como um método que tem dois parâmetros do tipo `String` e que retorna um valor do tipo `Bool`. Deste modo é possível passar este método diretamente para o método `sorted(by:)`. Por conta disto, você pode simplesmente passar o operador (`>`) e a linguagem irá inferir que você deseja passar a implementação contido no tipo `String`:


```swift
reversedNames = names.sorted(by: >)
```

Para mais sobre métodos operadores, veja [Métodos Operadores](AdvancedOperators.md#operator-methods).

*Trailing Closures*
-----------------

Se você precisa passar uma expressão *closure* como último argumento de uma função e esta expressão for grande, pode ser útil escrever ela como uma *trailing closure*. Uma *trailing closure* é escrita após os parênteses da chamada da função, apesar disso, a expressão continua pertencendo a função. Quando você utiliza a sintaxe *trailing closure*, você não escreve o nome externo que identifica a *closure* na chamada da função. Uma chamada de função pode incluir vários *trailing closures*; no entanto, os primeiros exemplos abaixo usam uma única *trailing closure*


```swift
func someFunctionThatTakesAClosure(closure: () -> Void) {
    // corpo da função
}

// Chamando a função sem utilizar *trailing closure*: 

someFunctionThatTakesAClosure(closure: {
    // corpo da closure
})

// Chamada de função utilizando *trailing closure*:

someFunctionThatTakesAClosure() {
    // corpo da closure
}
```

A *closure* do método `sorted(by:)` visto em [Sintaxe Expressão *Closure*](#closure-expression-syntax) pode ser escrita de modo *trailing closure*:

```swift
reversedNames = names.sorted() { $0 > $1 }
```

Se a expressão *closure* é o único argumento do método e você utiliza *trailing closure*, você não precisa escrever os parênteses depois do nome do método/função quando você chama a função:

```swift
reversedNames = names.sorted { $0 > $1 }
```

*Trailing closures* é muito útil quando a *closure* é grande e não é possível escrever em uma única expressão. Por exemplo, O tipo `Array` em Swift possui o método `map(_:)`, o qual possui uma *closure* como único argumento. A *closure* é chamada uma vez para cada item dentro do *array* e retorna um novo valor (possivelmente até mesmo de outro tipo). Você especifica a natureza do mapeamento e o tipo do valor que será retornado escrevendo o código na *closure* que você for passar no método `map(_:)`.

Depois de aplicar as transformações fornecidas pela *closure* em cada elemento do *array*, o método `map(_:)` retorna um novo *array* contendo todos os novos elementos transformados na mesma ordem correspondente ao seus valores originais. 

Aqui está um exemplo de como usar o método `map(_:)` com uma *trailing closure* para converter uma *array* de `Int` em `String`. O *array* `[16,58,50]` é usado para a criação do novo *array* `["OneSix", "FiveEight", "FiveOneZero"]`:

```swift
let digitNames = [
    0: "Zero", 1: "One", 2: "Two", 3: "Three", 4: "Four",
    5: "Five", 6: "Six", 7: "Seven", 8: "Eight", 9: "Nine"
]
let numbers = [16, 58, 510]
```

O código acima cria um dicionário que mapeia números inteiros e o número extenso em inglês. Também define um *array* de inteiros preparado para ser convertido em *strings*.

Agora você pode utilizar o *array* `numbers` para criar um outro *array* de `String` passando como parâmetro esta *trailing closure* para o método `map(_:)`:

```swift
let strings = numbers.map { (number) -> String in
    var number = number
    var output = ""
    repeat {
        output = digitNames[number % 10]! + output
        number /= 10
    } while number > 0
        return output
}
// *strings* são inferidos para serem do tipo [String]
// o *array* é ["OneSix", "FiveEight", "FiveOneZero"]
```

O método `map(_:)` chama a *closure* uma vez para cada item do *array*. Você não precisa especificar o tipo do parâmetro da *closure*, `number`, pois o tipo pode ser inferido dos elementos do *array* a ser mapeado.

Neste exemplo, a variável `number` é inicializada com o valor do parâmetro da *closure* `number`, só então este valor pode ser modificado dentro do corpo da *closure*. (Parâmetros de *closures* e funções são sempre constantes.) A expressão *closure* especifica o tipo de retorno `String` para indicar que o tipo que será armazenado no *array* retornado

A expressão *closure* constrói uma *string* chamada `output` cada vez que ela é chamada. Ele calcula o último digito de `number` usando o operador de resto (`number % 10`) e usar este valor para achar a *string* apropriada no dicionário `digitNames`. A *closure* ode ser usada para criar uma representação *string* de qualquer inteiro maior que zero.

**Nota**

>A chamada do *subscript* do dicionário `digitNames` possui um (`!`) porquê o *subscript* do dicionário retorna um valor *optional* para indicar que o valor daquela chave pode não existir. No exemplo acima é garantido que `number % 10` sempre irá gerar uma chave válida para o dicionário `digitNames`, então o ponto de exclamação é utilizado para realizar um *force-unwrap* do valor daquela chave.

A *string* recebida do dicionário `digitNames` é adicionada no *início* de `output`, construindo a versão *string* do número ao contrário. (A expressão `number % 10` fornece os valores `6` para `16`, `8` para `58` e `0` para `510`).

A variável `number` é então dividida por `10`. Como ela é do tipo inteiro será arredondada para baixo durante a divisão, então `16` se torna `1`, `58` se torna `5` e `510` se torna `51`.

O processo é repetido até `number` ficar igual a `0`, neste ponto a *string* `output` é retornada pela *closure* e adicionada ao *array* retornado pelo método `map(_:)`.

O uso da sintaxe *trailing closure* no exemplo citado encapsula a funcionalidade da *closure* imediatamente depois da função a qual a *closure* atua. 

Se uma função aceita várias *closures*,   if a function takes multiple closures, you omit the argument label for the first trailing closure and you label the remaining trailing closures. For example, the function below loads a picture for a photo gallery:,você omite a *label* do argumento da primeira *closure* mais à direita e deixa a *label* das *closures* à direita restantes. Por exemplo, a função abaixo carrega uma imagem para uma galeria de fotos:

```swift
func loadPicture(from server: Server, completion: (Picture) -> Void, onFailure: () -> Void) {
    if let picture = download("photo.jpg", from: server) {
        completion(picture)
    } else {
        onFailure()
    }
}
```

Quando você chama essa função para carregar uma imagem, você precisa fornecer duas *closures*. A primeira *closure*  é uma *completion handler* que exibe uma imagem após um download bem-sucedido. A segunda *closure* é um *error handler* que exibe um erro para o usuário.

```swift
loadPicture(from: someServer) { picture in
    someView.currentPicture = picture
} onFailure: {
    print("Não foi possível baixar a próxima imagem.")
}
```

In this example, the `loadPicture(from:completion:onFailure:)` function dispatches its network task into the background, and calls one of the two completion handlers when the network task finishes. Writing the function this way lets you cleanly separate the code that’s responsible for handling a network failure from the code that updates the user interface after a successful download, instead of using just one closure that handles both circumstances.

Neste exemplo, a função `loadPicture (from: completed: onFailure:)` despacha sua tarefa de *network* para o *background* e chama uma das duas *completion handlers* essa tarefa de *network* termina. Escrever a função dessa forma permite separar claramente o código responsável por lidar com uma falha de *network* do código que atualiza a interface do usuário após um *download* bem-sucedido, em vez de usar apenas uma *closure* para lidar com essas duas situações.

Capturing Values
----------------

A closure can *capture* constants and variables from the surrounding context in which it is defined. The closure can then refer to and modify the values of those constants and variables from within its body, even if the original scope that defined the constants and variables no longer exists.

In Swift, the simplest form of a closure that can capture values is a nested function, written within the body of another function. A nested function can capture any of its outer function’s arguments and can also capture any constants and variables defined within the outer function.

Here’s an example of a function called `makeIncrementer`, which contains a nested function called `incrementer`. The nested `incrementer()` function captures two values, `runningTotal` and `amount`, from its surrounding context. After capturing these values, `incrementer` is returned by `makeIncrementer` as a closure that increments `runningTotal` by `amount` each time it is called.

```swift
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runningTotal = 0
    func incrementer() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incrementer
}
```

The return type of `makeIncrementer` is `() -> Int`. This means that it returns a *function*, rather than a simple value. The function it returns has no parameters, and returns an `Int` value each time it is called. To learn how functions can return other functions, see [Function Types as Return Types](Functions.md#function-types-as-return-types).

The `makeIncrementer(forIncrement:)` function defines an integer variable called `runningTotal`, to store the current running total of the incrementer that will be returned. This variable is initialized with a value of `0`.

The `makeIncrementer(forIncrement:)` function has a single `Int` parameter with an argument label of `forIncrement`, and a parameter name of `amount`. The argument value passed to this parameter specifies how much `runningTotal` should be incremented by each time the returned incrementer function is called. The `makeIncrementer` function defines a nested function called `incrementer`, which performs the actual incrementing. This function simply adds `amount` to `runningTotal`, and returns the result.

When considered in isolation, the nested `incrementer()` function might seem unusual:

```swift
func incrementer() -> Int {
    runningTotal += amount
    return runningTotal
}
```

The `incrementer()` function doesn’t have any parameters, and yet it refers to `runningTotal` and `amount` from within its function body. It does this by capturing a *reference* to `runningTotal` and `amount` from the surrounding function and using them within its own function body. Capturing by reference ensures that `runningTotal` and `amount` do not disappear when the call to `makeIncrementer` ends, and also ensures that `runningTotal` is available the next time the `incrementer` function is called.

**Note**

>As an optimization, Swift may instead capture and store a *copy* of a value if that value is not mutated by a closure, and if the value is not mutated after the closure is created.
>
>Swift also handles all memory management involved in disposing of variables when they are no longer needed.

Here’s an example of `makeIncrementer` in action:

```swift
let incrementByTen = makeIncrementer(forIncrement: 0)
```

This example sets a constant called `incrementByTen` to refer to an incrementer function that adds `0` to its `runningTotal` variable each time it is called. Calling the function multiple times shows this behavior in action:

```swift
incrementByTen()
// returns a value of 0
incrementByTen()
// returns a value of 20
incrementByTen()
// returns a value of 30
```

If you create a second incrementer, it will have its own stored reference to a new, separate `runningTotal` variable:

```swift
let incrementBySeven = makeIncrementer(forIncrement: 7)
incrementBySeven()
// returns a value of 7
```

Calling the original incrementer (`incrementByTen`) again continues to increment its own `runningTotal` variable, and does not affect the variable captured by `incrementBySeven`:

```swift
incrementByTen()
// returns a value of 40
```

**Note**

>If you assign a closure to a property of a class instance, and the closure captures that instance by referring to the instance or its members, you will create a strong reference cycle between the closure and the instance. Swift uses *capture lists* to break these strong reference cycles. For more information, see [Strong Reference Cycles for Closures](AutomaticReferenceCounting.xhtml#strong-reference-cycles-for-closures).

*Closures* São *Reference Types*
----------------------------

No exemplo acima, `incrementBySeven` e `incrementByTen` são constantes, mas a *closure* para qual estas constantes apontam ainda podem incrementar a variável `runningTotal` que elas capturaram. Isto ocorre porque *closures* e funções são *reference types*. 

Sempre quando você assinalar uma função ou *closure* para uma constante ou variável, vocês está na verdade fazendo com que a constante ou variável seja uma referência para a função/*closure*. No exemplo acima, a *closure* `incrementByTen` aponta para a constante e não para o conteúdo da *closure* em si.

Isto também significa que se você assinalar uma *closure* para duas constantes ou variáveis diferentes, ambas vão apontar para a mesma *closure*.

```swift
let alsoIncrementByTen = incrementByTen
alsoIncrementByTen()
// retorna o valor 50 

incrementByTen()
// retorna o valor 60
```

O exemplo acima mostra a chamada de `alsoIncrementByTen` é o mesmo que chamar `incrementByTen`. Ambas se referem a mesma *closure*, as duas incrementam e retornam o mesmo valor total.

*Escaping Closures*
-----------------

Diz-se que uma *closure* *escape* uma função quando ela é passada como argumento para uma função, mas é chamada apenas depois do seu retorno. Quando você declara uma função que recebe uma *closure* como um dos seus parâmetros, você escrever `@escaping` antes do tipo do parâmetro para indicar que a *closure* pode ser *escape*.

Uma vez que uma *closure* pode ser *escape* ela é armazenada em uma variável que é definida fora da função. Por exemplo, várias funções que iniciam uma operação assíncrona recebe uma closure como argumento para ser executada ao fim do processamento. A função retorna depois do início da operação, mas a *closure* não é executada até a operação ser completada. A *closure* precisa ser *escape* para ser chamada posteriormente. Por exemplo:

```swift
var completionHandlers: [() -> Void] = []
func someFunctionWithEscapingClosure(completionHandler: @escaping () -> Void) {
    completionHandlers.append(completionHandler)
}
```

A função `someFunctionWithEscapingClosure(_:)` recebe uma *closure* como seu argumento e adiciona a um *array* declarado fora da função. Se você não marcar o parâmetro desta função como `@escaping` você terá uma erro em tempo de compilação.

Marcar uma *closure* como `@escaping` significa que você tem que se referir a `self` de maneira explícita dentro da *closure*. Por exemplo, no código abaixo, a *closure* passada para `someFunctionWithEscapingClosure(_:)` é uma *escaping closure*, o que significa que precisa se referir a `self` explicitamente. Por outro lado, a *closure* passada para `someFunctionWithNonescapingClosure(_:)` é uma *nonescaping closure*, o que siginfica que ela pode se referir a `self` de maneira implícita.

```swift
func someFunctionWithNonescapingClosure(closure: () -> Void) {
    closure()
}

class SomeClass {
    var x = 0
    func doSomething() {
        someFunctionWithEscapingClosure { self.x = 100 }
        someFunctionWithNonescapingClosure { x = 200 }
    }
}

let instance = SomeClass()
instance.doSomething()
print(instance.x)
// Prints "200"

completionHandlers.first?()
print(instance.x)
// Prints "100"
```

Autoclosures
------------

Uma *autoclosure* é uma closure que é automaticamente criada para embrulhar uma expressão que está sendo passada como argumento para a função. Ela não requer qualquer argumento, e quando é chamada, retorna o valor da expressão que está embrulhada dentro de si. Essa conveniência sintática permite omitir as chaves ao redor do parâmetro da função, escrevendo uma expressão normal ao invés de uma closure explicita.

É comum *fazer a chamada* de funções que recebem *autoclosures*, mas não é comum *implementar* esse tipo de função. Por exemplo, a função `assert(condition:message:file:line)` recebe uma autoclosure para os parâmetros `condition` e `message`; o parâmetro `condition` é executado somente em debug builds e o parâmetro `message` é executado somente se `condition` é `false`.

Uma autoclosure permite que você atrase sua execução, porque o código dentro dele não é executado até que você faça a chamada da closure. Atrasar a execução é útil para códigos que tem efeitos colaterais ou demandam muito poder computacional, porque permite que você controle quando este código é executado. O código abaixo mostra como uma closure atrasa a execução.

```swift
var customersInLine = \["Chris", "Alex", "Ewa", "Barry", "Daniella"\]
print(customersInLine.count)
// Prints "5"

let customerProvider = { customersInLine.remove(at: 0) }
print(customersInLine.count)
// Prints "5"

print("Now serving \\(customerProvider())!")
// Prints "Now serving Chris!"
print(customersInLine.count)
// Prints "4"
```

Apesar de o primeiro elemento do array `customersInLine` ser removido pelo código dentro da closure, o elemento do array não é removido até que a closure seja realmente chamada. Se a closure nunca é chamada, a expressão dentro da closure nunca é executada, o que significa que o elemento do array nunca é removido. Note que o tipo de `customerProvider` não é `String` mas `( ) -> String`- uma função sem parâmetros que retorna uma string.

Você tem o mesmo comportamento da execução atrasada quando você passa a closure como um argumento para a função.

```swift
// customersInLine is ["Alex", "Ewa", "Barry", "Daniella"]
func serve(customer customerProvider: () -> String) {
    print("Now serving \\(customerProvider())!")
}
serve(customer: { customersInLine.remove(at: 0) } )
// Prints "Now serving Alex!"
```

A função `serve(customer:)` na listagem acima recebe uma closure explícita que retorna o nome do cliente. A versão de `serve(customer:)` abaixo executa a mesma operação mas, ao invés de receber uma closure explícita, ela recebe uma autoclosure marcando o tipo desse parâmetro com o atributo `@autoclosure`. Agora você pode chamar a função como se ela recebesse um parâmetro `String` ao invés de uma closure. O argumento é automaticamente convertido para uma closure, porque o tipo do parâmetro `customerProvider` está marcado com o atributo `@autoclosure`.

```swift
// customersInLine is ["Ewa", "Barry", "Daniella"]
func serve(customer customerProvider: @autoclosure () -> String) {
    print("Now serving \(customerProvider())!")
}
serve(customer: customersInLine.remove(at: 0))
// Prints "Now serving Ewa!"
```

**Nota**

>Usar muitas autoclosures pode fazer seu código difícil de entender. O contexto e o nome da função devem deixar claros que sua execução está sendo adiada.

Se você quiser uma autoclosure que o escape é permitido, use os atributos `@autoclosure` e `@escaping`. O atributo `@escaping` é descrito acima em [Escaping Closures](#escaping-closures).

```swift
// customersInLine is ["Barry", "Daniella"]
var customerProviders: [() -> String] = []
func collectCustomerProviders(_ customerProvider: @autoclosure @escaping () -> String) {
    customerProviders.append(customerProvider)
}
collectCustomerProviders(customersInLine.remove(at: 0))
collectCustomerProviders(customersInLine.remove(at: 0))

print("Collected \(customerProviders.count) closures.")
// Prints "Collected 2 closures."
for customerProvider in customerProviders {
    print("Now serving \(customerProvider())!")
}
// Prints "Now serving Barry!"
// Prints "Now serving Daniella!"
```

No código acima, ao invés de chamar a closure passada para ela como o argumento `customerProvider`, a função `collectCustomProviders` adiciona a closure no array `customerProviders`. O array é declarado fora do escopo da função, o que significa que as closures no array podem ser executadas após o retorno da função. Como resultado, o valor do argumento `customerProvider` deve ser permitido de escapar do escopo da função.
