Summary of the Grammar  

Summary of the Grammar
======================

Lexical Structure
-----------------

>**Grammar of whitespace**
>
>whitespace → [whitespace-item](../ReferenceManual/LexicalStructure.md#grammar_whitespace-item) [whitespace](../ReferenceManual/LexicalStructure.md#grammar_whitespace) <sub>opt</sub>
>
>whitespace-item → [line-break](../ReferenceManual/LexicalStructure.md#grammar_line-break)
>
>whitespace-item → [comment](../ReferenceManual/LexicalStructure.md#grammar_comment)
>
>whitespace-item → [multiline-comment](../ReferenceManual/LexicalStructure.md#grammar_multiline-comment)
>
>whitespace-item → U+0000, U+0009, U+000B, U+000C, or U+0020
>
>line-break → U+000A
>
>line-break → U+000D
>
>line-break → U+000D followed by U+000A
>
>comment → `//` [comment-text](../ReferenceManual/LexicalStructure.md#grammar_comment-text) [line-break](../ReferenceManual/LexicalStructure.md#grammar_line-break)
>
>multiline-comment → `/*` [multiline-comment-text](../ReferenceManual/LexicalStructure.md#grammar_multiline-comment-text) `*/`
>
>comment-text → [comment-text-item](../ReferenceManual/LexicalStructure.md#grammar_comment-text-item) [comment-text](../ReferenceManual/LexicalStructure.md#grammar_comment-text) <sub>opt</sub>
>
>comment-text-item → Any Unicode scalar value except U+000A or U+000D
>
>multiline-comment-text → [multiline-comment-text-item](../ReferenceManual/LexicalStructure.md#grammar_multiline-comment-text-item) [multiline-comment-text](../ReferenceManual/LexicalStructure.md#grammar_multiline-comment-text) <sub>opt</sub>
>
>multiline-comment-text-item → [multiline-comment](../ReferenceManual/LexicalStructure.md#grammar_multiline-comment)
>
>multiline-comment-text-item → [comment-text-item](../ReferenceManual/LexicalStructure.md#grammar_comment-text-item)
>
>multiline-comment-text-item → Any Unicode scalar value except `/*` or `*/`

>**Grammar of an identifier**
>
>identifier → [identifier-head](../ReferenceManual/LexicalStructure.md#grammar_identifier-head) [identifier-characters](../ReferenceManual/LexicalStructure.md#grammar_identifier-characters) <sub>opt</sub>
>
>identifier → `` ` `` [identifier-head](../ReferenceManual/LexicalStructure.md#grammar_identifier-head) [identifier-characters](../ReferenceManual/LexicalStructure.md#grammar_identifier-characters) <sub>opt</sub> `` ` ``
>
>identifier → [implicit-parameter-name](../ReferenceManual/LexicalStructure.md#grammar_implicit-parameter-name)
>
>identifier → [property-wrapper-projection](../ReferenceManual/LexicalStructure.md#grammar_property-wrapper-projection)
>
>identifier-list → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) | [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `,` [identifier-list](../ReferenceManual/LexicalStructure.md#grammar_identifier-list)
>
>identifier-head → Upper- or lowercase letter A through Z
>
>identifier-head → `_`
>
>identifier-head → U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA
>
>identifier-head → U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF
>
>identifier-head → U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF
>
>identifier-head → U+1E00–U+1FFF
>
>identifier-head → U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F
>
>identifier-head → U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793
>
>identifier-head → U+2C00–U+2DFF or U+2E80–U+2FFF
>
>identifier-head → U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF
>
>identifier-head → U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44
>
>identifier-head → U+FE47–U+FFFD
>
>identifier-head → U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD
>
>identifier-head → U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD
>
>identifier-head → U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD
>
>identifier-head → U+D0000–U+DFFFD or U+E0000–U+EFFFD
>
>identifier-character → Digit 0 through 9
>
>identifier-character → U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F
>
>identifier-character → [identifier-head](../ReferenceManual/LexicalStructure.md#grammar_identifier-head)
>
>identifier-characters → [identifier-character](../ReferenceManual/LexicalStructure.md#grammar_identifier-character) [identifier-characters](../ReferenceManual/LexicalStructure.md#grammar_identifier-characters) <sub>opt</sub>
>
>implicit-parameter-name → `$` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)
>
>property-wrapper-projection → `$` [identifier-characters](../ReferenceManual/LexicalStructure.md#grammar_identifier-characters)

>**Grammar of a literal**
>
>literal → [numeric-literal](../ReferenceManual/LexicalStructure.md#grammar_numeric-literal) | [string-literal](../ReferenceManual/LexicalStructure.md#grammar_string-literal) | [boolean-literal](../ReferenceManual/LexicalStructure.md#grammar_boolean-literal) | [nil-literal](../ReferenceManual/LexicalStructure.md#grammar_nil-literal)
>
>numeric-literal → `-`<sub>opt</sub> [integer-literal](../ReferenceManual/LexicalStructure.md#grammar_integer-literal) | `-`<sub>opt</sub> [floating-point-literal](../ReferenceManual/LexicalStructure.md#grammar_floating-point-literal)
>
>boolean-literal → `true` | `false`
>
>nil-literal → `nil`

>**Grammar of an integer literal**
>
>integer-literal → [binary-literal](../ReferenceManual/LexicalStructure.md#grammar_binary-literal)
>
>integer-literal → [octal-literal](../ReferenceManual/LexicalStructure.md#grammar_octal-literal)
>
>integer-literal → [decimal-literal](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal)
>
>integer-literal → [hexadecimal-literal](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-literal)
>
>binary-literal → `0b` [binary-digit](../ReferenceManual/LexicalStructure.md#grammar_binary-digit) [binary-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_binary-literal-characters) <sub>opt</sub>
>
>binary-digit → Digit 0 or 1
>
>binary-literal-character → [binary-digit](../ReferenceManual/LexicalStructure.md#grammar_binary-digit) | `_`
>
>binary-literal-characters → [binary-literal-character](../ReferenceManual/LexicalStructure.md#grammar_binary-literal-character) [binary-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_binary-literal-characters) <sub>opt</sub>
>
>octal-literal → `0o` [octal-digit](../ReferenceManual/LexicalStructure.md#grammar_octal-digit) [octal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_octal-literal-characters) <sub>opt</sub>
>
>octal-digit → Digit 0 through 7
>
>octal-literal-character → [octal-digit](../ReferenceManual/LexicalStructure.md#grammar_octal-digit) | `_`
>
>octal-literal-characters → [octal-literal-character](../ReferenceManual/LexicalStructure.md#grammar_octal-literal-character) [octal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_octal-literal-characters) <sub>opt</sub>
>
>decimal-literal → [decimal-digit](../ReferenceManual/LexicalStructure.md#grammar_decimal-digit) [decimal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal-characters) <sub>opt</sub>
>
>decimal-digit → Digit 0 through 9
>
>decimal-digits → [decimal-digit](../ReferenceManual/LexicalStructure.md#grammar_decimal-digit) [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) <sub>opt</sub>
>
>decimal-literal-character → [decimal-digit](../ReferenceManual/LexicalStructure.md#grammar_decimal-digit) | `_`
>
>decimal-literal-characters → [decimal-literal-character](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal-character) [decimal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal-characters) <sub>opt</sub>
>
>hexadecimal-literal → `0x` [hexadecimal-digit](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-digit) [hexadecimal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-literal-characters) <sub>opt</sub>
>
>hexadecimal-digit → Digit 0 through 9, a through f, or A through F
>
>hexadecimal-literal-character → [hexadecimal-digit](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-digit) | `_`
>
>hexadecimal-literal-characters → [hexadecimal-literal-character](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-literal-character) [hexadecimal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-literal-characters) <sub>opt</sub>

>**Grammar of a floating-point literal**
>
>floating-point-literal → [decimal-literal](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal) [decimal-fraction](../ReferenceManual/LexicalStructure.md#grammar_decimal-fraction) <sub>opt</sub> [decimal-exponent](../ReferenceManual/LexicalStructure.md#grammar_decimal-exponent) <sub>opt</sub>
>
>floating-point-literal → [hexadecimal-literal](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-literal) [hexadecimal-fraction](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-fraction) <sub>opt</sub> [hexadecimal-exponent](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-exponent)
>
>decimal-fraction → `.` [decimal-literal](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal)
>
>decimal-exponent → [floating-point-e](../ReferenceManual/LexicalStructure.md#grammar_floating-point-e) [sign](../ReferenceManual/LexicalStructure.md#grammar_sign) <sub>opt</sub> [decimal-literal](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal)
>
>hexadecimal-fraction → `.` [hexadecimal-digit](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-digit) [hexadecimal-literal-characters](../ReferenceManual/LexicalStructure.md#grammar_hexadecimal-literal-characters) <sub>opt</sub>
>
>hexadecimal-exponent → [floating-point-p](../ReferenceManual/LexicalStructure.md#grammar_floating-point-p) [sign](../ReferenceManual/LexicalStructure.md#grammar_sign) <sub>opt</sub> [decimal-literal](../ReferenceManual/LexicalStructure.md#grammar_decimal-literal)
>
>floating-point-e → `e` | `E`
>
>floating-point-p → `p` | `P`
>
>sign → `+` | `-`

>**Grammar of a string literal**
>
>string-literal → [static-string-literal](../ReferenceManual/LexicalStructure.md#grammar_static-string-literal) | [interpolated-string-literal](../ReferenceManual/LexicalStructure.md#grammar_interpolated-string-literal)
>
>string-literal-opening-delimiter → [extended-string-literal-delimiter](../ReferenceManual/LexicalStructure.md#grammar_extended-string-literal-delimiter) <sub>opt</sub> `"`
>
>string-literal-closing-delimiter → `"` [extended-string-literal-delimiter](../ReferenceManual/LexicalStructure.md#grammar_extended-string-literal-delimiter) <sub>opt</sub>
>
>static-string-literal → [string-literal-opening-delimiter](../ReferenceManual/LexicalStructure.md#grammar_string-literal-opening-delimiter) [quoted-text](../ReferenceManual/LexicalStructure.md#grammar_quoted-text) <sub>opt</sub> [string-literal-closing-delimiter](../ReferenceManual/LexicalStructure.md#grammar_string-literal-closing-delimiter)
>
>static-string-literal → [multiline-string-literal-opening-delimiter](../ReferenceManual/LexicalStructure.md#grammar_multiline-string-literal-opening-delimiter) [multiline-quoted-text](../ReferenceManual/LexicalStructure.md#grammar_multiline-quoted-text) <sub>opt</sub> [multiline-string-literal-closing-delimiter](../ReferenceManual/LexicalStructure.md#grammar_multiline-string-literal-closing-delimiter)
>
>multiline-string-literal-opening-delimiter → [extended-string-literal-delimiter](../ReferenceManual/LexicalStructure.md#grammar_extended-string-literal-delimiter) `"""`
>
>multiline-string-literal-closing-delimiter → `"""` [extended-string-literal-delimiter](../ReferenceManual/LexicalStructure.md#grammar_extended-string-literal-delimiter)
>
>extended-string-literal-delimiter → `#` [extended-string-literal-delimiter](../ReferenceManual/LexicalStructure.md#grammar_extended-string-literal-delimiter) <sub>opt</sub>
>
>quoted-text → [quoted-text-item](../ReferenceManual/LexicalStructure.md#grammar_quoted-text-item) [quoted-text](../ReferenceManual/LexicalStructure.md#grammar_quoted-text) <sub>opt</sub>
>
>quoted-text-item → [escaped-character](../ReferenceManual/LexicalStructure.md#grammar_escaped-character)
>
>quoted-text-item → Any Unicode scalar value except `"`, `\`, U+000A, or U+000D
>
>multiline-quoted-text → [multiline-quoted-text-item](../ReferenceManual/LexicalStructure.md#grammar_multiline-quoted-text-item) [multiline-quoted-text](../ReferenceManual/LexicalStructure.md#grammar_multiline-quoted-text) <sub>opt</sub>
>
>multiline-quoted-text-item → [escaped-character](../ReferenceManual/LexicalStructure.md#grammar_escaped-character)
>
>multiline-quoted-text-item → Any Unicode scalar value except `\`
>
>multiline-quoted-text-item → [escaped-newline](../ReferenceManual/LexicalStructure.md#grammar_escaped-newline)
>
>interpolated-string-literal → [string-literal-opening-delimiter](../ReferenceManual/LexicalStructure.md#grammar_string-literal-opening-delimiter) [interpolated-text](../ReferenceManual/LexicalStructure.md#grammar_interpolated-text) <sub>opt</sub> [string-literal-closing-delimiter](../ReferenceManual/LexicalStructure.md#grammar_string-literal-closing-delimiter)
>
>interpolated-string-literal → [multiline-string-literal-opening-delimiter](../ReferenceManual/LexicalStructure.md#grammar_multiline-string-literal-opening-delimiter) [interpolated-text](../ReferenceManual/LexicalStructure.md#grammar_interpolated-text) <sub>opt</sub> [multiline-string-literal-closing-delimiter](../ReferenceManual/LexicalStructure.md#grammar_multiline-string-literal-closing-delimiter)
>
>interpolated-text → [interpolated-text-item](../ReferenceManual/LexicalStructure.md#grammar_interpolated-text-item) [interpolated-text](../ReferenceManual/LexicalStructure.md#grammar_interpolated-text) <sub>opt</sub>
>
>interpolated-text-item → `\(` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)` | [quoted-text-item](../ReferenceManual/LexicalStructure.md#grammar_quoted-text-item)
>
>multiline-interpolated-text → [multiline-interpolated-text-item](../ReferenceManual/LexicalStructure.md#grammar_multiline-interpolated-text-item) [multiline-interpolated-text](../ReferenceManual/LexicalStructure.md#grammar_multiline-interpolated-text) <sub>opt</sub>
>
>multiline-interpolated-text-item → `\(` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)` | [multiline-quoted-text-item](../ReferenceManual/LexicalStructure.md#grammar_multiline-quoted-text-item)
>
>escape-sequence → `\` [extended-string-literal-delimiter](../ReferenceManual/LexicalStructure.md#grammar_extended-string-literal-delimiter)
>
>escaped-character → [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `0` | [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `\` | [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `t` | [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `n` | [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `r` | [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `"` | [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `'`
>
>escaped-character → [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) `u` `{` [unicode-scalar-digits](../ReferenceManual/LexicalStructure.md#grammar_unicode-scalar-digits) `}`
>
>unicode-scalar-digits → Between one and eight hexadecimal digits
>
>escaped-newline → [escape-sequence](../ReferenceManual/LexicalStructure.md#grammar_escape-sequence) [whitespace](../ReferenceManual/LexicalStructure.md#grammar_whitespace) <sub>opt</sub> [line-break](../ReferenceManual/LexicalStructure.md#grammar_line-break)

>**Grammar of operators**
>
>operator → [operator-head](../ReferenceManual/LexicalStructure.md#grammar_operator-head) [operator-characters](../ReferenceManual/LexicalStructure.md#grammar_operator-characters) <sub>opt</sub>
>
>operator → [dot-operator-head](../ReferenceManual/LexicalStructure.md#grammar_dot-operator-head) [dot-operator-characters](../ReferenceManual/LexicalStructure.md#grammar_dot-operator-characters)
>
>operator-head → `/` | `=` | `-` | `+` | `!` | `*` | `%` | `<` | `>` | `&` | `|` | `^` | `~` | `?`
>
>operator-head → U+00A1–U+00A7
>
>operator-head → U+00A9 or U+00AB
>
>operator-head → U+00AC or U+00AE
>
>operator-head → U+00B0–U+00B1
>
>operator-head → U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7
>
>operator-head → U+2016–U+2017
>
>operator-head → U+2020–U+2027
>
>operator-head → U+2030–U+203E
>
>operator-head → U+2041–U+2053
>
>operator-head → U+2055–U+205E
>
>operator-head → U+2190–U+23FF
>
>operator-head → U+2500–U+2775
>
>operator-head → U+2794–U+2BFF
>
>operator-head → U+2E00–U+2E7F
>
>operator-head → U+3001–U+3003
>
>operator-head → U+3008–U+3020
>
>operator-head → U+3030
>
>operator-character → [operator-head](../ReferenceManual/LexicalStructure.md#grammar_operator-head)
>
>operator-character → U+0300–U+036F
>
>operator-character → U+1DC0–U+1DFF
>
>operator-character → U+20D0–U+20FF
>
>operator-character → U+FE00–U+FE0F
>
>operator-character → U+FE20–U+FE2F
>
>operator-character → U+E0100–U+E01EF
>
>operator-characters → [operator-character](../ReferenceManual/LexicalStructure.md#grammar_operator-character) [operator-characters](../ReferenceManual/LexicalStructure.md#grammar_operator-characters) <sub>opt</sub>
>
>dot-operator-head → `.`
>
>dot-operator-character → `.` | [operator-character](../ReferenceManual/LexicalStructure.md#grammar_operator-character)
>
>dot-operator-characters → [dot-operator-character](../ReferenceManual/LexicalStructure.md#grammar_dot-operator-character) [dot-operator-characters](../ReferenceManual/LexicalStructure.md#grammar_dot-operator-characters) <sub>opt</sub>
>
>binary-operator → [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)
>
>prefix-operator → [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)
>
>postfix-operator → [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)

Types
-----

>**Grammar of a type**
>
>type → [function-type](../ReferenceManual/Types.md#grammar_function-type)
>
>type → [array-type](../ReferenceManual/Types.md#grammar_array-type)
>
>type → [dictionary-type](../ReferenceManual/Types.md#grammar_dictionary-type)
>
>type → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier)
>
>type → [tuple-type](../ReferenceManual/Types.md#grammar_tuple-type)
>
>type → [optional-type](../ReferenceManual/Types.md#grammar_optional-type)
>
>type → [implicitly-unwrapped-optional-type](../ReferenceManual/Types.md#grammar_implicitly-unwrapped-optional-type)
>
>type → [protocol-composition-type](../ReferenceManual/Types.md#grammar_protocol-composition-type)
>
>type → [opaque-type](../ReferenceManual/Types.md#grammar_opaque-type)
>
>type → [metatype-type](../ReferenceManual/Types.md#grammar_metatype-type)
>
>type → [self-type](../ReferenceManual/Types.md#grammar_self-type)
>
>type → `Any`
>
>type → `(` [type](../ReferenceManual/Types.md#grammar_type) `)`

>**Grammar of a type annotation**
>
>type-annotation → `:` [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `inout`<sub>opt</sub> [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of a type identifier**
>
>type-identifier → [type-name](../ReferenceManual/Types.md#grammar_type-name) [generic-argument-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument-clause) <sub>opt</sub> | [type-name](../ReferenceManual/Types.md#grammar_type-name) [generic-argument-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument-clause) <sub>opt</sub> `.` [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier)
>
>type-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of a tuple type**
>
>tuple-type → `(` `)` | `(` [tuple-type-element](../ReferenceManual/Types.md#grammar_tuple-type-element) `,` [tuple-type-element-list](../ReferenceManual/Types.md#grammar_tuple-type-element-list) `)`
>
>tuple-type-element-list → [tuple-type-element](../ReferenceManual/Types.md#grammar_tuple-type-element) | [tuple-type-element](../ReferenceManual/Types.md#grammar_tuple-type-element) `,` [tuple-type-element-list](../ReferenceManual/Types.md#grammar_tuple-type-element-list)
>
>tuple-type-element → [element-name](../ReferenceManual/Types.md#grammar_element-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) | [type](../ReferenceManual/Types.md#grammar_type)
>
>element-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

**Grammar of a function type**
>
>function-type → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [function-type-argument-clause](../ReferenceManual/Types.md#grammar_function-type-argument-clause) `throws`<sub>opt</sub> `->` [type](../ReferenceManual/Types.md#grammar_type)
>
>function-type-argument-clause → `(` `)`
>
>function-type-argument-clause → `(` [function-type-argument-list](../ReferenceManual/Types.md#grammar_function-type-argument-list) `...`<sub>opt</sub> `)`
>
>function-type-argument-list → [function-type-argument](../ReferenceManual/Types.md#grammar_function-type-argument) | [function-type-argument](../ReferenceManual/Types.md#grammar_function-type-argument) `,` [function-type-argument-list](../ReferenceManual/Types.md#grammar_function-type-argument-list)
>
>function-type-argument → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `inout`<sub>opt</sub> [type](../ReferenceManual/Types.md#grammar_type) | [argument-label](../ReferenceManual/Types.md#grammar_argument-label) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation)
>
>argument-label → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of an array type**
>
>array-type → `[` [type](../ReferenceManual/Types.md#grammar_type) `]`

>**Grammar of a dictionary type**
>
>dictionary-type → `[` [type](../ReferenceManual/Types.md#grammar_type) `:` [type](../ReferenceManual/Types.md#grammar_type) `]`

>**Grammar of an optional type**
>
>optional-type → [type](../ReferenceManual/Types.md#grammar_type) `?`

>**Grammar of an implicitly unwrapped optional type**
>
>implicitly-unwrapped-optional-type → [type](../ReferenceManual/Types.md#grammar_type) `!`

>**Grammar of a protocol composition type**
>
>protocol-composition-type → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) `&` [protocol-composition-continuation](../ReferenceManual/Types.md#grammar_protocol-composition-continuation)
>
>protocol-composition-continuation → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) | [protocol-composition-type](../ReferenceManual/Types.md#grammar_protocol-composition-type)

>**Grammar of an opaque type**
>
>opaque-type → `some` [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of a metatype type**
>
>metatype-type → [type](../ReferenceManual/Types.md#grammar_type) `.` `Type` | [type](../ReferenceManual/Types.md#grammar_type) `.` `Protocol`

>**Grammar of a Self type**
>
>self-type → `Self`

>**Grammar of a type inheritance clause**
>
>type-inheritance-clause → `:` [type-inheritance-list](../ReferenceManual/Types.md#grammar_type-inheritance-list)
>
>type-inheritance-list → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) | [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) `,` [type-inheritance-list](../ReferenceManual/Types.md#grammar_type-inheritance-list)

Expressions
-----------

>**Grammar of an expression**
>
>expression → [try-operator](../ReferenceManual/Expressions.md#grammar_try-operator) <sub>opt</sub> [prefix-expression](../ReferenceManual/Expressions.md#grammar_prefix-expression) [binary-expressions](../ReferenceManual/Expressions.md#grammar_binary-expressions) <sub>opt</sub>
>
>expression-list → [expression](../ReferenceManual/Expressions.md#grammar_expression) | [expression](../ReferenceManual/Expressions.md#grammar_expression) `,` [expression-list](../ReferenceManual/Expressions.md#grammar_expression-list)

>**Grammar of a prefix expression**
>
>prefix-expression → [prefix-operator](../ReferenceManual/LexicalStructure.md#grammar_prefix-operator) <sub>opt</sub> [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression)
>
>prefix-expression → [in-out-expression](../ReferenceManual/Expressions.md#grammar_in-out-expression)
>
>in-out-expression → `&` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of a try expression**
>
>try-operator → `try` | `try` `?` | `try` `!`

>**Grammar of a binary expression**
>
>binary-expression → [binary-operator](../ReferenceManual/LexicalStructure.md#grammar_binary-operator) [prefix-expression](../ReferenceManual/Expressions.md#grammar_prefix-expression)
>
>binary-expression → [assignment-operator](../ReferenceManual/Expressions.md#grammar_assignment-operator) [try-operator](../ReferenceManual/Expressions.md#grammar_try-operator) <sub>opt</sub> [prefix-expression](../ReferenceManual/Expressions.md#grammar_prefix-expression)
>
>binary-expression → [conditional-operator](../ReferenceManual/Expressions.md#grammar_conditional-operator) [try-operator](../ReferenceManual/Expressions.md#grammar_try-operator) <sub>opt</sub> [prefix-expression](../ReferenceManual/Expressions.md#grammar_prefix-expression)
>
>binary-expression → [type-casting-operator](../ReferenceManual/Expressions.md#grammar_type-casting-operator)
>
>binary-expressions → [binary-expression](../ReferenceManual/Expressions.md#grammar_binary-expression) [binary-expressions](../ReferenceManual/Expressions.md#grammar_binary-expressions) <sub>opt</sub>

>**Grammar of an assignment operator**
>
>assignment-operator → `=`

>**Grammar of a conditional operator**
>
>conditional-operator → `?` [expression](../ReferenceManual/Expressions.md#grammar_expression) `:`

>**Grammar of a type-casting operator**
>
>type-casting-operator → `is` [type](../ReferenceManual/Types.md#grammar_type)
>
>type-casting-operator → `as` [type](../ReferenceManual/Types.md#grammar_type)
>
>type-casting-operator → `as` `?` [type](../ReferenceManual/Types.md#grammar_type)
>
>type-casting-operator → `as` `!` [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of a primary expression**
>
>primary-expression → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) [generic-argument-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument-clause) <sub>opt</sub>
>
>primary-expression → [literal-expression](../ReferenceManual/Expressions.md#grammar_literal-expression)
>
>primary-expression → [self-expression](../ReferenceManual/Expressions.md#grammar_self-expression)
>
>primary-expression → [superclass-expression](../ReferenceManual/Expressions.md#grammar_superclass-expression)
>
>primary-expression → [closure-expression](../ReferenceManual/Expressions.md#grammar_closure-expression)
>
>primary-expression → [parenthesized-expression](../ReferenceManual/Expressions.md#grammar_parenthesized-expression)
>
>primary-expression → [tuple-expression](../ReferenceManual/Expressions.md#grammar_tuple-expression)
>
>primary-expression → [implicit-member-expression](../ReferenceManual/Expressions.md#grammar_implicit-member-expression)
>
>primary-expression → [wildcard-expression](../ReferenceManual/Expressions.md#grammar_wildcard-expression)
>
>primary-expression → [key-path-expression](../ReferenceManual/Expressions.md#grammar_key-path-expression)
>
>primary-expression → [selector-expression](../ReferenceManual/Expressions.md#grammar_selector-expression)
>
>primary-expression → [key-path-string-expression](../ReferenceManual/Expressions.md#grammar_key-path-string-expression)

>**Grammar of a literal expression**
>
>literal-expression → [literal](../ReferenceManual/LexicalStructure.md#grammar_literal)
>
>literal-expression → [array-literal](../ReferenceManual/Expressions.md#grammar_array-literal) | [dictionary-literal](../ReferenceManual/Expressions.md#grammar_dictionary-literal) | [playground-literal](../ReferenceManual/Expressions.md#grammar_playground-literal)
>
>literal-expression → `#file` | `#line` | `#column` | `#function` | `#dsohandle`
>
>array-literal → `[` [array-literal-items](../ReferenceManual/Expressions.md#grammar_array-literal-items) <sub>opt</sub> `]`
>
>array-literal-items → [array-literal-item](../ReferenceManual/Expressions.md#grammar_array-literal-item) `,`<sub>opt</sub> | [array-literal-item](../ReferenceManual/Expressions.md#grammar_array-literal-item) `,` [array-literal-items](../ReferenceManual/Expressions.md#grammar_array-literal-items)
>
>array-literal-item → [expression](../ReferenceManual/Expressions.md#grammar_expression)
>
>dictionary-literal → `[` [dictionary-literal-items](../ReferenceManual/Expressions.md#grammar_dictionary-literal-items) `]` | `[` `:` `]`
>
>dictionary-literal-items → [dictionary-literal-item](../ReferenceManual/Expressions.md#grammar_dictionary-literal-item) `,`<sub>opt</sub> | [dictionary-literal-item](../ReferenceManual/Expressions.md#grammar_dictionary-literal-item) `,` [dictionary-literal-items](../ReferenceManual/Expressions.md#grammar_dictionary-literal-items)
>
>dictionary-literal-item → [expression](../ReferenceManual/Expressions.md#grammar_expression) `:` [expression](../ReferenceManual/Expressions.md#grammar_expression)
>
>playground-literal → `#colorLiteral` `(` `red` `:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `,` `green` `:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `,` `blue` `:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `,` `alpha` `:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`
>
>playground-literal → `#fileLiteral` `(` `resourceName` `:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`
>
>playground-literal → `#imageLiteral` `(` `resourceName` `:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`

>**Grammar of a self expression**
>
>self-expression → `self` | [self-method-expression](../ReferenceManual/Expressions.md#grammar_self-method-expression) | [self-subscript-expression](../ReferenceManual/Expressions.md#grammar_self-subscript-expression) | [self-initializer-expression](../ReferenceManual/Expressions.md#grammar_self-initializer-expression)
>
>self-method-expression → `self` `.` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>self-subscript-expression → `self` `[` [function-call-argument-list](../ReferenceManual/Expressions.md#grammar_function-call-argument-list) `]`
>
>self-initializer-expression → `self` `.` `init`

>**Grammar of a superclass expression**
>
>superclass-expression → [superclass-method-expression](../ReferenceManual/Expressions.md#grammar_superclass-method-expression) | [superclass-subscript-expression](../ReferenceManual/Expressions.md#grammar_superclass-subscript-expression) | [superclass-initializer-expression](../ReferenceManual/Expressions.md#grammar_superclass-initializer-expression)
>
>superclass-method-expression → `super` `.` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>superclass-subscript-expression → `super` `[` [function-call-argument-list](../ReferenceManual/Expressions.md#grammar_function-call-argument-list) `]`
>
>superclass-initializer-expression → `super` `.` `init`

>**Grammar of a closure expression**
>
>closure-expression → `{` [closure-signature](../ReferenceManual/Expressions.md#grammar_closure-signature) <sub>opt</sub> [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub> `}`
>
>closure-signature → [capture-list](../ReferenceManual/Expressions.md#grammar_capture-list) <sub>opt</sub> [closure-parameter-clause](../ReferenceManual/Expressions.md#grammar_closure-parameter-clause) `throws`<sub>opt</sub> [function-result](../ReferenceManual/Declarations.md#grammar_function-result) <sub>opt</sub> `in`
>
>closure-signature → [capture-list](../ReferenceManual/Expressions.md#grammar_capture-list) `in`
>
>closure-parameter-clause → `(` `)` | `(` [closure-parameter-list](../ReferenceManual/Expressions.md#grammar_closure-parameter-list) `)` | [identifier-list](../ReferenceManual/LexicalStructure.md#grammar_identifier-list)
>
>closure-parameter-list → [closure-parameter](../ReferenceManual/Expressions.md#grammar_closure-parameter) | [closure-parameter](../ReferenceManual/Expressions.md#grammar_closure-parameter) `,` [closure-parameter-list](../ReferenceManual/Expressions.md#grammar_closure-parameter-list)
>
>closure-parameter → [closure-parameter-name](../ReferenceManual/Expressions.md#grammar_closure-parameter-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) <sub>opt</sub>
>
>closure-parameter → [closure-parameter-name](../ReferenceManual/Expressions.md#grammar_closure-parameter-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) `...`
>
>closure-parameter-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>capture-list → `[` [capture-list-items](../ReferenceManual/Expressions.md#grammar_capture-list-items) `]`
>
>capture-list-items → [capture-list-item](../ReferenceManual/Expressions.md#grammar_capture-list-item) | [capture-list-item](../ReferenceManual/Expressions.md#grammar_capture-list-item) `,` [capture-list-items](../ReferenceManual/Expressions.md#grammar_capture-list-items)
>
>capture-list-item → [capture-specifier](../ReferenceManual/Expressions.md#grammar_capture-specifier) <sub>opt</sub> [expression](../ReferenceManual/Expressions.md#grammar_expression)
>
>capture-specifier → `weak` | `unowned` | `unowned(safe)` | `unowned(unsafe)`

>**Grammar of a implicit member expression**
>
>implicit-member-expression → `.` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of a parenthesized expression**
>
>parenthesized-expression → `(` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`

>**Grammar of a tuple expression**
>
>tuple-expression → `(` `)` | `(` [tuple-element](../ReferenceManual/Expressions.md#grammar_tuple-element) `,` [tuple-element-list](../ReferenceManual/Expressions.md#grammar_tuple-element-list) `)`
>
>tuple-element-list → [tuple-element](../ReferenceManual/Expressions.md#grammar_tuple-element) | [tuple-element](../ReferenceManual/Expressions.md#grammar_tuple-element) `,` [tuple-element-list](../ReferenceManual/Expressions.md#grammar_tuple-element-list)
>
>tuple-element → [expression](../ReferenceManual/Expressions.md#grammar_expression) | [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `:` [expression](../ReferenceManual/Expressions.md#grammar_expression)

>**Grammar of a wildcard expression**
>
>wildcard-expression → `_`

>**Grammar of a key-path expression**
>
>key-path-expression → `\` [type](../ReferenceManual/Types.md#grammar_type) <sub>opt</sub> `.` [key-path-components](../ReferenceManual/Expressions.md#grammar_key-path-components)
>
>key-path-components → [key-path-component](../ReferenceManual/Expressions.md#grammar_key-path-component) | [key-path-component](../ReferenceManual/Expressions.md#grammar_key-path-component) `.` [key-path-components](../ReferenceManual/Expressions.md#grammar_key-path-components)
>
>key-path-component → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) [key-path-postfixes](../ReferenceManual/Expressions.md#grammar_key-path-postfixes) <sub>opt</sub> | [key-path-postfixes](../ReferenceManual/Expressions.md#grammar_key-path-postfixes)
>
>key-path-postfixes → [key-path-postfix](../ReferenceManual/Expressions.md#grammar_key-path-postfix) [key-path-postfixes](../ReferenceManual/Expressions.md#grammar_key-path-postfixes) <sub>opt</sub>
>
>key-path-postfix → `?` | `!` | `self` | `[` [function-call-argument-list](../ReferenceManual/Expressions.md#grammar_function-call-argument-list) `]`

>**Grammar of a selector expression**
>
>selector-expression → `#selector` `(` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`
>
>selector-expression → `#selector` `(` `getter:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`
>
>selector-expression → `#selector` `(` `setter:` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`

>**Grammar of a key-path string expression**
>
>key-path-string-expression → `#keyPath` `(` [expression](../ReferenceManual/Expressions.md#grammar_expression) `)`

>**Grammar of a postfix expression**
>
>postfix-expression → [primary-expression](../ReferenceManual/Expressions.md#grammar_primary-expression)
>
>postfix-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) [postfix-operator](../ReferenceManual/LexicalStructure.md#grammar_postfix-operator)
>
>postfix-expression → [function-call-expression](../ReferenceManual/Expressions.md#grammar_function-call-expression)
>
>postfix-expression → [initializer-expression](../ReferenceManual/Expressions.md#grammar_initializer-expression)
>
>postfix-expression → [explicit-member-expression](../ReferenceManual/Expressions.md#grammar_explicit-member-expression)
>
>postfix-expression → [postfix-self-expression](../ReferenceManual/Expressions.md#grammar_postfix-self-expression)
>
>postfix-expression → [subscript-expression](../ReferenceManual/Expressions.md#grammar_subscript-expression)
>
>postfix-expression → [forced-value-expression](../ReferenceManual/Expressions.md#grammar_forced-value-expression)
>
>postfix-expression → [optional-chaining-expression](../ReferenceManual/Expressions.md#grammar_optional-chaining-expression)

>**Grammar of a function call expression**
>
>function-call-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) [function-call-argument-clause](../ReferenceManual/Expressions.md#grammar_function-call-argument-clause)
>
>function-call-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) [function-call-argument-clause](../ReferenceManual/Expressions.md#grammar_function-call-argument-clause) <sub>opt</sub> [trailing-closure](../ReferenceManual/Expressions.md#grammar_trailing-closure)
>
>function-call-argument-clause → `(` `)` | `(` [function-call-argument-list](../ReferenceManual/Expressions.md#grammar_function-call-argument-list) `)`
>
>function-call-argument-list → [function-call-argument](../ReferenceManual/Expressions.md#grammar_function-call-argument) | [function-call-argument](../ReferenceManual/Expressions.md#grammar_function-call-argument) `,` [function-call-argument-list](../ReferenceManual/Expressions.md#grammar_function-call-argument-list)
>
>function-call-argument → [expression](../ReferenceManual/Expressions.md#grammar_expression) | [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `:` [expression](../ReferenceManual/Expressions.md#grammar_expression)
>
>function-call-argument → [operator](../ReferenceManual/LexicalStructure.md#grammar_operator) | [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `:` [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)
>
>trailing-closure → [closure-expression](../ReferenceManual/Expressions.md#grammar_closure-expression)

>**Grammar of an initializer expression**
>
>initializer-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `.` `init`
>
>initializer-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `.` `init` `(` [argument-names](../ReferenceManual/Expressions.md#grammar_argument-names) `)`

>**Grammar of an explicit member expression**
>
>explicit-member-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)
>
>explicit-member-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `.` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) [generic-argument-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument-clause) <sub>opt</sub>
>
>explicit-member-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `.` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `(` [argument-names](../ReferenceManual/Expressions.md#grammar_argument-names) `)`
>
>argument-names → [argument-name](../ReferenceManual/Expressions.md#grammar_argument-name) [argument-names](../ReferenceManual/Expressions.md#grammar_argument-names) <sub>opt</sub>
>
>argument-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `:`

>**Grammar of a postfix self expression**
>
>postfix-self-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `.` `self`

>**Grammar of a subscript expression**
>
>subscript-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `[` [function-call-argument-list](../ReferenceManual/Expressions.md#grammar_function-call-argument-list) `]`

>**Grammar of a forced-value expression**
>
>forced-value-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `!`

>**Grammar of an optional-chaining expression**
>
>optional-chaining-expression → [postfix-expression](../ReferenceManual/Expressions.md#grammar_postfix-expression) `?`

Statements
----------

>**Grammar of a statement**
>
>statement → [expression](../ReferenceManual/Expressions.md#grammar_expression) `;`<sub>opt</sub>
>
>statement → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) `;`<sub>opt</sub>
>
>statement → [loop-statement](../ReferenceManual/Statements.md#grammar_loop-statement) `;`<sub>opt</sub>
>
>statement → [branch-statement](../ReferenceManual/Statements.md#grammar_branch-statement) `;`<sub>opt</sub>
>
>statement → [labeled-statement](../ReferenceManual/Statements.md#grammar_labeled-statement) `;`<sub>opt</sub>
>
>statement → [control-transfer-statement](../ReferenceManual/Statements.md#grammar_control-transfer-statement) `;`<sub>opt</sub>
>
>statement → [defer-statement](../ReferenceManual/Statements.md#grammar_defer-statement) `;`<sub>opt</sub>
>
>statement → [do-statement](../ReferenceManual/Statements.md#grammar_do-statement) `;`<sub>opt</sub>
>
>statement → [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)
>
>statements → [statement](../ReferenceManual/Statements.md#grammar_statement) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>

>**Grammar of a loop statement**
>
>loop-statement → [for-in-statement](../ReferenceManual/Statements.md#grammar_for-in-statement)
>
>loop-statement → [while-statement](../ReferenceManual/Statements.md#grammar_while-statement)
>
>loop-statement → [repeat-while-statement](../ReferenceManual/Statements.md#grammar_repeat-while-statement)

>**Grammar of a for-in statement**
>
>for-in-statement → `for` `case`<sub>opt</sub> [pattern](../ReferenceManual/Patterns.md#grammar_pattern) `in` [expression](../ReferenceManual/Expressions.md#grammar_expression) [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

>**Grammar of a while statement**
>
>while-statement → `while` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list) [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>condition-list → [condition](../ReferenceManual/Statements.md#grammar_condition) | [condition](../ReferenceManual/Statements.md#grammar_condition) `,` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list)
>
>condition → [expression](../ReferenceManual/Expressions.md#grammar_expression) | [availability-condition](../ReferenceManual/Statements.md#grammar_availability-condition) | [case-condition](../ReferenceManual/Statements.md#grammar_case-condition) | [optional-binding-condition](../ReferenceManual/Statements.md#grammar_optional-binding-condition)
>
>case-condition → `case` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer)
>
>optional-binding-condition → `let` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer) | `var` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer)

>**Grammar of a repeat-while statement**
>
>repeat-while-statement → `repeat` [code-block](../ReferenceManual/Declarations.md#grammar_code-block) `while` [expression](../ReferenceManual/Expressions.md#grammar_expression)

>**Grammar of a branch statement**
>
>branch-statement → [if-statement](../ReferenceManual/Statements.md#grammar_if-statement)
>
>branch-statement → [guard-statement](../ReferenceManual/Statements.md#grammar_guard-statement)
>
>branch-statement → [switch-statement](../ReferenceManual/Statements.md#grammar_switch-statement)

>**Grammar of an if statement**
>
>if-statement → `if` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list) [code-block](../ReferenceManual/Declarations.md#grammar_code-block) [else-clause](../ReferenceManual/Statements.md#grammar_else-clause) <sub>opt</sub>
>
>else-clause → `else` [code-block](../ReferenceManual/Declarations.md#grammar_code-block) | `else` [if-statement](../ReferenceManual/Statements.md#grammar_if-statement)

>**Grammar of a guard statement**
>
>guard-statement → `guard` [condition-list](../ReferenceManual/Statements.md#grammar_condition-list) `else` [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

>**Grammar of a switch statement**
>
>switch-statement → `switch` [expression](../ReferenceManual/Expressions.md#grammar_expression) `{` [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub> `}`
>
>switch-cases → [switch-case](../ReferenceManual/Statements.md#grammar_switch-case) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>
>
>switch-case → [case-label](../ReferenceManual/Statements.md#grammar_case-label) [statements](../ReferenceManual/Statements.md#grammar_statements)
>
>switch-case → [default-label](../ReferenceManual/Statements.md#grammar_default-label) [statements](../ReferenceManual/Statements.md#grammar_statements)
>
>switch-case → [conditional-switch-case](../ReferenceManual/Statements.md#grammar_conditional-switch-case)
>
>case-label → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `case` [case-item-list](../ReferenceManual/Statements.md#grammar_case-item-list) `:`
>
>case-item-list → [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> | [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> `,` [case-item-list](../ReferenceManual/Statements.md#grammar_case-item-list)
>
>default-label → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `default` `:`
>
>where-clause → `where` [where-expression](../ReferenceManual/Statements.md#grammar_where-expression)
>
>where-expression → [expression](../ReferenceManual/Expressions.md#grammar_expression)
>
>conditional-switch-case → [switch-if-directive-clause](../ReferenceManual/Statements.md#grammar_switch-if-directive-clause) [switch-elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_switch-elseif-directive-clauses) <sub>opt</sub> [switch-else-directive-clause](../ReferenceManual/Statements.md#grammar_switch-else-directive-clause) <sub>opt</sub> [endif-directive](../ReferenceManual/Statements.md#grammar_endif-directive)
>
>switch-if-directive-clause → [if-directive](../ReferenceManual/Statements.md#grammar_if-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>
>
>switch-elseif-directive-clauses → [elseif-directive-clause](../ReferenceManual/Statements.md#grammar_elseif-directive-clause) [switch-elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_switch-elseif-directive-clauses) <sub>opt</sub>
>
>switch-elseif-directive-clause → [elseif-directive](../ReferenceManual/Statements.md#grammar_elseif-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>
>
>switch-else-directive-clause → [else-directive](../ReferenceManual/Statements.md#grammar_else-directive) [switch-cases](../ReferenceManual/Statements.md#grammar_switch-cases) <sub>opt</sub>

>**Grammar of a labeled statement**
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [loop-statement](../ReferenceManual/Statements.md#grammar_loop-statement)
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [if-statement](../ReferenceManual/Statements.md#grammar_if-statement)
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [switch-statement](../ReferenceManual/Statements.md#grammar_switch-statement)
>
>labeled-statement → [statement-label](../ReferenceManual/Statements.md#grammar_statement-label) [do-statement](../ReferenceManual/Statements.md#grammar_do-statement)
>
>statement-label → [label-name](../ReferenceManual/Statements.md#grammar_label-name) `:`
>
>label-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of a control transfer statement**
>
>control-transfer-statement → [break-statement](../ReferenceManual/Statements.md#grammar_break-statement)
>
>control-transfer-statement → [continue-statement](../ReferenceManual/Statements.md#grammar_continue-statement)
>
>control-transfer-statement → [fallthrough-statement](../ReferenceManual/Statements.md#grammar_fallthrough-statement)
>
>control-transfer-statement → [return-statement](../ReferenceManual/Statements.md#grammar_return-statement)
>
>control-transfer-statement → [throw-statement](../ReferenceManual/Statements.md#grammar_throw-statement)

>**Grammar of a break statement**
>
>break-statement → `break` [label-name](../ReferenceManual/Statements.md#grammar_label-name) <sub>opt</sub>

>**Grammar of a continue statement**
>
>continue-statement → `continue` [label-name](../ReferenceManual/Statements.md#grammar_label-name) <sub>opt</sub>

>**Grammar of a fallthrough statement**
>
>fallthrough-statement → `fallthrough`

>**Grammar of a return statement**
>
>return-statement → `return` [expression](../ReferenceManual/Expressions.md#grammar_expression) <sub>opt</sub>

>**Grammar of a throw statement**
>
>throw-statement → `throw` [expression](../ReferenceManual/Expressions.md#grammar_expression)

>**Grammar of a defer statement**
>
>defer-statement → `defer` [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

**Grammar of a do statement**
>
>do-statement → `do` [code-block](../ReferenceManual/Declarations.md#grammar_code-block) [catch-clauses](../ReferenceManual/Statements.md#grammar_catch-clauses) <sub>opt</sub>
>
>catch-clauses → [catch-clause](../ReferenceManual/Statements.md#grammar_catch-clause) [catch-clauses](../ReferenceManual/Statements.md#grammar_catch-clauses) <sub>opt</sub>
>
>catch-clause → `catch` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) <sub>opt</sub> [where-clause](../ReferenceManual/Statements.md#grammar_where-clause) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

>**Grammar of a compiler control statement**
>
>compiler-control-statement → [conditional-compilation-block](../ReferenceManual/Statements.md#grammar_conditional-compilation-block)
>
>compiler-control-statement → [line-control-statement](../ReferenceManual/Statements.md#grammar_line-control-statement)
>
>compiler-control-statement → [diagnostic-statement](../ReferenceManual/Statements.md#grammar_diagnostic-statement)

>**Grammar of a conditional compilation block**
>
>conditional-compilation-block → [if-directive-clause](../ReferenceManual/Statements.md#grammar_if-directive-clause) [elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_elseif-directive-clauses) <sub>opt</sub> [else-directive-clause](../ReferenceManual/Statements.md#grammar_else-directive-clause) <sub>opt</sub> [endif-directive](../ReferenceManual/Statements.md#grammar_endif-directive)
>
>if-directive-clause → [if-directive](../ReferenceManual/Statements.md#grammar_if-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>
>
>elseif-directive-clauses → [elseif-directive-clause](../ReferenceManual/Statements.md#grammar_elseif-directive-clause) [elseif-directive-clauses](../ReferenceManual/Statements.md#grammar_elseif-directive-clauses) <sub>opt</sub>
>
>elseif-directive-clause → [elseif-directive](../ReferenceManual/Statements.md#grammar_elseif-directive) [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>
>
>else-directive-clause → [else-directive](../ReferenceManual/Statements.md#grammar_else-directive) [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>
>
>if-directive → `#if`
>
>elseif-directive → `#elseif`
>
>else-directive → `#else`
>
>endif-directive → `#endif`
>
>compilation-condition → [platform-condition](../ReferenceManual/Statements.md#grammar_platform-condition)
>
>compilation-condition → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>compilation-condition → [boolean-literal](../ReferenceManual/LexicalStructure.md#grammar_boolean-literal)
>
>compilation-condition → `(` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) `)`
>
>compilation-condition → `!` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition)
>
>compilation-condition → [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) `&&` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition)
>
>compilation-condition → [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition) `||` [compilation-condition](../ReferenceManual/Statements.md#grammar_compilation-condition)
>
>platform-condition → `os` `(` [operating-system](../ReferenceManual/Statements.md#grammar_operating-system) `)`
>
>platform-condition → `arch` `(` [architecture](../ReferenceManual/Statements.md#grammar_architecture) `)`
>
>platform-condition → `swift` `(` `>=` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)` | `swift` `(` `<` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)`
>
>platform-condition → `compiler` `(` `>=` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)` | `compiler` `(` `<` [swift-version](../ReferenceManual/Statements.md#grammar_swift-version) `)`
>
>platform-condition → `canImport` `(` [module-name](../ReferenceManual/Statements.md#grammar_module-name) `)`
>
>platform-condition → `targetEnvironment` `(` [environment](../ReferenceManual/Statements.md#grammar_environment) `)`
>
>operating-system → `macOS` | `iOS` | `watchOS` | `tvOS`
>
>architecture → `i386` | `x86_64` | `arm` | `arm64`
>
>swift-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) [swift-version-continuation](../ReferenceManual/Statements.md#grammar_swift-version-continuation) <sub>opt</sub>
>
>swift-version-continuation → `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) [swift-version-continuation](../ReferenceManual/Statements.md#grammar_swift-version-continuation) <sub>opt</sub>
>
>module-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>environment → `simulator`

>**Grammar of a line control statement**
>
>line-control-statement → `#sourceLocation` `(` `file:` [file-name](../ReferenceManual/Statements.md#grammar_file-name) `,` `line:` [line-number](../ReferenceManual/Statements.md#grammar_line-number) `)`
>
>line-control-statement → `#sourceLocation` `(` `)`
>
>line-number → A decimal integer greater than zero
>
>file-name → [static-string-literal](../ReferenceManual/LexicalStructure.md#grammar_static-string-literal)

>**Grammar of a compile-time diagnostic statement**
>
>diagnostic-statement → `#error` `(` [diagnostic-message](../ReferenceManual/Statements.md#grammar_diagnostic-message) `)`
>
>diagnostic-statement → `#warning` `(` [diagnostic-message](../ReferenceManual/Statements.md#grammar_diagnostic-message) `)`
>
>diagnostic-message → [static-string-literal](../ReferenceManual/LexicalStructure.md#grammar_static-string-literal)

>**Grammar of an availability condition**
>
>availability-condition → `#available` `(` [availability-arguments](../ReferenceManual/Statements.md#grammar_availability-arguments) `)`
>
>availability-arguments → [availability-argument](../ReferenceManual/Statements.md#grammar_availability-argument) | [availability-argument](../ReferenceManual/Statements.md#grammar_availability-argument) `,` [availability-arguments](../ReferenceManual/Statements.md#grammar_availability-arguments)
>
>availability-argument → [platform-name](../ReferenceManual/Statements.md#grammar_platform-name) [platform-version](../ReferenceManual/Statements.md#grammar_platform-version)
>
>availability-argument → `*`
>
>platform-name → `iOS` | `iOSApplicationExtension`
>
>platform-name → `macOS` | `macOSApplicationExtension`
>
>platform-name → `watchOS`
>
>platform-name → `tvOS`
>
>platform-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)
>
>platform-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)
>
>platform-version → [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits) `.` [decimal-digits](../ReferenceManual/LexicalStructure.md#grammar_decimal-digits)

Declarations
------------

>**Grammar of a declaration**
>
>declaration → [import-declaration](../ReferenceManual/Declarations.md#grammar_import-declaration)
>
>declaration → [constant-declaration](../ReferenceManual/Declarations.md#grammar_constant-declaration)
>
>declaration → [variable-declaration](../ReferenceManual/Declarations.md#grammar_variable-declaration)
>
>declaration → [typealias-declaration](../ReferenceManual/Declarations.md#grammar_typealias-declaration)
>
>declaration → [function-declaration](../ReferenceManual/Declarations.md#grammar_function-declaration)
>
>declaration → [enum-declaration](../ReferenceManual/Declarations.md#grammar_enum-declaration)
>
>declaration → [struct-declaration](../ReferenceManual/Declarations.md#grammar_struct-declaration)
>
>declaration → [class-declaration](../ReferenceManual/Declarations.md#grammar_class-declaration)
>
>declaration → [protocol-declaration](../ReferenceManual/Declarations.md#grammar_protocol-declaration)
>
>declaration → [initializer-declaration](../ReferenceManual/Declarations.md#grammar_initializer-declaration)
>
>declaration → [deinitializer-declaration](../ReferenceManual/Declarations.md#grammar_deinitializer-declaration)
>
>declaration → [extension-declaration](../ReferenceManual/Declarations.md#grammar_extension-declaration)
>
>declaration → [subscript-declaration](../ReferenceManual/Declarations.md#grammar_subscript-declaration)
>
>declaration → [operator-declaration](../ReferenceManual/Declarations.md#grammar_operator-declaration)
>
>declaration → [precedence-group-declaration](../ReferenceManual/Declarations.md#grammar_precedence-group-declaration)
>
>declarations → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) [declarations](../ReferenceManual/Declarations.md#grammar_declarations) <sub>opt</sub>

>**Grammar of a top-level declaration**
>
>top-level-declaration → [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub>

>**Grammar of a code block**
>
>code-block → `{` [statements](../ReferenceManual/Statements.md#grammar_statements) <sub>opt</sub> `}`

>**Grammar of an import declaration**
>
>import-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `import` [import-kind](../ReferenceManual/Declarations.md#grammar_import-kind) <sub>opt</sub> [import-path](../ReferenceManual/Declarations.md#grammar_import-path)
>
>import-kind → `typealias` | `struct` | `class` | `enum` | `protocol` | `let` | `var` | `func`
>
>import-path → [import-path-identifier](../ReferenceManual/Declarations.md#grammar_import-path-identifier) | [import-path-identifier](../ReferenceManual/Declarations.md#grammar_import-path-identifier) `.` [import-path](../ReferenceManual/Declarations.md#grammar_import-path)
>
>import-path-identifier → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) | [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)

>**Grammar of a constant declaration**
>
>constant-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `let` [pattern-initializer-list](../ReferenceManual/Declarations.md#grammar_pattern-initializer-list)
>
>pattern-initializer-list → [pattern-initializer](../ReferenceManual/Declarations.md#grammar_pattern-initializer) | [pattern-initializer](../ReferenceManual/Declarations.md#grammar_pattern-initializer) `,` [pattern-initializer-list](../ReferenceManual/Declarations.md#grammar_pattern-initializer-list)
>
>pattern-initializer → [pattern](../ReferenceManual/Patterns.md#grammar_pattern) [initializer](../ReferenceManual/Declarations.md#grammar_initializer) <sub>opt</sub>
>
>initializer → `=` [expression](../ReferenceManual/Expressions.md#grammar_expression)

>**Grammar of a variable declaration**
>
>variable-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [pattern-initializer-list](../ReferenceManual/Declarations.md#grammar_pattern-initializer-list)
>
>variable-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [variable-name](../ReferenceManual/Declarations.md#grammar_variable-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>variable-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [variable-name](../ReferenceManual/Declarations.md#grammar_variable-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) [getter-setter-block](../ReferenceManual/Declarations.md#grammar_getter-setter-block)
>
>variable-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [variable-name](../ReferenceManual/Declarations.md#grammar_variable-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) [getter-setter-keyword-block](../ReferenceManual/Declarations.md#grammar_getter-setter-keyword-block)
>
>variable-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [variable-name](../ReferenceManual/Declarations.md#grammar_variable-name) [initializer](../ReferenceManual/Declarations.md#grammar_initializer) [willSet-didSet-block](../ReferenceManual/Declarations.md#grammar_willSet-didSet-block)
>
>variable-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [variable-name](../ReferenceManual/Declarations.md#grammar_variable-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) [initializer](../ReferenceManual/Declarations.md#grammar_initializer) opt [willSet-didSet-block](../ReferenceManual/Declarations.md#grammar_willSet-didSet-block)
>
>variable-declaration-head → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `var`
>
>variable-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>getter-setter-block → [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>getter-setter-block → `{` [getter-clause](../ReferenceManual/Declarations.md#grammar_getter-clause) [setter-clause](../ReferenceManual/Declarations.md#grammar_setter-clause) <sub>opt</sub> `}`
>
>getter-setter-block → `{` [setter-clause](../ReferenceManual/Declarations.md#grammar_setter-clause) [getter-clause](../ReferenceManual/Declarations.md#grammar_getter-clause) `}`
>
>getter-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [mutation-modifier](../ReferenceManual/Declarations.md#grammar_mutation-modifier) <sub>opt</sub> `get` [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>setter-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [mutation-modifier](../ReferenceManual/Declarations.md#grammar_mutation-modifier) <sub>opt</sub> `set` [setter-name](../ReferenceManual/Declarations.md#grammar_setter-name) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>setter-name → `(` [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `)`
>
>getter-setter-keyword-block → `{` [getter-keyword-clause](../ReferenceManual/Declarations.md#grammar_getter-keyword-clause) [setter-keyword-clause](../ReferenceManual/Declarations.md#grammar_setter-keyword-clause) <sub>opt</sub> `}`
>
>getter-setter-keyword-block → `{` [setter-keyword-clause](../ReferenceManual/Declarations.md#grammar_setter-keyword-clause) [getter-keyword-clause](../ReferenceManual/Declarations.md#grammar_getter-keyword-clause) `}`
>
>getter-keyword-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [mutation-modifier](../ReferenceManual/Declarations.md#grammar_mutation-modifier) <sub>opt</sub> `get`
>
>setter-keyword-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [mutation-modifier](../ReferenceManual/Declarations.md#grammar_mutation-modifier) <sub>opt</sub> `set`
>
>willSet-didSet-block → `{` [willSet-clause](../ReferenceManual/Declarations.md#grammar_willSet-clause) [didSet-clause](../ReferenceManual/Declarations.md#grammar_didSet-clause) <sub>opt</sub> `}`
>
>willSet-didSet-block → `{` [didSet-clause](../ReferenceManual/Declarations.md#grammar_didSet-clause) [willSet-clause](../ReferenceManual/Declarations.md#grammar_willSet-clause) <sub>opt</sub> `}`
>
>willSet-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `willSet` [setter-name](../ReferenceManual/Declarations.md#grammar_setter-name) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>didSet-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `didSet` [setter-name](../ReferenceManual/Declarations.md#grammar_setter-name) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

>**Grammar of a type alias declaration**
>
>typealias-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `typealias` [typealias-name](../ReferenceManual/Declarations.md#grammar_typealias-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [typealias-assignment](../ReferenceManual/Declarations.md#grammar_typealias-assignment)
>
>typealias-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>typealias-assignment → `=` [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of a function declaration**
>
>function-declaration → [function-head](../ReferenceManual/Declarations.md#grammar_function-head) [function-name](../ReferenceManual/Declarations.md#grammar_function-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [function-signature](../ReferenceManual/Declarations.md#grammar_function-signature) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [function-body](../ReferenceManual/Declarations.md#grammar_function-body) <sub>opt</sub>
>
>function-head → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `func`
>
>function-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) | [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)
>
>function-signature → [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause) `throws`<sub>opt</sub> [function-result](../ReferenceManual/Declarations.md#grammar_function-result) <sub>opt</sub>
>
>function-signature → [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause) `rethrows` [function-result](../ReferenceManual/Declarations.md#grammar_function-result) <sub>opt</sub>
>
>function-result → `->` [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [type](../ReferenceManual/Types.md#grammar_type)
>
>function-body → [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>parameter-clause → `(` `)` | `(` [parameter-list](../ReferenceManual/Declarations.md#grammar_parameter-list) `)`
>
>parameter-list → [parameter](../ReferenceManual/Declarations.md#grammar_parameter) | [parameter](../ReferenceManual/Declarations.md#grammar_parameter) `,` [parameter-list](../ReferenceManual/Declarations.md#grammar_parameter-list)
>
>parameter → [external-parameter-name](../ReferenceManual/Declarations.md#grammar_external-parameter-name) <sub>opt</sub> [local-parameter-name](../ReferenceManual/Declarations.md#grammar_local-parameter-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) [default-argument-clause](../ReferenceManual/Declarations.md#grammar_default-argument-clause) <sub>opt</sub>
>
>parameter → [external-parameter-name](../ReferenceManual/Declarations.md#grammar_external-parameter-name) <sub>opt</sub> [local-parameter-name](../ReferenceManual/Declarations.md#grammar_local-parameter-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation)
>
>parameter → [external-parameter-name](../ReferenceManual/Declarations.md#grammar_external-parameter-name) <sub>opt</sub> [local-parameter-name](../ReferenceManual/Declarations.md#grammar_local-parameter-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) `...`
>
>external-parameter-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>local-parameter-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>default-argument-clause → `=` [expression](../ReferenceManual/Expressions.md#grammar_expression)

>**Grammar of an enumeration declaration**
>
>enum-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> [union-style-enum](../ReferenceManual/Declarations.md#grammar_union-style-enum)
>
>enum-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> [raw-value-style-enum](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum)
>
>union-style-enum → `indirect`<sub>opt</sub> `enum` [enum-name](../ReferenceManual/Declarations.md#grammar_enum-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> `{` [union-style-enum-members](../ReferenceManual/Declarations.md#grammar_union-style-enum-members) <sub>opt</sub> `}`
>
>union-style-enum-members → [union-style-enum-member](../ReferenceManual/Declarations.md#grammar_union-style-enum-member) [union-style-enum-members](../ReferenceManual/Declarations.md#grammar_union-style-enum-members) <sub>opt</sub>
>
>union-style-enum-member → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) | [union-style-enum-case-clause](../ReferenceManual/Declarations.md#grammar_union-style-enum-case-clause) | [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)
>
>union-style-enum-case-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `indirect`<sub>opt</sub> `case` [union-style-enum-case-list](../ReferenceManual/Declarations.md#grammar_union-style-enum-case-list)
>
>union-style-enum-case-list → [union-style-enum-case](../ReferenceManual/Declarations.md#grammar_union-style-enum-case) | [union-style-enum-case](../ReferenceManual/Declarations.md#grammar_union-style-enum-case) `,` [union-style-enum-case-list](../ReferenceManual/Declarations.md#grammar_union-style-enum-case-list)
>
>union-style-enum-case → [enum-case-name](../ReferenceManual/Declarations.md#grammar_enum-case-name) [tuple-type](../ReferenceManual/Types.md#grammar_tuple-type) <sub>opt</sub>
>
>enum-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>enum-case-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>raw-value-style-enum → `enum` [enum-name](../ReferenceManual/Declarations.md#grammar_enum-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> `{` [raw-value-style-enum-members](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-members) `}`
>
>raw-value-style-enum-members → [raw-value-style-enum-member](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-member) [raw-value-style-enum-members](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-members) <sub>opt</sub>
>
>raw-value-style-enum-member → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) | [raw-value-style-enum-case-clause](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-case-clause) | [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)
>
>raw-value-style-enum-case-clause → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `case` [raw-value-style-enum-case-list](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-case-list)
>
>raw-value-style-enum-case-list → [raw-value-style-enum-case](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-case) | [raw-value-style-enum-case](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-case) `,` [raw-value-style-enum-case-list](../ReferenceManual/Declarations.md#grammar_raw-value-style-enum-case-list)
>
>raw-value-style-enum-case → [enum-case-name](../ReferenceManual/Declarations.md#grammar_enum-case-name) [raw-value-assignment](../ReferenceManual/Declarations.md#grammar_raw-value-assignment) <sub>opt</sub>
>
>raw-value-assignment → `=` [raw-value-literal](../ReferenceManual/Declarations.md#grammar_raw-value-literal)
>
>raw-value-literal → [numeric-literal](../ReferenceManual/LexicalStructure.md#grammar_numeric-literal) | [static-string-literal](../ReferenceManual/LexicalStructure.md#grammar_static-string-literal) | [boolean-literal](../ReferenceManual/LexicalStructure.md#grammar_boolean-literal)

>**Grammar of a structure declaration**
>
>struct-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `struct` [struct-name](../ReferenceManual/Declarations.md#grammar_struct-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [struct-body](../ReferenceManual/Declarations.md#grammar_struct-body)
>
>struct-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>struct-body → `{` [struct-members](../ReferenceManual/Declarations.md#grammar_struct-members) <sub>opt</sub> `}`
>
>struct-members → [struct-member](../ReferenceManual/Declarations.md#grammar_struct-member) [struct-members](../ReferenceManual/Declarations.md#grammar_struct-members) <sub>opt</sub>
>
>struct-member → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) | [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)

>**Grammar of a class declaration**
>
>class-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `final`<sub>opt</sub> `class` [class-name](../ReferenceManual/Declarations.md#grammar_class-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [class-body](../ReferenceManual/Declarations.md#grammar_class-body)
>
>class-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `final` [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `class` [class-name](../ReferenceManual/Declarations.md#grammar_class-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [class-body](../ReferenceManual/Declarations.md#grammar_class-body)
>
>class-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>class-body → `{` [class-members](../ReferenceManual/Declarations.md#grammar_class-members) <sub>opt</sub> `}`
>
>class-members → [class-member](../ReferenceManual/Declarations.md#grammar_class-member) [class-members](../ReferenceManual/Declarations.md#grammar_class-members) <sub>opt</sub>
>
>class-member → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) | [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)

>**Grammar of a protocol declaration**
>
>protocol-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `protocol` [protocol-name](../ReferenceManual/Declarations.md#grammar_protocol-name) [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [protocol-body](../ReferenceManual/Declarations.md#grammar_protocol-body)
>
>protocol-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>protocol-body → `{` [protocol-members](../ReferenceManual/Declarations.md#grammar_protocol-members) <sub>opt</sub> `}`
>
>protocol-members → [protocol-member](../ReferenceManual/Declarations.md#grammar_protocol-member) [protocol-members](../ReferenceManual/Declarations.md#grammar_protocol-members) <sub>opt</sub>
>
>protocol-member → [protocol-member-declaration](../ReferenceManual/Declarations.md#grammar_protocol-member-declaration) | [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)
>
>protocol-member-declaration → [protocol-property-declaration](../ReferenceManual/Declarations.md#grammar_protocol-property-declaration)
>
>protocol-member-declaration → [protocol-method-declaration](../ReferenceManual/Declarations.md#grammar_protocol-method-declaration)
>
>protocol-member-declaration → [protocol-initializer-declaration](../ReferenceManual/Declarations.md#grammar_protocol-initializer-declaration)
>
>protocol-member-declaration → [protocol-subscript-declaration](../ReferenceManual/Declarations.md#grammar_protocol-subscript-declaration)
>
>protocol-member-declaration → [protocol-associated-type-declaration](../ReferenceManual/Declarations.md#grammar_protocol-associated-type-declaration)
>
>protocol-member-declaration → [typealias-declaration](../ReferenceManual/Declarations.md#grammar_typealias-declaration)

>**Grammar of a protocol property declaration**
>
>protocol-property-declaration → [variable-declaration-head](../ReferenceManual/Declarations.md#grammar_variable-declaration-head) [variable-name](../ReferenceManual/Declarations.md#grammar_variable-name) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) [getter-setter-keyword-block](../ReferenceManual/Declarations.md#grammar_getter-setter-keyword-block)

>**Grammar of a protocol method declaration**
>
>protocol-method-declaration → [function-head](../ReferenceManual/Declarations.md#grammar_function-head) [function-name](../ReferenceManual/Declarations.md#grammar_function-name) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [function-signature](../ReferenceManual/Declarations.md#grammar_function-signature) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub>

>**Grammar of a protocol initializer declaration**
>
>protocol-initializer-declaration → [initializer-head](../ReferenceManual/Declarations.md#grammar_initializer-head) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause) `throws`<sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub>
>
>protocol-initializer-declaration → [initializer-head](../ReferenceManual/Declarations.md#grammar_initializer-head) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause) `rethrows` [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub>

>**Grammar of a protocol subscript declaration**
>
>protocol-subscript-declaration → [subscript-head](../ReferenceManual/Declarations.md#grammar_subscript-head) [subscript-result](../ReferenceManual/Declarations.md#grammar_subscript-result) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [getter-setter-keyword-block](../ReferenceManual/Declarations.md#grammar_getter-setter-keyword-block)

>**Grammar of a protocol associated type declaration**
>
>protocol-associated-type-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) opt [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `associatedtype` [typealias-name](../ReferenceManual/Declarations.md#grammar_typealias-name) [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [typealias-assignment](../ReferenceManual/Declarations.md#grammar_typealias-assignment) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub>

>**Grammar of an initializer declaration**
>
>initializer-declaration → [initializer-head](../ReferenceManual/Declarations.md#grammar_initializer-head) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause) `throws`<sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [initializer-body](../ReferenceManual/Declarations.md#grammar_initializer-body)
>
>initializer-declaration → [initializer-head](../ReferenceManual/Declarations.md#grammar_initializer-head) [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause) `rethrows` [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [initializer-body](../ReferenceManual/Declarations.md#grammar_initializer-body)
>
>initializer-head → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `init`
>
>initializer-head → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `init` `?`
>
>initializer-head → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `init` `!`
>
>initializer-body → [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

>**Grammar of a deinitializer declaration**
>
>deinitializer-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> `deinit` [code-block](../ReferenceManual/Declarations.md#grammar_code-block)

>**Grammar of an extension declaration**
>
>extension-declaration → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier) <sub>opt</sub> `extension` [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) [type-inheritance-clause](../ReferenceManual/Types.md#grammar_type-inheritance-clause) <sub>opt</sub> [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [extension-body](../ReferenceManual/Declarations.md#grammar_extension-body)
>
>extension-body → `{` [extension-members](../ReferenceManual/Declarations.md#grammar_extension-members) <sub>opt</sub> `}`
>
>extension-members → [extension-member](../ReferenceManual/Declarations.md#grammar_extension-member) [extension-members](../ReferenceManual/Declarations.md#grammar_extension-members) <sub>opt</sub>
>
>extension-member → [declaration](../ReferenceManual/Declarations.md#grammar_declaration) | [compiler-control-statement](../ReferenceManual/Statements.md#grammar_compiler-control-statement)

>**Grammar of a subscript declaration**
>
>subscript-declaration → [subscript-head](../ReferenceManual/Declarations.md#grammar_subscript-head) [subscript-result](../ReferenceManual/Declarations.md#grammar_subscript-result) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [code-block](../ReferenceManual/Declarations.md#grammar_code-block)
>
>subscript-declaration → [subscript-head](../ReferenceManual/Declarations.md#grammar_subscript-head) [subscript-result](../ReferenceManual/Declarations.md#grammar_subscript-result) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [getter-setter-block](../ReferenceManual/Declarations.md#grammar_getter-setter-block)
>
>subscript-declaration → [subscript-head](../ReferenceManual/Declarations.md#grammar_subscript-head) [subscript-result](../ReferenceManual/Declarations.md#grammar_subscript-result) [generic-where-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-where-clause) <sub>opt</sub> [getter-setter-keyword-block](../ReferenceManual/Declarations.md#grammar_getter-setter-keyword-block)
>
>subscript-head → [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub> `subscript` [generic-parameter-clause](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-clause) <sub>opt</sub> [parameter-clause](../ReferenceManual/Declarations.md#grammar_parameter-clause)
>
>subscript-result → `->` [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub> [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of an operator declaration**
>
>operator-declaration → [prefix-operator-declaration](../ReferenceManual/Declarations.md#grammar_prefix-operator-declaration) | [postfix-operator-declaration](../ReferenceManual/Declarations.md#grammar_postfix-operator-declaration) | [infix-operator-declaration](../ReferenceManual/Declarations.md#grammar_infix-operator-declaration)
>
>prefix-operator-declaration → `prefix` `operator` [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)
>
>postfix-operator-declaration → `postfix` `operator` [operator](../ReferenceManual/LexicalStructure.md#grammar_operator)
>
>infix-operator-declaration → `infix` `operator` [operator](../ReferenceManual/LexicalStructure.md#grammar_operator) [infix-operator-group](../ReferenceManual/Declarations.md#grammar_infix-operator-group) <sub>opt</sub>
>
>infix-operator-group → `:` [precedence-group-name](../ReferenceManual/Declarations.md#grammar_precedence-group-name)

>**Grammar of a precedence group declaration**
>
>precedence-group-declaration → `precedencegroup` [precedence-group-name](../ReferenceManual/Declarations.md#grammar_precedence-group-name) `{` [precedence-group-attributes](../ReferenceManual/Declarations.md#grammar_precedence-group-attributes) <sub>opt</sub> `}`
>
>precedence-group-attributes → [precedence-group-attribute](../ReferenceManual/Declarations.md#grammar_precedence-group-attribute) [precedence-group-attributes](../ReferenceManual/Declarations.md#grammar_precedence-group-attributes) <sub>opt</sub>
>
>precedence-group-attribute → [precedence-group-relation](../ReferenceManual/Declarations.md#grammar_precedence-group-relation)
>
>precedence-group-attribute → [precedence-group-assignment](../ReferenceManual/Declarations.md#grammar_precedence-group-assignment)
>
>precedence-group-attribute → [precedence-group-associativity](../ReferenceManual/Declarations.md#grammar_precedence-group-associativity)
>
>precedence-group-relation → `higherThan` `:` [precedence-group-names](../ReferenceManual/Declarations.md#grammar_precedence-group-names)
>
>precedence-group-relation → `lowerThan` `:` [precedence-group-names](../ReferenceManual/Declarations.md#grammar_precedence-group-names)
>
>precedence-group-assignment → `assignment` `:` [boolean-literal](../ReferenceManual/LexicalStructure.md#grammar_boolean-literal)
>
>precedence-group-associativity → `associativity` `:` `left`
>
>precedence-group-associativity → `associativity` `:` `right`
>
>precedence-group-associativity → `associativity` `:` `none`
>
>precedence-group-names → [precedence-group-name](../ReferenceManual/Declarations.md#grammar_precedence-group-name) | [precedence-group-name](../ReferenceManual/Declarations.md#grammar_precedence-group-name) `,` [precedence-group-names](../ReferenceManual/Declarations.md#grammar_precedence-group-names)
>
>precedence-group-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of a declaration modifier**
>
>declaration-modifier → `class` | `convenience` | `dynamic` | `final` | `infix` | `lazy` | `optional` | `override` | `postfix` | `prefix` | `required` | `static` | `unowned` | `unowned` `(` `safe` `)` | `unowned` `(` `unsafe` `)` | `weak`
>
>declaration-modifier → [access-level-modifier](../ReferenceManual/Declarations.md#grammar_access-level-modifier)
>
>declaration-modifier → [mutation-modifier](../ReferenceManual/Declarations.md#grammar_mutation-modifier)
>
>declaration-modifiers → [declaration-modifier](../ReferenceManual/Declarations.md#grammar_declaration-modifier) [declaration-modifiers](../ReferenceManual/Declarations.md#grammar_declaration-modifiers) <sub>opt</sub>
>
>access-level-modifier → `private` | `private` `(` `set` `)`
>
>access-level-modifier → `fileprivate` | `fileprivate` `(` `set` `)`
>
>access-level-modifier → `internal` | `internal` `(` `set` `)`
>
>access-level-modifier → `public` | `public` `(` `set` `)`
>
>access-level-modifier → `open` | `open` `(` `set` `)`
>
>mutation-modifier → `mutating` | `nonmutating`

Attributes
----------

>**Grammar of an attribute**
>
>attribute → `@` [attribute-name](../ReferenceManual/Attributes.md#grammar_attribute-name) [attribute-argument-clause](../ReferenceManual/Attributes.md#grammar_attribute-argument-clause) <sub>opt</sub>
>
>attribute-name → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)
>
>attribute-argument-clause → `(` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `)`
>
>attributes → [attribute](../ReferenceManual/Attributes.md#grammar_attribute) [attributes](../ReferenceManual/Attributes.md#grammar_attributes) <sub>opt</sub>
>
>balanced-tokens → [balanced-token](../ReferenceManual/Attributes.md#grammar_balanced-token) [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub>
>
>balanced-token → `(` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `)`
>
>balanced-token → `[` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `]`
>
>balanced-token → `{` [balanced-tokens](../ReferenceManual/Attributes.md#grammar_balanced-tokens) <sub>opt</sub> `}`
>
>balanced-token → Any identifier, keyword, literal, or operator
>
>balanced-token → Any punctuation except `(`, `)`, `[`, `]`, `{`, or `}`

Patterns
--------

>**Grammar of a pattern**
>
>pattern → [wildcard-pattern](../ReferenceManual/Patterns.md#grammar_wildcard-pattern) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) <sub>opt</sub>
>
>pattern → [identifier-pattern](../ReferenceManual/Patterns.md#grammar_identifier-pattern) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) <sub>opt</sub>
>
>pattern → [value-binding-pattern](../ReferenceManual/Patterns.md#grammar_value-binding-pattern)
>
>pattern → [tuple-pattern](../ReferenceManual/Patterns.md#grammar_tuple-pattern) [type-annotation](../ReferenceManual/Types.md#grammar_type-annotation) <sub>opt</sub>
>
>pattern → [enum-case-pattern](../ReferenceManual/Patterns.md#grammar_enum-case-pattern)
>
>pattern → [optional-pattern](../ReferenceManual/Patterns.md#grammar_optional-pattern)
>
>pattern → [type-casting-pattern](../ReferenceManual/Patterns.md#grammar_type-casting-pattern)
>
>pattern → [expression-pattern](../ReferenceManual/Patterns.md#grammar_expression-pattern)

>**Grammar of a wildcard pattern**
>
>wildcard-pattern → `_`

>**Grammar of an identifier pattern**
>
>identifier-pattern → [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier)

>**Grammar of a value-binding pattern**
>
>value-binding-pattern → `var` [pattern](../ReferenceManual/Patterns.md#grammar_pattern) | `let` [pattern](../ReferenceManual/Patterns.md#grammar_pattern)

>**Grammar of a tuple pattern**
>
>tuple-pattern → `(` [tuple-pattern-element-list](../ReferenceManual/Patterns.md#grammar_tuple-pattern-element-list) <sub>opt</sub> `)`
>
>tuple-pattern-element-list → [tuple-pattern-element](../ReferenceManual/Patterns.md#grammar_tuple-pattern-element) | [tuple-pattern-element](../ReferenceManual/Patterns.md#grammar_tuple-pattern-element) `,` [tuple-pattern-element-list](../ReferenceManual/Patterns.md#grammar_tuple-pattern-element-list)
>
>tuple-pattern-element → [pattern](../ReferenceManual/Patterns.md#grammar_pattern) | [identifier](../ReferenceManual/LexicalStructure.md#grammar_identifier) `:` [pattern](../ReferenceManual/Patterns.md#grammar_pattern)

>**Grammar of an enumeration case pattern**
>
>enum-case-pattern → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) <sub>opt</sub> `.` [enum-case-name](../ReferenceManual/Declarations.md#grammar_enum-case-name) [tuple-pattern](../ReferenceManual/Patterns.md#grammar_tuple-pattern) <sub>opt</sub>

>**Grammar of an optional pattern**
>
>optional-pattern → [identifier-pattern](../ReferenceManual/Patterns.md#grammar_identifier-pattern) `?`

>**Grammar of a type casting pattern**
>
>type-casting-pattern → [is-pattern](../ReferenceManual/Patterns.md#grammar_is-pattern) | [as-pattern](../ReferenceManual/Patterns.md#grammar_as-pattern)
>
>is-pattern → `is` [type](../ReferenceManual/Types.md#grammar_type)
>
>as-pattern → [pattern](../ReferenceManual/Patterns.md#grammar_pattern) `as` [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of an expression pattern**
>
>expression-pattern → [expression](../ReferenceManual/Expressions.md#grammar_expression)

Generic Parameters and Arguments
--------------------------------

>**Grammar of a generic parameter clause**
>
>generic-parameter-clause → `<` [generic-parameter-list](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-list) `>`
>
>generic-parameter-list → [generic-parameter](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter) | [generic-parameter](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter) `,` [generic-parameter-list](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-parameter-list)
>
>generic-parameter → [type-name](../ReferenceManual/Types.md#grammar_type-name)
>
>generic-parameter → [type-name](../ReferenceManual/Types.md#grammar_type-name) `:` [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier)
>
>generic-parameter → [type-name](../ReferenceManual/Types.md#grammar_type-name) `:` [protocol-composition-type](../ReferenceManual/Types.md#grammar_protocol-composition-type)
>
>generic-where-clause → `where` [requirement-list](../ReferenceManual/GenericParametersAndArguments.md#grammar_requirement-list)
>
>requirement-list → [requirement](../ReferenceManual/GenericParametersAndArguments.md#grammar_requirement) | [requirement](../ReferenceManual/GenericParametersAndArguments.md#grammar_requirement) `,` [requirement-list](../ReferenceManual/GenericParametersAndArguments.md#grammar_requirement-list)
>
>requirement → [conformance-requirement](../ReferenceManual/GenericParametersAndArguments.md#grammar_conformance-requirement) | [same-type-requirement](../ReferenceManual/GenericParametersAndArguments.md#grammar_same-type-requirement)
>
>conformance-requirement → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) `:` [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier)
>
>conformance-requirement → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) `:` [protocol-composition-type](../ReferenceManual/Types.md#grammar_protocol-composition-type)
>
>same-type-requirement → [type-identifier](../ReferenceManual/Types.md#grammar_type-identifier) `==` [type](../ReferenceManual/Types.md#grammar_type)

>**Grammar of a generic argument clause**
>
>generic-argument-clause → `<` [generic-argument-list](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument-list) `>`
>
>generic-argument-list → [generic-argument](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument) | [generic-argument](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument) `,` [generic-argument-list](../ReferenceManual/GenericParametersAndArguments.md#grammar_generic-argument-list)
>
>generic-argument → [type](../ReferenceManual/Types.md#grammar_type)