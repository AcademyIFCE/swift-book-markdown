# Swift Book

Esse projeto tem como objetivo traduzir e disponibilizar gratuitamente em português o livro *The Swift Programming Language (swift 5.1)*. 

## O que já pode ser traduzido

O livro em inglês está lentamente sendo migrado para o formato de *Markdown*  antes de ser traduzido. A seguintes *Sessões* já estão em formato *Markdown* e já podem ser traduzidas através de Pull Requests:

- [x] About Swift
- [x] Version Compatibility
- [x] A Swift Tour
  - [x] Intro
  - [x] Simple Values
  - [x] Control Flow
  - [x] Functions and Closures
  - [x] Objects and Classes
  - [x] Enumerations and Structures
  - [x] Protocols and Extensions
  - [x] Error Handling
  - [x] Generics
- [ ] Language Guide
  - [ ] The Basics
    - [x] Intro
    - [ ] Constants and Variables
    - [ ] Floating-Point Numbers
    - [ ] Type Safety and Type Inference
    - [ ] Numeric Type Conversion
    - [ ] Assertions and Preconditions
  - [x] Basic Operators
    - [x] Intro
    - [x] Terminology
    - [x] Assignment Operator
    - [x] Arithmetic Operators
    - [x] Compound Assignment Operators
    - [x] Comparison Operators
    - [x] Ternary Conditional Operator
    - [x] Nil-Coalescing Operator
    - [x] Range Operators
    - [x] Logical Operators
  - [ ] Strings And Characters
    - [ ] Intro
    - [ ] String Literals
    - [ ] Initializing an Empty String
    - [ ] String Mutability
    - [ ] Strings Are Value Types
    - [ ] Working with Characters
    - [ ] Concatenating Strings and Characters
    - [ ] String Interpolation
    - [ ] Unicode
    - [ ] Counting Characters
    - [ ] Accessing and Modifying a String
    - [ ] Substrings
    - [ ] Unicode
    - [ ] Comparing Strings
    - [ ] Unicode Representations of Strings
  - [ ] Collection Types
    - [ ] Intro
    - [ ] Mutability of Collections
    - [ ] Arrays
    - [ ] Sets
    - [ ] Performing Set Operations
    - [ ] Dictionaries
  - [ ] Control Flow
    - [ ] Intro
    - [ ] For-In Loops
    - [ ] While Loops
    - [ ] Conditional Statements
    - [ ] Control Transfer Statements
    - [ ] Early Exit
    - [ ] Checking API Availability
  - [ ] Functions
    - [ ] Intro
    - [ ] Defining and Calling Functions
    - [ ] Function Parameters and Return Values
    - [ ] Function Argument Labels and Parameter Names
    - [ ] Function Types
    - [ ] Nested Functions
  - [ ] Closures
    - [X] Intro
    - [X] Closure Expressions
    - [ ] Trailing Closures
    - [ ] Capturing Values
    - [X] Closures Are Reference Types
    - [X] Escaping Closures
    - [ ] Autoclosures
  - [ ] Enumerations
    - [ ] Intro
    - [ ] Enumeration Syntax
    - [ ] Matching Enumeration Values with a Switch Statement
    - [ ] Iterating over Enumeration Cases
    - [ ] Associated Values
    - [ ] Raw Values
    - [ ] Recursive Enumerations
  - [ ] Structures and Classes
    - [ ] Intro
    - [ ] Comparing Structures and Classes
    - [ ] Structures and Enumerations Are Value Types
    - [ ] Classes Are Reference Types
  - [ ] Properties
    - [x] Intro
    - [ ] Stored Properties
    - [ ] Computed Properties
    - [ ] Property Observers
    - [ ] Property Wrappers
    - [ ] Global and Local Variables
    - [ ] Type Properties
  - [ ] Methods
    - [ ] Intro
    - [ ] Instance Methods
    - [ ] Type Methods
  - [ ] Subscripts
    - [ ] Intro
    - [ ] Subscript Syntax
    - [ ] Subscript Usage
    - [ ] Subscript Options
    - [ ] Type Subscripts
  - [ ] Inheritance
    - [ ] Intro
    - [ ] Defining a Base Class
    - [ ] Subclassing
    - [ ] Overriding
    - [ ] Preventing Overrides
  - [ ] Initialization
    - [ ] Intro
    - [ ] Setting Initial Values for Stored Properties
    - [ ] Customizing Initialization
    - [ ] Default Initializers
    - [ ] Initializer Delegation for Value Types
    - [ ] Class Inheritance and Initialization
    - [ ] Failable Initializers
    - [ ] Required Initializers
    - [ ] Setting a Default Property Value with a Closure or Function
  - [ ] Deinitialization
    - [ ] Intro
    - [ ] How Deinitialization Works
    - [ ] Deinitializers in Action
  - [ ] Optional Chaining
    - [ ] Intro
    - [ ] Optional Chaining as an Alternative to Forced Unwrapping
    - [ ] Defining Model Classes for Optional Chaining
    - [ ] Accessing Properties Through Optional Chaining
    - [ ] Calling Methods Through Optional Chaining
    - [ ] Accessing Subscripts Through Optional Chaining
    - [ ] Linking Multiple Levels of Chaining
    - [ ] Chaining on Methods with Optional Return Values
  - [ ] Error Handling
    - [ ] Intro
    - [ ] Representing and Throwing Errors
    - [ ] Handling Errors
    - [ ] Specifying Cleanup Actions
  - [ ] Type Casting
    - [ ] Intro
    - [ ] Defining a Class Hierarchy for Type Casting
    - [ ] Checking Type
    - [ ] Downcasting
    - [ ] Type Casting for Any and AnyObject
    - [ ] Downcasting
  - [ ] Nested Types
    - [ ] Intro
    - [ ] Nested Types in Action
    - [ ] Referring to Nested Types
  - [ ] Extensions
    - [ ] Intro
    - [ ] Extension Syntax
    - [ ] Computed Properties
    - [ ] Initializers
    - [ ] Methods
    - [ ] Subscripts
    - [ ] Nested Types
  - [ ] Protocols
    - [ ] Intro
    - [ ] Protocol Syntax
    - [ ] Property Requirements
    - [ ] Method Requirements
    - [ ] Mutating Method Requirements
    - [ ] Initializer Requirements
    - [ ] Protocols as Types
    - [ ] Delegation
    - [ ] Adding Protocol Conformance with an Extension
    - [ ] Collections of Protocol Types
    - [ ] Protocol Inheritance
    - [ ] Class-Only Protocols
    - [ ] Protocol Composition
    - [ ] Checking for Protocol Conformance
    - [ ] Optional Protocol Requirements
    - [ ] Protocol Extensions
  - [ ] Generics
    - [x] Intro
    - [x] The Problem That Generics Solve
    - [x] Generic Functions
    - [ ] Type Parameters
    - [ ] Naming Type Parameters
    - [ ] Generic Types
    - [ ] Extending a Generic Type
    - [ ] Type Constraints
    - [ ] Associated Types
    - [ ] Generic Where Clauses
    - [ ] Extensions with a Generic Where Clause
    - [ ] Associated Types with a Generic Where Clause 
    - [ ] Generic Subscripts
  - [ ] Opaque Types
    - [ ] Intro
    - [ ] The Problem That Opaque Types Solve
    - [ ] Returning an Opaque Type
    - [ ] Differences Between Opaque Types and Protocol Types
  - [ ] Automatic Reference Counting
    - [ ] Intro
    - [ ] How ARC Works
    - [ ] ARC in Action
    - [ ] Strong Reference Cycles Between Class Instances
    - [ ] Resolving Strong Reference Cycles Between Class Instances
    - [ ] Strong Reference Cycles for Closures
    - [ ] Resolving Strong Reference Cycles for Closures
  - [ ] Memory Safety
    - [ ] Intro
    - [ ] Understanding Conflicting Access to Memory
    - [ ] Conflicting Access to In-Out Parameters
    - [ ] Conflicting Access to self in Methods
    - [ ] Conflicting Access to Properties
  - [ ] Access Control
    - [ ] Intro
    - [ ] Modules and Source Files
    - [ ] Access Levels
    - [ ] Access Control Syntax
    - [ ] Custom Types
    - [ ] Subclassing
    - [ ] Constants, Variables, Properties, and Subscripts 
    - [ ] Initializers
    - [ ] Protocols
    - [ ] Extensions
    - [ ] Generics
    - [ ] Type Aliases
  - [ ] Advanced Operators
    - [ ] Intro
    - [ ] Bitwise Operators
    - [ ] Overflow Operators
    - [ ] Precedence and Associativity
    - [ ] Operator Methods
    - [ ] Custom Operators
