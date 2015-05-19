DOCUMENTAÇÃO DO PROJETO
=======================

Execução do código fonte
------------------------

Para executar o compilador completo é necessário utilizar o comando:

```bash
 python3 executa.py.
```

Fases de Desenvolvimento
------------------------

* Fase 1 - Analisador Léxico (Finalizada);

* Fase 2 - Analisador Sintático (em desenvolvimento);

* Fase 3 - Analisador Semântico (em planejamento).

Requisitos detalhados de cada fase de desenvolvimento
-----------------------------------------------------

* Analisador Léxico
  * Implementação de um analisador léxico para a linguagem definida pela tabela a seguir (maiores detalhes sobre a linguagem foram baseados na linguagem de progração C):
  
| Palavra Token                        | Expressão regular correspondente     |
|--------------------------------------|--------------------------------------|
| Palavras reservadas                  | algoritmo, variaveis, constantes, registro, funcao, retorno, vazio, se, senao, enquanto, para, leia, escreva, inteiro, real, booleano, char, cadeia, verdadeiro, falso |
| Identificadores                      | ```Letra(Letra|Dígito|_)*```                          |
| Número                               | ```Dígito+(.Dígito+)?```                              |
| Letra                                | ```(a..z|A..Z)```                                     |
| Dígito                               | ```0..9```                                            |
| Símbolo                              | ```ASCII de 32 a 126```                               |
| Cadeia Constante                     | ```"(Letra|Dígito|Símbolo (exceto 34))"```            |
| Caractere Constante                  | ```'(Letra|Dígito|Símbolo (exceto 39))'```            |
| Operadores                           | ```. + - * / ++ -- == != > >= < <= && || =```         |
| Delimitadores                        | ```; , ( ) { } [ ]```                                 |
| Comentários de Linha                 | ```/* Isto é um comentário de bloco */```             |
| Comentários de Bloco                 | ```// Isto é um comentário de linha```                |

* Analisador Sintático
  * Construção de uma gramática livre de contexto fatorada à esquerda, na forma de Backus-Naur (BNF), de acordo com as especificações do anexo A a seguir:
  Anexo A - Características Gerais da Linguagem de Programação criada
  -------------------------------------------------------------------

  1. Linguagem estruturada;
  2. A declaração de constantes deverá vir em um bloco iniciado pela palavra reservada constantes. Constantes podem ser de qualquer tipo primitivo (inteiro, real, blooleano, char, cadeia). Cada constante deve ser declarada em uma linha dentro do bloco. Este bloco é obrigatório. Se não houver constantes, o bloco deverá estar vazio.
  
   Exemplo:
    ```cpp
     constantes
     {
      inteiro MAX = 10;
      inteiro MAX2 = 50;
      cadeia Texto = "mensagem";
     }
    ```
  3. Todas as constantes devem ser globais;
  4. A criação de um tipo registro dessa linguagem deve-se iniciar pela palavra reservada registro, seguida do nome do tipo do registro, seguida de um bloco contendo a declaração dos campos do registro (tipo e nome). Uma declaração em cada linha do bloco.
  5. Todos os tipos registros, se existirem, devem ser globais e declarados no início do programa antes da declaração das constantes e variáveis globais.
  6. Toda declaração de variáveis deverá vir em um bloco começando com a palavra reservada variáveis. Cada variável deve ser declarada em uma linha dentro do bloco, contendo o tipo e o nome da variável seguido de ponto e vírgula. Este bloco é obrigatório. Se não houver variáveis, o bloco deverá estar vazio.
  
   Exemplo:
    ```cpp
     variaveis
     {
      inteiro a;
      inteiro b;
      cadeia Mensagem;
     }
    ```
  7. As variáveis podem ser dos tipos primitivos ou dos tipos registros.
  8. A declaração de vetores e matrizes deve ser feita no bloco de declaração de variáveis. A linguagem permite somente a declaração e manipulação de vetores e matrizes dos tipos primitivos.
  9. É permitida a inicialização de variáveis na declaração, mas não de vetores e matrizes.
  10. As variáveis podem ser locais ou globais. Se forem globais devem vir devem vir declaradas após a declaração das constantes. Se forem locais, deve ser declaradas no início do bloco da função, sendo seu escopo, o corpo da função onde as variáveis forem declaradas.
  11. Para acessar os campos de uma variáveil do tipo registro deve-se utilizar o nome da variável seguido deo operador ponto, seguido do nome do campo.
  12. O corpo principal do programa é um bloco iniciado pela palavra reservada algoritmo. Quando um programa nessa linguagem é executado, é este bloco que é executado. Este bloco é a última parte de um programa nesta linguagem.
  13. 
  * Implementação de um analisador sintático para a linguagem definida pela gramática construída.

* Analisador Semântico
