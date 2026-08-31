# Apostila — Estrutura de Dados com Linguagem C

## Representação dos Dados na Memória, Arrays, Matrizes e Structs

**Disciplina:** Estrutura de Dados  
**Linguagem:** C  
**Módulo:** Fundamentos de representação e organização de dados

---

## Sumário

1. [Introdução à linguagem C](#1-introdução-à-linguagem-c)
2. [Primeiro programa em C](#2-primeiro-programa-em-c)
3. [O que são dados?](#3-o-que-são-dados)
4. [Estruturas de dados](#4-estruturas-de-dados)
5. [Representação dos dados na memória](#5-representação-dos-dados-na-memória)
6. [Variáveis e tipos de dados](#6-variáveis-e-tipos-de-dados)
7. [Endereços de memória](#7-endereços-de-memória)
8. [Arrays](#8-arrays)
9. [Matrizes](#9-matrizes)
10. [Strings em C](#10-strings-em-c)
11. [Estruturas (`struct`)](#11-estruturas-struct)
12. [Arrays de estruturas](#12-arrays-de-estruturas)
13. [Modelagem de dados](#13-modelagem-de-dados)
14. [Abstração](#14-abstração)
15. [Implementação prática](#15-implementação-prática)
16. [Atividades](#16-atividades)
17. [Erros comuns](#17-erros-comuns)
18. [Resumo](#18-resumo)
19. [Questões de revisão](#19-questões-de-revisão)
20. [Conclusão](#20-conclusão)

---

# 1. Introdução à linguagem C

A linguagem C é uma linguagem de programação de propósito geral, criada na década de 1970 e amplamente utilizada no desenvolvimento de sistemas, aplicações embarcadas, sistemas operacionais e softwares que exigem alto desempenho.

No contexto da disciplina de **Estrutura de Dados**, C é especialmente importante porque permite compreender de maneira mais próxima do hardware:

- como os dados são armazenados;
- como a memória é organizada;
- como variáveis ocupam espaço;
- como arrays são representados;
- como endereços de memória são utilizados;
- como estruturas de dados podem ser implementadas.

Essa proximidade com a memória torna C uma excelente linguagem para estudar os fundamentos de Estrutura de Dados.

---

# 2. Primeiro programa em C

Um programa simples:

```c
#include <stdio.h>

int main(void)
{
    printf("Ola, mundo!\n");

    return 0;
}
```

## Entendendo o programa

### `#include <stdio.h>`

Inclui a biblioteca padrão de entrada e saída. Ela fornece funções como:

```c
printf()
scanf()
```

### `int main(void)`

É a função principal do programa. A execução começa nela.

### `printf()`

Utilizada para exibir informações na tela.

### `return 0`

Indica que o programa terminou normalmente.

---

# 3. O que são dados?

Um dado é uma informação que pode ser armazenada e processada pelo computador.

Exemplos:

```text
25
3.14
"Maria"
'A'
```

Em programação, precisamos definir:

1. qual informação será armazenada;
2. qual tipo de dado ela representa;
3. onde será armazenada;
4. como será manipulada.

É nesse contexto que surgem as **estruturas de dados**.

---

# 4. Estruturas de dados

Uma estrutura de dados é uma forma de organizar informações na memória para permitir que elas sejam utilizadas de maneira eficiente.

Podemos pensar:

```text
DADOS
  ↓
ORGANIZAÇÃO
  ↓
ESTRUTURA DE DADOS
  ↓
OPERAÇÕES
```

Exemplos de estruturas de dados:

- arrays;
- matrizes;
- `structs`;
- listas encadeadas;
- pilhas;
- filas;
- árvores;
- grafos;
- tabelas hash.

Nesta apostila, começaremos pelas estruturas fundamentais.

---

# 5. Representação dos dados na memória

Quando um programa é executado, seus dados precisam ser armazenados na memória.

Considere:

```c
int idade = 20;
```

Podemos representar conceitualmente:

```text
        MEMÓRIA

Endereço        Conteúdo
---------       --------
1000            20
```

O endereço `1000` é apenas ilustrativo.

O computador utiliza endereços de memória para localizar os dados.

Assim, podemos pensar:

```text
Variável
   ↓
Endereço
   ↓
Memória
   ↓
Valor
```

---

# 6. Variáveis e tipos de dados

Uma variável é uma região de memória associada a um nome utilizada para armazenar um valor.

Exemplo:

```c
int idade = 20;
```

Nesse caso:

```text
idade
  ↓
20
```

Outro exemplo:

```c
float salario = 2500.50f;
```

E:

```c
char inicial = 'M';
```

## Principais tipos de dados

| Tipo | Exemplo | Utilização |
|---|---|---|
| `int` | `20` | Números inteiros |
| `float` | `7.5f` | Números reais |
| `double` | `3.141592` | Números reais com maior precisão |
| `char` | `'A'` | Um caractere |

Exemplo:

```c
int idade = 20;
float nota = 8.5f;
double pi = 3.1415926535;
char inicial = 'M';
```

## Tamanho dos tipos

O tamanho ocupado por um tipo pode variar conforme a implementação e a plataforma. Podemos descobrir o tamanho utilizando `sizeof`:

```c
#include <stdio.h>

int main(void)
{
    printf("int: %zu bytes\n", sizeof(int));
    printf("float: %zu bytes\n", sizeof(float));
    printf("double: %zu bytes\n", sizeof(double));
    printf("char: %zu byte\n", sizeof(char));

    return 0;
}
```

O operador `sizeof` informa o tamanho, em bytes, de um tipo ou objeto.

---

# 7. Endereços de memória

Em C, podemos obter o endereço de uma variável utilizando o operador `&`.

Exemplo:

```c
#include <stdio.h>

int main(void)
{
    int idade = 20;

    printf("Valor: %d\n", idade);
    printf("Endereco: %p\n", (void *)&idade);

    return 0;
}
```

Observe:

```c
idade
```

representa o valor.

Enquanto:

```c
&idade
```

representa o endereço da variável.

## Por que estudar memória?

A compreensão da memória será importante quando estudarmos:

- arrays;
- ponteiros;
- listas encadeadas;
- árvores;
- alocação dinâmica;
- estruturas complexas.

Por exemplo, uma lista encadeada depende da capacidade de armazenar referências para outros elementos.

> **Compreender memória ajuda a compreender estruturas de dados.**

---

# 8. Arrays

Um array permite armazenar vários elementos do mesmo tipo.

Imagine que precisamos armazenar cinco notas.

Uma solução inadequada seria:

```c
float nota1;
float nota2;
float nota3;
float nota4;
float nota5;
```

Uma solução mais adequada:

```c
float notas[5];
```

Agora temos uma única estrutura contendo cinco elementos.

## Índices do array

Em C, os índices começam em `0`.

Para:

```c
float notas[5];
```

temos:

```text
Índice:    0      1      2      3      4
         +------+------+------+------+------+
Valor:   |      |      |      |      |      |
         +------+------+------+------+------+
```

Os elementos são:

```c
notas[0]
notas[1]
notas[2]
notas[3]
notas[4]
```

Não existe um sexto elemento válido em `notas[5]`.

## Inicializando um array

Podemos declarar e inicializar:

```c
int numeros[5] = {10, 20, 30, 40, 50};
```

Podemos acessar:

```c
printf("%d\n", numeros[0]);
printf("%d\n", numeros[3]);
```

Resultado:

```text
10
40
```

## Percorrendo um array

Uma das operações mais importantes é percorrer todos os elementos:

```c
#include <stdio.h>

int main(void)
{
    int numeros[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; i++) {
        printf("%d\n", numeros[i]);
    }

    return 0;
}
```

O `for` percorre os índices:

```text
0 → 1 → 2 → 3 → 4
```

## Entrada de dados em um array

Podemos solicitar os valores ao usuário:

```c
#include <stdio.h>

int main(void)
{
    int numeros[5];

    for (int i = 0; i < 5; i++) {
        printf("Digite o %d valor: ", i + 1);
        scanf("%d", &numeros[i]);
    }

    printf("\nValores digitados:\n");

    for (int i = 0; i < 5; i++) {
        printf("%d\n", numeros[i]);
    }

    return 0;
}
```

Observe:

```c
scanf("%d", &numeros[i]);
```

O `&` é necessário porque `scanf` precisa receber o endereço onde deverá armazenar o valor.

## Operações com arrays

Uma operação comum é calcular a soma:

```c
int numeros[5] = {10, 20, 30, 40, 50};

int soma = 0;

for (int i = 0; i < 5; i++) {
    soma += numeros[i];
}

printf("Soma: %d\n", soma);
```

Podemos calcular a média:

```c
float media = soma / 5.0f;
```

## Arrays e memória

Um dos conceitos fundamentais é que os elementos de um array são armazenados de forma contígua.

Conceitualmente:

```text
Memória

+---------+---------+---------+---------+
| notas[0]| notas[1]| notas[2]| notas[3]|
+---------+---------+---------+---------+
```

Se cada elemento ocupa o mesmo tamanho, os endereços dos elementos seguem uma sequência.

Essa característica permite que o acesso por índice seja muito eficiente.

---

# 9. Matrizes

Uma matriz pode ser entendida como um array com duas dimensões.

Exemplo:

```c
int matriz[3][3];
```

Podemos visualizar:

```text
       Colunas

       0   1   2
     +---+---+---+
  0  |   |   |   |
     +---+---+---+
  1  |   |   |   |
     +---+---+---+
  2  |   |   |   |
     +---+---+---+

Linhas
```

## Inicializando uma matriz

```c
int matriz[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

Acesso:

```c
printf("%d\n", matriz[0][0]);
```

Resultado:

```text
1
```

Outro exemplo:

```c
printf("%d\n", matriz[2][1]);
```

Resultado:

```text
8
```

## Percorrendo uma matriz

Utilizamos dois loops:

```c
#include <stdio.h>

int main(void)
{
    int matriz[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matriz[i][j]);
        }

        printf("\n");
    }

    return 0;
}
```

O primeiro `for` controla as linhas.

O segundo controla as colunas.

## Aplicações de matrizes

Matrizes podem representar:

- tabuleiros;
- mapas;
- tabelas;
- imagens;
- notas;
- dados científicos;
- matrizes matemáticas.

Exemplo: notas de alunos.

```text
             Prova 1  Prova 2  Prova 3

Aluno 1         8        7        9
Aluno 2         6        8        7
Aluno 3        10        9        8
```

Em C:

```c
float notas[3][3];
```

---

# 10. Strings em C

Em C, uma string é representada por um array de caracteres terminado pelo caractere especial `'\0'`.

Exemplo:

```c
char nome[20] = "Maria";
```

Conceitualmente:

```text
M | a | r | i | a | \0
```

Podemos imprimir:

```c
printf("%s\n", nome);
```

## Lendo strings

Uma possibilidade:

```c
char nome[50];

printf("Digite seu nome: ");
scanf("%49s", nome);
```

Essa forma não lê espaços.

Para ler uma linha:

```c
scanf(" %49[^\n]", nome);
```

Outra alternativa é utilizar `fgets`:

```c
fgets(nome, sizeof(nome), stdin);
```

`fgets` é geralmente uma opção mais segura para leitura de linhas.

---

# 11. Estruturas (`struct`)

Considere um aluno.

Ele pode possuir:

```text
Nome       → texto
Idade      → inteiro
Nota       → real
Matrícula  → inteiro
```

Temos dados de diferentes tipos.

Um array tradicional não resolve diretamente esse problema porque seus elementos são de um mesmo tipo.

Precisamos de outra forma de organização.

É nesse contexto que utilizamos `struct`.

## Criando uma estrutura

Uma `struct` permite agrupar diferentes campos em uma única estrutura.

```c
struct Aluno {
    char nome[50];
    int idade;
    int matricula;
    float nota;
};
```

Agora podemos criar uma variável:

```c
struct Aluno aluno1;
```

## Acessando os campos

Utilizamos o operador `.`:

```c
aluno1.idade = 20;
aluno1.matricula = 12345;
aluno1.nota = 8.5f;
```

Para o nome:

```c
#include <string.h>

strcpy(aluno1.nome, "Maria");
```

## Exemplo completo

```c
#include <stdio.h>
#include <string.h>

struct Aluno {
    char nome[50];
    int idade;
    int matricula;
    float nota;
};

int main(void)
{
    struct Aluno aluno;

    strcpy(aluno.nome, "Maria");
    aluno.idade = 20;
    aluno.matricula = 12345;
    aluno.nota = 8.5f;

    printf("Nome: %s\n", aluno.nome);
    printf("Idade: %d\n", aluno.idade);
    printf("Matricula: %d\n", aluno.matricula);
    printf("Nota: %.2f\n", aluno.nota);

    return 0;
}
```

## Inicializando uma `struct`

Também podemos inicializar diretamente:

```c
struct Aluno aluno = {
    "Maria",
    20,
    12345,
    8.5f
};
```

Ou utilizar inicialização nomeada:

```c
struct Aluno aluno = {
    .nome = "Maria",
    .idade = 20,
    .matricula = 12345,
    .nota = 8.5f
};
```

A segunda forma torna o código mais explícito.

---

# 12. Arrays de estruturas

Podemos combinar os conceitos estudados.

Por exemplo:

```c
struct Aluno alunos[3];
```

Temos um array contendo três estruturas `Aluno`.

Visualmente:

```text
alunos

+----------------+----------------+----------------+
|    Aluno 0     |    Aluno 1     |    Aluno 2     |
+----------------+----------------+----------------+
| nome           | nome           | nome           |
| idade          | idade          | idade          |
| matricula      | matricula      | matricula      |
| nota            | nota            | nota            |
+----------------+----------------+----------------+
```

## Acessando arrays de estruturas

Exemplo:

```c
alunos[0].idade = 20;
alunos[1].idade = 21;
alunos[2].idade = 19;
```

Para acessar a nota do segundo aluno:

```c
alunos[1].nota
```

Para acessar o nome do terceiro:

```c
alunos[2].nome
```

Essa combinação é extremamente importante em Estrutura de Dados.

## Cadastro de alunos

Exemplo completo:

```c
#include <stdio.h>

struct Aluno {
    char nome[50];
    int idade;
    float nota;
};

int main(void)
{
    struct Aluno alunos[3];

    for (int i = 0; i < 3; i++) {
        printf("\nAluno %d\n", i + 1);

        printf("Nome: ");
        scanf(" %49[^\n]", alunos[i].nome);

        printf("Idade: ");
        scanf("%d", &alunos[i].idade);

        printf("Nota: ");
        scanf("%f", &alunos[i].nota);
    }

    printf("\n--- ALUNOS ---\n");

    for (int i = 0; i < 3; i++) {
        printf("\nNome: %s\n", alunos[i].nome);
        printf("Idade: %d\n", alunos[i].idade);
        printf("Nota: %.2f\n", alunos[i].nota);
    }

    return 0;
}
```

---

# 13. Modelagem de dados

Antes de implementar uma estrutura, precisamos compreender o problema.

Imagine um sistema acadêmico.

Podemos identificar a entidade:

```text
ALUNO
```

E seus atributos:

```text
nome
idade
matrícula
curso
notas
```

Podemos representar:

```text
              ALUNO
                |
       +--------+--------+
       |        |        |
      nome    idade   matrícula
                |
              notas
```

Em C:

```c
struct Aluno {
    char nome[50];
    int idade;
    int matricula;
    float notas[3];
};
```

## O que é modelagem?

**Modelagem de dados** é o processo de identificar e organizar as informações relevantes de um problema.

Por exemplo:

### Problema

Criar um sistema para uma biblioteca.

Podemos identificar:

```text
Livro
Aluno
Empréstimo
```

Um livro pode possuir:

```text
título
autor
ISBN
ano
```

Em C:

```c
struct Livro {
    char titulo[100];
    char autor[80];
    char isbn[20];
    int ano;
};
```

---

# 14. Abstração

Abstração é concentrar-se nos aspectos importantes de um problema e ignorar detalhes que não são relevantes naquele contexto.

Imagine que precisamos representar um livro em uma biblioteca.

Podemos precisar de:

```text
título
autor
ISBN
ano
```

Mas talvez não precisemos armazenar:

```text
cor da capa
peso emocional da história
filme favorito do autor
```

A abstração ajuda a responder:

> **Quais características são relevantes para o problema que estamos tentando resolver?**

## Modelagem → Estrutura de Dados

O processo pode ser representado assim:

```text
PROBLEMA REAL
      ↓
IDENTIFICAÇÃO DAS ENTIDADES
      ↓
IDENTIFICAÇÃO DOS ATRIBUTOS
      ↓
MODELAGEM
      ↓
ESCOLHA DA ESTRUTURA DE DADOS
      ↓
IMPLEMENTAÇÃO EM C
```

Exemplo:

```text
Problema:
Cadastro de produtos

        ↓

Entidade:
Produto

        ↓

Atributos:
nome
preço
quantidade

        ↓

Implementação:

struct Produto {
    char nome[50];
    float preco;
    int quantidade;
};
```

---

# 15. Implementação prática

## Sistema de produtos

Vamos desenvolver uma aplicação simples.

### Requisitos

O sistema deverá:

1. cadastrar cinco produtos;
2. armazenar nome, preço e quantidade;
3. exibir os produtos;
4. calcular o valor total do estoque.

## Código

```c
#include <stdio.h>

struct Produto {
    char nome[50];
    float preco;
    int quantidade;
};

int main(void)
{
    struct Produto produtos[5];

    float valorTotal = 0.0f;

    for (int i = 0; i < 5; i++) {
        printf("\nProduto %d\n", i + 1);

        printf("Nome: ");
        scanf(" %49[^\n]", produtos[i].nome);

        printf("Preco: ");
        scanf("%f", &produtos[i].preco);

        printf("Quantidade: ");
        scanf("%d", &produtos[i].quantidade);
    }

    printf("\n===== ESTOQUE =====\n");

    for (int i = 0; i < 5; i++) {
        float valorProduto =
            produtos[i].preco * produtos[i].quantidade;

        printf("\nProduto: %s\n", produtos[i].nome);
        printf("Preco: R$ %.2f\n", produtos[i].preco);
        printf("Quantidade: %d\n", produtos[i].quantidade);
        printf("Valor em estoque: R$ %.2f\n", valorProduto);

        valorTotal += valorProduto;
    }

    printf("\nValor total do estoque: R$ %.2f\n", valorTotal);

    return 0;
}
```

## Analisando o programa

Observe:

```c
struct Produto produtos[5];
```

Ela combina dois conceitos:

```text
struct
  +
array
```

Ou seja:

> Temos um array de estruturas `Produto`.

Cada posição possui:

```text
produtos[0]
produtos[1]
produtos[2]
produtos[3]
produtos[4]
```

E cada elemento possui:

```text
nome
preco
quantidade
```

---

# 16. Atividades

## Atividade 1 — Arrays

Crie um programa que:

1. declare um array com 10 números inteiros;
2. solicite os valores ao usuário;
3. exiba todos os números;
4. calcule a soma;
5. calcule a média.

### Desafio

Além disso, encontre:

- o maior valor;
- o menor valor.

---

## Atividade 2 — Matrizes

Crie uma matriz `3 × 3`.

Solicite os valores ao usuário e:

1. exiba a matriz;
2. calcule a soma de todos os elementos;
3. calcule a soma da diagonal principal.

Exemplo:

```text
1 2 3
4 5 6
7 8 9
```

A diagonal principal é:

```text
1
   5
      9
```

Soma:

```text
1 + 5 + 9 = 15
```

---

## Atividade 3 — Struct

Crie uma estrutura:

```c
struct Livro
```

com os seguintes campos:

```text
titulo
autor
ano
preco
```

Depois:

1. crie um livro;
2. leia os dados;
3. exiba os dados.

---

## Atividade 4 — Array de structs

Crie:

```c
struct Aluno
```

com:

```text
nome
matrícula
nota1
nota2
```

Cadastre cinco alunos.

Depois:

1. calcule a média de cada aluno;
2. exiba os alunos aprovados;
3. identifique o aluno com maior média.

Considere aprovação:

```text
média >= 7.0
```

---

## Desafio integrador — Sistema de estoque

Desenvolva um pequeno sistema de estoque.

Crie:

```c
struct Produto
```

com:

```text
codigo
nome
preco
quantidade
```

O programa deverá permitir:

- cadastrar produtos;
- listar produtos;
- calcular o valor total do estoque;
- localizar um produto pelo código;
- identificar o produto com maior preço.

### Desafio adicional

Implemente um menu:

```text
===== SISTEMA DE ESTOQUE =====

1 - Cadastrar produto
2 - Listar produtos
3 - Buscar produto
4 - Valor total do estoque
5 - Produto mais caro
0 - Sair

Escolha:
```

Esse exercício prepara o estudante para conteúdos posteriores, como funções, modularização e estruturas de dados mais complexas.

---

# 17. Erros comuns

## Erro 1 — Índice inválido

```c
int numeros[5];

numeros[5] = 10;
```

Os índices válidos são:

```text
0
1
2
3
4
```

Acesso fora dos limites de um array é um comportamento indefinido e pode causar resultados incorretos ou falhas.

---

## Erro 2 — Esquecer o `&` no `scanf`

Incorreto:

```c
scanf("%d", idade);
```

Correto:

```c
scanf("%d", &idade);
```

Para `scanf`, normalmente passamos o endereço da variável que receberá o valor.

---

## Erro 3 — Confundir `.` com `&`

Para acessar um campo:

```c
aluno.idade
```

Para obter o endereço:

```c
&aluno
```

São operações diferentes.

---

## Erro 4 — Confundir índice com quantidade

Em:

```c
int numeros[10];
```

existem **10 elementos**, mas o maior índice é:

```text
9
```

---

## Erro 5 — Não reservar espaço suficiente para uma string

Considere:

```c
char nome[5] = "Maria";
```

Isso é inadequado porque `"Maria"` precisa de seis posições: cinco caracteres mais o `'\0'`.

O correto seria:

```c
char nome[6] = "Maria";
```

Ou, preferencialmente, deixar o compilador calcular:

```c
char nome[] = "Maria";
```

---

# 18. Resumo

Nesta unidade aprendemos que:

### Variáveis

Representam dados armazenados na memória.

```c
int idade = 20;
```

### Arrays

Armazenam vários elementos do mesmo tipo.

```c
int numeros[10];
```

### Matrizes

Representam dados em duas ou mais dimensões.

```c
int matriz[3][3];
```

### Strings

São representadas em C por arrays de caracteres terminados em `'\0'`.

```c
char nome[50];
```

### Structs

Agrupam diferentes tipos de dados relacionados.

```c
struct Aluno {
    char nome[50];
    int idade;
    float nota;
};
```

### Arrays de structs

Permitem representar coleções de entidades.

```c
struct Aluno alunos[30];
```

### Modelagem

Define quais entidades e informações são relevantes para o problema.

### Abstração

Permite concentrar a representação nos aspectos importantes.

---

# 19. Questões de revisão

### Questão 1

O que é uma estrutura de dados?

### Questão 2

Qual é a diferença entre uma variável e um array?

### Questão 3

Qual é o primeiro índice de um array em C?

### Questão 4

Quantos elementos existem em:

```c
int valores[20];
```

E qual é o maior índice válido?

### Questão 5

O que representa:

```c
matriz[2][3]
```

### Questão 6

Para que serve uma `struct`?

### Questão 7

Qual é a diferença entre:

```c
aluno.idade
```

e:

```c
&aluno
```

### Questão 8

Por que podemos utilizar um array de `struct`?

### Questão 9

O que significa modelar um problema?

### Questão 10

Explique o conceito de abstração utilizando um exemplo de sistema computacional.

---

# 20. Gabarito resumido

**1.** Forma de organizar dados para permitir seu armazenamento e manipulação.

**2.** Uma variável normalmente representa um único dado, enquanto um array permite armazenar vários elementos do mesmo tipo.

**3.** `0`.

**4.** 20 elementos; índices de `0` a `19`.

**5.** O elemento localizado na linha de índice `2` e coluna de índice `3`. Portanto, em uma matriz válida com pelo menos quatro colunas, corresponde à terceira linha e quarta coluna.

**6.** Agrupar diferentes campos relacionados em uma única estrutura.

**7.** `aluno.idade` acessa o campo `idade`; `&aluno` obtém o endereço da variável `aluno`.

**8.** Para armazenar vários objetos/entidades que possuem a mesma estrutura.

**9.** Identificar e organizar as informações relevantes de um problema.

**10.** Representar somente as características relevantes para determinado problema, ignorando detalhes desnecessários.

---

# Conclusão

O estudo de Estrutura de Dados começa pela compreensão de como os dados são representados e organizados.

Em C, podemos observar essa organização de forma bastante próxima da memória do computador.

A progressão fundamental desta unidade é:

```text
VARIÁVEL
   ↓
ARRAY
   ↓
MATRIZ
   ↓
STRUCT
   ↓
ARRAY DE STRUCTS
   ↓
MODELAGEM
   ↓
ABSTRAÇÃO
```

Esses conceitos constituem a base para o estudo de estruturas de dados mais avançadas.

A partir deles, será possível compreender melhor:

```text
Listas Encadeadas
       ↓
Pilhas
       ↓
Filas
       ↓
Árvores
       ↓
Grafos
       ↓
Tabelas Hash
```

O princípio fundamental permanece:

> **Uma estrutura de dados deve ser escolhida de acordo com o problema, os dados que precisam ser representados e as operações que serão realizadas sobre eles.**