- [ ] Reference Manual
  - [ ] About The Language Reference

Cada item dessa lista terá uma Issue. **Antes de pegar um desses items para traduzir, verifique a Issue e descubra se alguém já não está traduzindo**. Quando alguém pegar uma dessas `sessao/topico` para traduzir, terá o nome atribuído a Issue.

## Convenções

Para facilitar o processo de revisão e diminuir as inconsistências entre traduções, quem contribuir deverá seguir algumas convenções:

* Não traduzir palavras reservadas.
* Na dúvida entre traduzir ou não determinado termo, deixar o termo em inglês.
* Criar Branches no padrão `sessao/topico`  e traduzir por *Sessao* e *Tópico* (textos mais internos dentro da *Sessão*).
* *Pull Requests* devem ser feitos para `master`, marcando a Issue que resolvem.

## Criação de Branches

A tradução deverá ser feita através de Forks, com branches nomeadas por sessão e tópico, com letras minúsculas, seguindo o seguinte padrão:

`nome-da-sessao/nome-do-topico`

Exemplo:
`a-swift-tour/control-flow`

Caso não existam tópicos para determinada sessão, a branch deve ter somente o nome da sessão:
`nome-da-sessao`

## Pull Requests

Os Pull Requests devem ser feitos diretamente para a branch `master`, e marcar a Issue que está resolvendo. A revisão será feita avaliando a tradução em si, a coerência do texto da tradução, e a coerência com as traduções anteriores.

## Começe Agora! 🎉  

Existe pouco ou nenhum material gratuito em português de Swift / Desenvolvimento iOS básico. Contribuindo com a tradução desse livro, você pode estar ajudando alguém que não tem $$$ para comprar material a estudar. Além disso, você mesmo estará estudando, revisando, e aprendendo recursos da linguagem que você talvez não conheça.

Com esforço coletivo, conseguiremos finalizar a tradução e facilitar o aprendizado de desenvolvimento iOS para quem não sabe inglês. 
