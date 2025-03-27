# OBJETIVO

Desenvolver um **analisador léxico** e um **analisador sintático** para uma linguagem de programação própria.

# ESPECIFICAÇÕES

## Especificação Léxica

A análise léxica será responsável por identificar os tokens da linguagem a partir de expressões regulares e de sua representação por autômatos finitos.

- **Ferramentas teóricas utilizadas:**
  - Expressões Regulares (ER)
  - Autômatos Finitos Determinísticos (AFD)
  - Autômatos Finitos Não Determinísticos (AFN) e método de Thompson (quando necessário)

- **Tokens previstos:**
  - **Palavras-chave:** `if`, `else`, `while`, `for`, `read`, `write`, `begin`, `end`, etc.
  - **Operadores:**
    - Aritméticos: `+`, `-`, `*`, `/`, `mod`
    - Relacionais: `=`, `!=`, `<=`, `>=`, `<`, `>`
    - Lógicos: `and`, `or`, `not`
  - **Identificadores:** `[a-zA-Z_][a-zA-Z0-9_]*`
  - **Números inteiros e reais** (definidos por ER específicas)
  - **Constantes de caractere**
  - **Símbolos especiais:** `;`, `:`, `,`, `(`, `)`, `{`, `}`, `.`

## Especificação Sintática

A análise sintática será construída com base em uma gramática livre de contexto (CFG), formalmente especificada em BNF (Backus-Naur Form).

- **Objetivo:** definir as regras de derivação válidas da linguagem, garantindo que a combinação dos tokens resulte em sentenças sintaticamente corretas.

- **Exemplos de construções sintáticas:**
  - Comandos de atribuição
  - Comandos condicionais (`if`, `else`)
  - Estruturas de repetição (`while`, `for`)
  - Blocos de código delimitados por `begin/end` ou `{}`

# TABELA DE TOKENS

