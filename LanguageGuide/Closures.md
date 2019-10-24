
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

Se você precisa passar uma expressão *closure* como último argumento de uma função e esta expressão for grande, pode ser útil escrever ela como uma *trailing closure*. Uma *trailing closure* é escrita após os parênteses da chamada da função, apesar disso, a expressão continua pertencendo a função. Quando você utiliza a sintaxe *trailing closure*, você não escreve o nome externo que identifica a *closure* na chamada da função.


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

*Trailing closures* é muito útil quando a *closure* é grande e não é possível escrever em uma única expressão. Por exemplo, O tipo `Array` em Swift possui o método `map(_:)`, o qual possui uma *closure* como único argumento. A *closure* é chamada uma vez para cada item dentro do *array* e retorna um novo valor (possivelmente até mesmo de outro tipo). As transformações e o tipo retornado é especificado pelo corpo da *closure*. 

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

A *string* recebida do dicionário `digitNames` é adicionada no *início* de `output`, construindo a versão *string* do número ao contrário. (A expressão `number % 10` fornece os valores `6` para `16`, `8` para `58` e `0` para `50`).

A variável `number` é então dividida por `10`. Como ela é do tipo inteiro será arredondada para baixo durante a divisão, então `16` se torna `1`, `58` se torna `5` e etc.

O processo é repetido até `number` ficar igual a `0`, neste ponto a *string* `output` é retornada pela *closure* e adicionada ao *array* retornado pelo método `map(_:)`.

O uso da sintaxe *trailing closure* no exemplo citado encapsula a funcionalidade da *closure* imediatamente depois da função a qual a *closure* atua. 

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

Isto também significa que se você assinalar uma *closure* para duas constante ou variável diferentes, ambas vão apontar para a mesma *closure*.

```swift
let alsoIncrementByTen = incrementByTen
alsoIncrementByTen()
// retorna o valor 50 

incrementByTen()
// retorna o valor 60
```

O exemplo acima mostra a chamada de `alsoIncrementByTen` é o mesmo que chamar `incrementByTen`. Ambas se referem a mesma *closure*, as duas incrementa e retornam o mesmo valor total.

Escaping Closures
-----------------

A closure is said to *escape* a function when the closure is passed as an argument to the function, but is called after the function returns. When you declare a function that takes a closure as one of its parameters, you can write `@escaping` before the parameter’s type to indicate that the closure is allowed to escape.

One way that a closure can escape is by being stored in a variable that is defined outside the function. As an example, many functions that start an asynchronous operation take a closure argument as a completion handler. The function returns after it starts the operation, but the closure isn’t called until the operation is completed—the closure needs to escape, to be called later. For example:

```swift
var completionHandlers: [() -> Void] = []
func someFunctionWithEscapingClosure(completionHandler: @escaping () -> Void) {
    completionHandlers.append(completionHandler)
}
```

The `someFunctionWithEscapingClosure(_:)` function takes a closure as its argument and adds it to an array that’s declared outside the function. If you didn’t mark the parameter of this function with `@escaping`, you would get a compile-time error.

Marking a closure with `@escaping` means you have to refer to `self` explicitly within the closure. For example, in the code below, the closure passed to `someFunctionWithEscapingClosure(_:)` is an escaping closure, which means it needs to refer to `self` explicitly. In contrast, the closure passed to `someFunctionWithNonescapingClosure(_:)` is a nonescaping closure, which means it can refer to `self` implicitly.

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

An *autoclosure* is a closure that is automatically created to wrap an expression that’s being passed as an argument to a function. It doesn’t take any arguments, and when it’s called, it returns the value of the expression that’s wrapped inside of it. This syntactic convenience lets you omit braces around a function’s parameter by writing a normal expression instead of an explicit closure.

It’s common to *call* functions that take autoclosures, but it’s not common to *implement* that kind of function. For example, the `assert(condition:message:file:line:)` function takes an autoclosure for its `condition` and `message` parameters; its `condition` parameter is evaluated only in debug builds and its `message` parameter is evaluated only if `condition` is `false`.

An autoclosure lets you delay evaluation, because the code inside isn’t run until you call the closure. Delaying evaluation is useful for code that has side effects or is computationally expensive, because it lets you control when that code is evaluated. The code below shows how a closure delays evaluation.

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

Even though the first element of the `customersInLine` array is removed by the code inside the closure, the array element isn’t removed until the closure is actually called. If the closure is never called, the expression inside the closure is never evaluated, which means the array element is never removed. Note that the type of `customerProvider` is not `String` but `() -> String`—a function with no parameters that returns a string.

You get the same behavior of delayed evaluation when you pass a closure as an argument to a function.

```swift
// customersInLine is ["Alex", "Ewa", "Barry", "Daniella"]
func serve(customer customerProvider: () -> String) {
    print("Now serving \\(customerProvider())!")
}
serve(customer: { customersInLine.remove(at: 0) } )
// Prints "Now serving Alex!"
```

The `serve(customer:)` function in the listing above takes an explicit closure that returns a customer’s name. The version of `serve(customer:)` below performs the same operation but, instead of taking an explicit closure, it takes an autoclosure by marking its parameter’s type with the `@autoclosure` attribute. Now you can call the function as if it took a `String` argument instead of a closure. The argument is automatically converted to a closure, because the `customerProvider` parameter’s type is marked with the `@autoclosure` attribute.

```swift
// customersInLine is ["Ewa", "Barry", "Daniella"]
func serve(customer customerProvider: @autoclosure () -> String) {
    print("Now serving \(customerProvider())!")
}
serve(customer: customersInLine.remove(at: 0))
// Prints "Now serving Ewa!"
```

**Note**

>Overusing autoclosures can make your code hard to understand. The context and function name should make it clear that evaluation is being deferred.

If you want an autoclosure that is allowed to escape, use both the `@autoclosure` and `@escaping` attributes. The `@escaping` attribute is described above in [Escaping Closures](#escaping-closures).

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

In the code above, instead of calling the closure passed to it as its `customerProvider` argument, the `collectCustomerProviders(_:)` function appends the closure to the `customerProviders` array. The array is declared outside the scope of the function, which means the closures in the array can be executed after the function returns. As a result, the value of the `customerProvider` argument must be allowed to escape the function’s scope.