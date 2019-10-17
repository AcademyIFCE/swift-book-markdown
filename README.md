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
- [ ] The Basics
  - [ ] Intro
  - [ ] Constants and Variables
  - [ ] Floating-Point Numbers (Minusculo)
  - [ ] Type Safety and Type Inference(Pequeno)
  - [ ] Numeric Type Conversion (Gigante)
  - [ ] Assertions and Preconditions
- [X] Basic Operators
  - [X] Operadores Básicos
  - [X] Terminologia
  - [X] Operador de Atribuição
  - [X] Operadores Aritméticos
  - [X] Operadores Compostos de Atribuição
  - [X] Operador Ternário Condicional
  - [X] Operador de Coalescência Nula
  - [X] Operadores de Intervalo
  - [X] Operadores Lógicos
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
- [ ] Closures
  - [ ] Intro
  - [ ] Closure Expressions
  - [ ] Trailing Closures
  - [ ] Capturing Values
  - [ ] Closures Are Reference Types
  - [ ] Escaping Closures
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
- [ ] Methods
  - [ ] Intro
  - [ ] Instance Methods
  - [ ] Type Methods
- [ ] Nested Types
  - [ ] Intro
  - [ ] Nested Types in Action
  - [ ] Referring to Nested Types
- [ ] Generics
  - [x] Intro
  - [ ] The Problem That Generics Solve
  - [ ] Generic Functions
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
