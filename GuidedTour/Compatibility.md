 Versão de Compatibilidade

Versão de Compatibilidade
=====================

Este livro descreve a versão Swift 5.1, a versão atual do Swift que já vem incluída no Xcode 11. Você pode usar o Xcode 11 para criar targets escritos em Swift 5.1, Swift 4.2 ou Swift 4.

Quando você usa o Xcode 11 para criar o código em Swift 4 e Swift 4.2, a maioria das funcionalidades do Swift 5.1 já estão disponíveis. Com isso, as alterações abaixo estão disponíveis apenas para códigos que utilizam a versão Swift 5.1 ou posterior:

*   Funções que tem como retorno um tipo opaco requerem o *runtime* do Swift 5.1
    
*   A expressão `try?` não introduz um nível extra de opcionalidade para expressões que já retornam opcionais.

*   As expressões literais inteiras grandes de inicialização são inferidas como sendo do tipo inteiro correto. Por exemplo, `UInt64 (0xffff_ffff_ffff_ffff)` avalia o valor correto ao invés de ter *overflow*.

Um target escrito em Swift 5.1 pode depender de um target escrito em Swift 4.2 ou Swift 4 e vice-versa. Isso significa que, se você tiver em um projeto grande dividido em vários *frameworks*, poderá migrar seu código do Swift 4 para Swift 5.1, um *framework* por vez.