| **Nome do Token**   | **Expressão Regular**      | **Exemplo reconhecido**   | **Característica**                                 |
|---------------------|----------------------------|---------------------------|----------------------------------------------------|
| `TK_IF`             | `if`                       | `if`                      | Palavras reservadas / Comandos de Condicional      |
| `TK_THEN`           | `then`                     | `then`                    | Palavras reservadas / Comandos de Condicional      |
| `TK_ELSE`           | `else`                     | `else`                    | Palavras reservadas / Comandos de Condicional      |
| `TK_ELSE_IF`        | `elif`                     | `elif`                    | Palavras reservadas / Comandos de Condicional      |
| `TK_INIT`           | `init`                     | `init`                    | Palavras reservadas / Blocos de comandos           |
| `TK_FINISH`         | `finish`                   | `finish`                  | Palavras reservadas / Blocos de comandos           |
| `TK_STOP`           | `stop`                     | `stop`                    | Palavras reservadas / Blocos de comandos           |
| `TK_KEEP`           | `keep`                     | `keep`                    | Palavras reservadas / Blocos de comandos           |
| `TK_WHILE`          | `while`                    | `while`                   | Palavras reservadas / Comandos de Repetição        |
| `TK_FOR`            | `for`                      | `for`                     | Palavras reservadas / Comandos de Repetição        |
| `TK_DO`             | `do`                       | `do`                      | Palavras reservadas                                |
| `TK_RETURN`         | `return`                   | `return`                  | Palavras reservadas                                |
| `TK_TRUE`           | `true`                     | `true`                    | Palavras reservadas / Tipos de dados               |
| `TK_FALSE`          | `false`                    | `false`                   | Palavras reservadas / Tipos de dados               |
| `TK_SCAN`           | `scan`                     | `scan`                    | Palavras reservadas / Comandos de Entrada e saída  |
| `TK_PRINT`          | `print`                    | `print`                   | Palavras reservadas / Comandos de Entrada e saída  |
| `TK_OPEN_C_BRACKET` | `{`                        | `{`                       | Blocos de comandos / Símbolos especiais            |
| `TK_CLOSE_C_BRACKET`| `}`                        | `}`                       | Blocos de comandos / Símbolos especiais            |
| `TK_OPEN_B_BRACKET` | `[`                        | `[`                       | Blocos de comandos / Símbolos especiais            |
| `TK_CLOSE_B_BRACKET`| `]`                        | `]`                       | Blocos de comandos / Símbolos especiais            |
| `TK_OPEN_R_BRACKET` | `(`                        | `(`                       | Blocos de comandos / Símbolos especiais            |
| `TK_CLOSE_R_BRACKET`| `)`                        | `)`                       | Blocos de comandos / Símbolos especiais            |
| `TK_IDENT`          | `[a-zA-Z_][a-zA-Z0-9_]*`   | `variavel1`, `_soma`      | Identificadores                                    |
| `TK_INT`            | `[0-9]+`                   | `42`                      | Tipos de dados                                     |
| `TK_FLOAT`          | `[0-9]+\.[0-9]+`           | `3.14`                    | Tipos de dados                                     |
| `TK_CHAR`           | `'.'`                      | `'a'`                     | Tipos de dados                                     |
| `TK_STRING`         | `"[^"]*"`                  | `"oi"`                    | Tipos de dados                                     |
| `TK_ASSIGN`         | `=`                        | `=`                       | Comandos de Atribuição                             |
| `TK_PLUS`           | `+`                        | `+`                       | Operadores aritméticos                             |
| `TK_MINUS`          | `-`                        | `-`                       | Operadores aritméticos                             |
| `TK_MULT`           | `*`                        | `*`                       | Operadores aritméticos                             |
| `TK_DIV`            | `/`                        | `/`                       | Operadores aritméticos                             |
| `TK_MOD`            | `%`                        | `%`                       | Operadores aritméticos                             |
| `TK_EXP`            | `^`                        | `^`                       | Operadores aritméticos                             |
| `TK_LOG`            | `log`                      | `log`                     | Operadores aritméticos                             |
| `TK_EEXP`           | `e^`                       | `e^`                      | Operadores aritméticos                             |
| `TK_LN`             | `ln`                       | `ln`                      | Operadores aritméticos                             |
| `TK_INC`            | `++`                       | `++`                      | Operadores aritméticos                             |
| `TK_DEC`            | `--`                       | `--`                      | Operadores aritméticos                             |
| `TK_ADD_ASSIGN`     | `+=`                       | `+=`                      | Operadores aritméticos                             |
| `TK_SUB_ASSIGN`     | `-=`                       | `-=`                      | Operadores aritméticos                             |
| `TK_MUL_ASSIGN`     | `*=`                       | `*=`                      | Operadores aritméticos                             |
| `TK_DIV_ASSIGN`     | `/=`                       | `/=`                      | Operadores aritméticos                             |
| `TK_EQ`             | `==`                       | `==`                      | Operadores relacionais                             |
| `TK_NEQ`            | `!=`                       | `!=`                      | Operadores relacionais                             |
| `TK_LT`             | `<`                        | `<`                       | Operadores relacionais                             |
| `TK_GT`             | `>`                        | `>`                       | Operadores relacionais                             |
| `TK_LE`             | `<=`                       | `<=`                      | Operadores relacionais                             |
| `TK_GE`             | `>=`                       | `>=`                      | Operadores relacionais                             |
| `TK_AND`            | `&`                        | `&`                       | Operadores lógicos                                 |
| `TK_OR`             | `\|`                       | `\|`                      | Operadores lógicos                                 |
| `TK_NOT`            | `!`                        | `!`                       | Operadores lógicos                                 |
| `TK_COLON`          | `:`                        | `:`                       | Símbolos especiais                                 |
| `TK_SEMICOLON`      | `;`                        | `;`                       | Símbolos especiais                                 |
| `TK_COMMA`          | `,`                        | `,`                       | Símbolos especiais                                 |
| `TK_DOT`            | `.`                        | `.`                       | Símbolos especiais                                 |
| `TK_COMMENT`        | `#`                        | `# este é o comantário`   | Comentários em linha                               |
| `TK_COMMENT_BLOCK`  | `###((?:(?!###)[\s\S])*?)(?:###\|$)` | `### comantário ####`  | Comentários em bloco                        |

Obs:

Em relação ao `TK_COMMENT_BLOCK`, depende do **lexer** e do **suporte a “greedy” ou “non-greedy”** em expressões regulares.

###((?:(?!###)[\s\S])*?)(?:###|$)

Em relação ao `TK_DOT`, para dicernir entre "." para função e para número (float, por exemplo), a prioridade das regras pode resolver isso.

Em relação a "EOF", [ainda está sendo estudado]

Em relação a "\n", "\t" e "\0", [ainda está sendo estudado]

Em relação a "e" (constante de Euler), "pi" (constante de Pi), "phi" (número de ouro) e "i" (unidade imaginária), [ainda está sendo estudado]

# Autômatos Finitos (AFD, AFN ou AFN-estendido a partir do Método de Thompson)

AFD: Autômatos finitos determinísticos

AFN: Autômato finito não determinístico

[ em breve ]

# Definição, declaração e explicação das regras para reconhecer os comandos e operadores definidos

[ em breve ]

---

*Observação: Este documento será atualizado conforme o progresso no desenvolvimento da linguagem, inclusão dos AFDs/AFNs e regras de produção.*
