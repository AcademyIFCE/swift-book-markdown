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

- [x] [Sobre Swift](GuidedTour/AboutSwift.md)
- [x] [Compatibilidade de Versão](GuidedTour/Compatibility.md)
- [x] [Um tour de Swift](GuidedTour/SwiftTour.md)
  - [x] [Introdução](GuidedTour/SwiftTour.md#uma-tour-pela-swift)
  - [x] [Valores Simples](GuidedTour/SwiftTour.md#valores-simples)
  - [x] [Controle de Fluxo](GuidedTour/SwiftTour.md#controle-de-fluxo)
  - [x] [Funções e closures](GuidedTour/SwiftTour.md#fun%C3%A7%C3%B5es-e-closures)
  - [x] [Objetos e classes](GuidedTour/SwiftTour.md#objetos-e-classes)
  - [x] [Enumerações e Estruturas](GuidedTour/SwiftTour.md#enumerations-and-structures)
  - [x] [Protocolos e Extensões](GuidedTour/SwiftTour.md#protocolos-e-extens%C3%B5es)
  - [x] [Tratamento de erros](GuidedTour/SwiftTour.md#tratamento-de-erros)
  - [x] [Generics](GuidedTour/SwiftTour.md#generics)
- [ ] Guia da Linguagem
  - [x] [O básico](LanguageGuide/TheBasics.md#the-basics)
    - [x] [Introdução](LanguageGuide/TheBasics.md#the-basics)
    - [x] [Constantes e variáveis](LanguageGuide/TheBasics.md#constants-and-variables)
    - [x] [Comentários](LanguageGuide/TheBasics.md#coment%C3%A1rios)
    - [x] [Ponto-e-vírgula](LanguageGuide/TheBasics.md#ponto-e-v%C3%ADrgula)
    - [x] [Inteiros](LanguageGuide/TheBasics.md#integers)
    - [x] [Números de ponto-flutuante](LanguageGuide/TheBasics.md#n%C3%BAmeros-de-ponto-flutuante)
    - [x] [Type Safety e inferência de tipo](LanguageGuide/TheBasics.md#type-safety-e-inferência-de-tipo)
    - [x] [Literais numéricos](LanguageGuide/TheBasics.md#literais-num%C3%A9ricos)
    - [x] [Conversão de tipo numérico](LanguageGuide/TheBasics.md#convers%C3%A3o-de-tipo-num%C3%A9rico)
    - [x] [Asserções e pré-condições](LanguageGuide/TheBasics.md#asserções-e-pré-condições)
  - [x] [Operadores básicos](LanguageGuide/BasicOperators.md)
    - [x] [Introdução](LanguageGuide/BasicOperators.md#operadores-b%C3%A1sicos)
    - [x] [Terminologia](LanguageGuide/BasicOperators.md#terminologia)
    - [x] [Operador de atribuição](LanguageGuide/BasicOperators.md#operador-de-atribui%C3%A7%C3%A3o)
    - [x] [Operadores aritméticos](LanguageGuide/BasicOperators.md#operadores-aritm%C3%A9ticos)
    - [x] [Operadores compostos de atribuição](LanguageGuide/BasicOperators.md#operadores-compostos-de-atribui%C3%A7%C3%A3o)
    - [x] [Operadores de comparação](LanguageGuide/BasicOperators.md#operadores-de-compara%C3%A7%C3%A3o)
    - [x] [Operador ternário condicional](LanguageGuide/BasicOperators.md#operador-tern%C3%A1rio-condicional)
    - [x] [Operador Nil-Coalescing](LanguageGuide/BasicOperators.md#operador-nil-coalescing)
    - [x] [Operadores de intervalo](LanguageGuide/BasicOperators.md#operadores-de-intervalo)
    - [x] [Operadores lógicos](LanguageGuide/BasicOperators.md#operadores-l%C3%B3gicos)
  - [ ] Strings e caracteres
    - [x] [Introdução](LanguageGuide/StringsAndCharacters.md#strings-e-caracteres)
    - [x] [Literais de string](LanguageGuide/StringsAndCharacters.md#literais-de-string)
    - [x] [Inicializando uma String vazia](LanguageGuide/StringsAndCharacters.md#inicializando-uma-string-vazia)
    - [x] [Mutabilidade de String](LanguageGuide/StringsAndCharacters.md#mutabilidade-da-string)
    - [x] [Strings são Value Types](LanguageGuide/StringsAndCharacters.md#strings-são-value-types)
    - [x] [Trabalhando com Characters](LanguageGuide/StringsAndCharacters.md#trabalhando-com-caracteres)
    - [x] [Concatenando Strings e caracteres](LanguageGuide/StringsAndCharacters.md#concatenando-strings-e-caracteres)
    - [x] [Interpolação de String](LanguageGuide/StringsAndCharacters.md#interpolação-de-string)
    - [ ] Unicode
    - [ ] Contando Caracteres
    - [ ] Acessando e modificando uma String
    - [ ] Substrings
    - [ ] Comparando Strings
    - [ ] Representação de Strings em Unicode
  - [ ] Tipos de coleções
    - [x] [Introdução](LanguageGuide/CollectionTypes.md#collection-types)
    - [x] [Mutabilidade de Coleções](LanguageGuide/CollectionTypes.md#mutabilidade-de-coleções)
    - [x] [Arrays](LanguageGuide/CollectionTypes.md#arrays)
    - [ ] Sets
    - [ ] Performando operações em Sets
    - [ ] Dicionários
  - [ ] Controle de fluxo
    - [ ] Introdução
    - [ ] Laços de repetição For-In
    - [ ] Laços de repetição While
    - [ ] Instruções condicionais
    - [ ] Comandos de transferência de controle
    - [ ] Saída antecipada
    - [ ] Verificando disponibilidade de API
  - [ ] Funções
    - [ ] Introdução
    - [ ] Definindo e chamando Funções
    - [ ] Parâmetros de funções e valores de retorno
    - [ ] Rótulos de argumentos de Funções e nomes de parâmetros
    - [ ] Tipos de Funcões
    - [ ] Funções aninhadas
  - [ ] Closures
    - [x] [Introdução](LanguageGuide/Closures.md#closures)
    - [x] [Expressões Closure](LanguageGuide/Closures.md#express%C3%B5es-closure)
    - [ ] Trailing Closures
    - [ ] Capturando valores
    - [x] [Closures são tipos de valor](LanguageGuide/Closures.md#closures-s%C3%A3o-reference-types)
    - [x] [Escaping Closures](LanguageGuide/Closures.md#escaping-closures)
    - [ ] Autoclosures
  - [ ] Enumerações
    - [X] [Introdução](LanguageGuide/Enumerations.md#enumera%C3%A7%C3%B5es)
    - [X] [Sintaxe de Enumerações](LanguageGuide/Enumerations.md#sintaxe-de-enumera%C3%A7%C3%B5es)
    - [X] [Matching Enumeration Values with a Switch Statement](LanguageGuide/Enumerations.md#correspondendo-valores-de-enumera%C3%A7%C3%B5es-com-blocos-switch)
    - [ ] Iterando sobre casos de Enumerações
    - [ ] Valores associados
    - [ ] Valores brutos
    - [ ] Enumerações recursivas
  - [ ] <i>Structures</i> e Classes
    - [ ] Introdução
    - [ ] Comparando Structures e Classes
    - [ ] Structures e enumerações são tipos de valor
    - [ ] Classes são tipos de referência
  - [ ] Propriedades
    - [x] [Introdução](LanguageGuide/Properties.md#propriedades)
    - [x] [Propriedades armazenadas](LanguageGuide/Properties.md#propriedades-armazenadas)
    - [x] [Propriedades computadas](LanguageGuide/Properties.md#propriedades-computadas)
    - [ ] Observadores de propriedades
    - [ ] <i>Wrappers</i> de propriedades
    - [ ] Variáveis globais e locais
    - [ ] Propriedades Tipo
  - [ ] Métodos
    - [ ] Introdução
    - [ ] Métodos de instância
    - [ ] Métodos de tipos
  - [ ] Subscritos
    - [ ] Introdução
    - [ ] Sintaxe de subscritos
    - [ ] Uso de subscritos
    - [ ] Opções de subscritos
    - [ ] Subscritos de tipos
  - [ ] Herança
    - [ ] Introdução
    - [ ] Definindo uma classe base
    - [ ] Criando subclasses
    - [ ] Sobrescrevendo
    - [ ] Prevenindo Sobrescrições
  - [ ] Inicialização
    - [ ] Introdução
    - [ ] Definindo valores iniciais para propriedades armazenadas
    - [ ] Customizando inicialização
    - [ ] Inicializadores padrão
    - [ ] Initializer Delegation for Value Types
    - [ ] Herança de classe e inicialização
    - [ ] Inicializadores que podem falhar
    - [ ] Inicializadores obrigatórios
    - [ ] Definindo um valor padrão de propriedade com uma _Closure_ ou Função
  - [ ] Deinicialização
    - [ ] Introdução
    - [ ] How Deinitialization Works
    - [ ] Deinitializers in Action
  - [ ] Encadeamento opcional
    - [ ] Introdução
    - [ ] Encadeamento opcional como uma alternativa ao _unwrapping_ forçado
    - [ ] Definindo classes modelo para encadeamento opcional
    - [ ] Acessando propriedades através de encadeamento opcional
    - [ ] Chamando métodos através de encadeamento opcional
    - [ ] Acessando subscrito através de encadeamento opcional
    - [ ] Vinculando multiplos níveis de encadeamento
    - [ ] Encadeamento em métodos com retornos do tipo opcional
  - [ ] Manipulação de erros
    - [ ] Introdução
    - [x] Representando e disparando erros
    - [ ] Manipulando erros
    - [ ] Especificando ações de limpeza
  - [ ] Conversão de tipo
    - [ ] Introdução
    - [ ] Definindo uma hierarquia de classe para conversão de tipo
    - [ ] Verificando tipo
    - [ ] _Downcasting_
    - [ ] Conversão de tipo para _Any_ e _AnyObject_
  - [ ] Tipos aninhados
    - [ ] Introdução
    - [ ] Tipos aninhados na prática
    - [ ] Referenciando tipos aninhados
  - [ ] Extensões
    - [ ] Introdução
    - [ ] Sintaxe de extensão
    - [ ] Propriedades computadas
    - [ ] Inicializadores
    - [ ] Métodos
    - [ ] Subscritos
    - [ ] Tipos aninhados
  - [ ] Protocolos
    - [ ] Introdução
    - [ ] Sintaxe de protocolo
    - [ ] Requisitos de propriedades
    - [ ] Requisitos de métodos
    - [ ] Requisitos de métodos _mutating_
    - [ ] Requisitos de inicializadores
    - [ ] Protocolos como tipos
    - [ ] Delegação
    - [ ] Adicionando conformação de protocolo com uma extensão
    - [ ] Adotando um protocolo usando uma implementação sintetizada
    - [ ] Coleções de tipos de protocolos
    - [ ] Herança de protocolos
    - [ ] Protocolos somente de classes
    - [ ] Composição de protocolos
    - [ ] Verificando conformidade com protocolos
    - [ ] Requisitos de protocolos opcionais
    - [ ] Extensões de protocolos
  - [ ] Generics
    - [x] [Intro](LanguageGuide/Generics.md#generics)
    - [x] [The Problem That Generics Solve](LanguageGuide/Generics.md#o-problema-que-generics-resolve)
    - [x] [Generic Functions](LanguageGuide/Generics.md#fun%C3%A7%C3%B5es-generic)
    - [ ] Type Parameters
    - [ ] Naming Type Parameters
    - [x] [Generic Types](LanguageGuide/Generics.md#Tipos%20Gen%C3%A9ricos)
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
