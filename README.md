# Swift Book

Esse projeto tem como objetivo traduzir e disponibilizar gratuitamente em português o livro _The Swift Programming Language (swift 5.3)_.

Cada item dessa lista terá uma Issue. **Antes de pegar um desses items para traduzir, verifique a Issue e descubra se alguém já não está traduzindo**. Quando alguém pegar uma dessas `sessao/topico` para traduzir, terá o nome atribuído a Issue.

## Convenções

Para facilitar o processo de revisão e diminuir as inconsistências entre traduções, quem contribuir deverá seguir algumas convenções:

- Não traduzir palavras reservadas.
- Na dúvida entre traduzir ou não determinado termo, deixar o termo em inglês.
- Criar Branches no padrão `sessao/topico` e traduzir por _Sessão_ e _Tópico_ (textos mais internos dentro da _Sessão_).
- _Pull Requests_ devem ser feitos para `master`, marcando a Issue que resolvem.

## Criação de Branches

A tradução deverá ser feita através de Forks, com branches nomeadas por sessão e tópico, com letras minúsculas, seguindo o seguinte padrão:

`nome-da-sessao/nome-do-topico`

Exemplo:
`a-swift-tour/control-flow`

Caso não existam tópicos para determinada sessão, a branch deve ter somente o nome da sessão:
`nome-da-sessao`

## Pull Requests

Os Pull Requests devem ser feitos diretamente para a branch `master`, e marcar a Issue que está resolvendo. A revisão será feita avaliando a tradução em si, a coerência do texto da tradução, e a coerência com as traduções anteriores.

## O que já pode ser traduzido

O livro em inglês está lentamente sendo migrado para o formato de _Markdown_ antes de ser traduzido. A seguintes _Sessões_ já estão em formato _Markdown_ e já podem ser traduzidas através de Pull Requests:

- [x] [About Swift](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/AboutSwift.md)
- [x] [Version Compatibility](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/Compatibility.md)
- [x] [A Swift Tour](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md)
  - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#uma-tour-pela-swift)
  - [x] [Simple Values](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#valores-simples)
  - [x] [Control Flow](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#controle-de-fluxo)
  - [x] [Functions and Closures](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#fun%C3%A7%C3%B5es-e-closures)
  - [x] [Objects and Classes](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#objetos-e-classes)
  - [x] [Enumerations and Structures](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#enumerations-and-structures)
  - [x] [Protocols and Extensions](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#protocolos-e-extens%C3%B5es)
  - [x] [Error Handling](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#tratamento-de-erros)
  - [x] [Generics](https://github.com/AcademyIFCE/Swift-Book/blob/master/GuidedTour/SwiftTour.md#generics)
- [ ] Language Guide
  - [ ] [The Basics](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#the-basics)
    - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#the-basics)
    - [x] [Constants and Variables](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#constants-and-variables)
    - [x] [Comments](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#coment%C3%A1rios)
    - [x] [Semicolons](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#ponto-e-v%C3%ADrgula)
    - [x] [Integers](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#integers)
    - [x] [Floating-Point Numbers](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#n%C3%BAmeros-de-ponto-flutuante)
    - [x] [Type Safety and Type Inference](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#type-safety-e-inferência-de-tipo)
    - [ ] Numeric Literals
    - [x] [Numeric Type Conversion](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/TheBasics.md#numeric-type-conversion)
    - [ ] Assertions and Preconditions
  - [x] [Basic Operators](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md)
    - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operadores-b%C3%A1sicos)
    - [x] [Terminology](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#terminologia)
    - [x] [Assignment Operator](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operador-de-atribui%C3%A7%C3%A3o)
    - [x] [Arithmetic Operators](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operadores-aritm%C3%A9ticos)
    - [x] [Compound Assignment Operators](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operadores-compostos-de-atribui%C3%A7%C3%A3o)
    - [x] [Comparison Operators](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operadores-de-compara%C3%A7%C3%A3o)
    - [x] [Ternary Conditional Operator](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operador-tern%C3%A1rio-condicional)
    - [x] [Nil-Coalescing Operator](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operador-nil-coalescing)
    - [x] [Range Operators](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operadores-de-intervalo)
    - [x] [Logical Operators](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/BasicOperators.md#operadores-l%C3%B3gicos)
  - [ ] Strings And Characters
    - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/StringsAndCharacters.md#strings-e-caracteres)
    - [x] [String Literals](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/StringsAndCharacters.md#literais-de-string)
    - [x] [Initializing an Empty String](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/StringsAndCharacters.md#initializing-an-empty-string)
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
    - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Closures.md#closures)
    - [x] [Closure Expressions](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Closures.md#express%C3%B5es-closure)
    - [ ] Trailing Closures
    - [ ] Capturing Values
    - [x] [Closures Are Reference Types](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Closures.md#closures-s%C3%A3o-reference-types)
    - [x] [Escaping Closures](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Closures.md#escaping-closures)
    - [ ] Autoclosures
  - [ ] Enumerations
    - [X] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Enumerations.md#enumera%C3%A7%C3%B5es)
    - [X] [Enumeration Syntax](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Enumerations.md#sintaxe-de-enumera%C3%A7%C3%B5es)
    - [X] [Matching Enumeration Values with a Switch Statement](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Enumerations.md#correspondendo-valores-de-enumera%C3%A7%C3%B5es-com-blocos-switch)
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
    - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Properties.md#propriedades)
    - [x] [Stored Properties](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Properties.md#propriedades-armazenadas)
    - [x] [Computed Properties](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Properties.md#propriedades-computadas)
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
    - [ ] Adopting a Protocol Using a Synthesized Implementation
    - [ ] Collections of Protocol Types
    - [ ] Protocol Inheritance
    - [ ] Class-Only Protocols
    - [ ] Protocol Composition
    - [ ] Checking for Protocol Conformance
    - [ ] Optional Protocol Requirements
    - [ ] Protocol Extensions
  - [ ] Generics
    - [x] [Intro](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Generics.md#generics)
    - [x] [The Problem That Generics Solve](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Generics.md#o-problema-que-generics-resolve)
    - [x] [Generic Functions](https://github.com/AcademyIFCE/Swift-Book/blob/master/LanguageGuide/Generics.md#fun%C3%A7%C3%B5es-generic)
    - [ ] Type Parameters
    - [ ] Naming Type Parameters
    - [ ] Generic Types
    - [ ] Extending a Generic Type
    - [ ] Type Constraints
    - [ ] Associated Types
    - [ ] Generic Where Clauses
    - [ ] Extensions with a Generic Where Clause
    - [ ] Contextual Where Clauses
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
  - [ ] Lexical Structure
    - [ ] Intro
    - [ ] Whitespace and Comments
    - [ ] Identifiers
    - [ ] Keywords and Punctuation
    - [ ] Literals
    - [ ] Operators
  - [ ] Types
    - [ ] Intro
    - [ ] Type Annotation
    - [ ] Type Identifier
    - [ ] Tuple Type
    - [ ] Function Type
    - [ ] Array Type
    - [ ] Dictionary Type
    - [ ] Optional Type
    - [ ] Implicitly Unwrapped Optional Type
    - [ ] Protocol Composition Type
    - [ ] Opaque Type
    - [ ] Metatype Type
    - [ ] Self Type
    - [ ] Type Inheritance Clause
    - [ ] Type Inference
  - [ ] Expressions
    - [ ] Intro
    - [ ] Prefix Expressions
    - [ ] Binary Expressions
    - [ ] Primary Expressions
    - [ ] Postfix Expressions
  - [ ] Statements
    - [ ] Intro
    - [ ] Loop Statements
    - [ ] Branch Statements
    - [ ] Labeled Statement
    - [ ] Control Transfer Statements
    - [ ] Defer Statement
    - [ ] Do Statement
    - [ ] Compiler Control Statements
    - [ ] Availability Condition
  - [ ] Declarations
    - [ ] Intro
    - [ ] Top-Level Code
    - [ ] Code Blocks
    - [ ] Import Declaration
    - [ ] Constant Declaration
    - [ ] Variable Declaration
    - [ ] Type Alias Declaration
    - [ ] Function Declaration
    - [ ] Enumeration Declaration
    - [ ] Structure Declaration
    - [ ] Class Declaration
    - [ ] Protocol Declaration
    - [ ] Initializer Declaration
    - [ ] Deinitializer Declaration
    - [ ] Extension Declaration
    - [ ] Subscript Declaration
    - [ ] Operator Declaration
    - [ ] Precedence Group Declaration
    - [ ] Declaration Modifiers
  - [ ] Attributes
    - [ ] Intro
    - [ ] Declaration Attributes
    - [ ] Type Attributes
    - [ ] Switch Case Attributes
  - [ ] Patterns
    - [ ] Intro
    - [ ] Wildcard Pattern
    - [ ] Identifier Pattern
    - [ ] Value-Binding Pattern
    - [ ] Tuple Pattern
    - [ ] Enumeration Case Pattern
    - [ ] Optional Pattern
    - [ ] Type-Casting Patterns
    - [ ] Expression Pattern
  - [ ] Generic Parameters and Arguments
    - [ ] Intro
    - [ ] Generic Parameter Clause
    - [ ] Generic Argument Clause

## Começe Agora! 🎉

Existe pouco ou nenhum material gratuito em português de Swift / Desenvolvimento iOS básico. Contribuindo com a tradução desse livro, você pode estar ajudando alguém que não tem \$\$\$ para comprar material a estudar. Além disso, você mesmo estará estudando, revisando, e aprendendo recursos da linguagem que você talvez não conheça.

Com esforço coletivo, conseguiremos finalizar a tradução e facilitar o aprendizado de desenvolvimento iOS para quem não sabe inglês.
