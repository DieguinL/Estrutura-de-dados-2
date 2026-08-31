# Apostila — Estrutura de Dados com Python

## Representação dos Dados, Listas, Matrizes, Dicionários e Dataclasses

**Disciplina:** Estrutura de Dados  
**Linguagem:** Python  
**Módulo:** Fundamentos de representação e organização de dados

---

## Sumário

1. [Introdução à linguagem Python](#1-introdução-à-linguagem-python)
2. [Primeiro programa em Python](#2-primeiro-programa-em-python)
3. [O que são dados?](#3-o-que-são-dados)
4. [Estruturas de dados](#4-estruturas-de-dados)
5. [Representação dos dados em memória](#5-representação-dos-dados-em-memória)
6. [Variáveis e tipos de dados](#6-variáveis-e-tipos-de-dados)
7. [Identidade e referências](#7-identidade-e-referências)
8. [Listas](#8-listas)
9. [Matrizes](#9-matrizes)
10. [Strings](#10-strings)
11. [Tuplas e conjuntos](#11-tuplas-e-conjuntos)
12. [Dicionários](#12-dicionários)
13. [Dataclasses](#13-dataclasses)
14. [Listas de objetos](#14-listas-de-objetos)
15. [Modelagem de dados](#15-modelagem-de-dados)
16. [Abstração](#16-abstração)
17. [Implementação prática](#17-implementação-prática)
18. [Atividades](#18-atividades)
19. [Erros comuns](#19-erros-comuns)
20. [Resumo](#20-resumo)
21. [Questões de revisão](#21-questões-de-revisão)
22. [Gabarito](#22-gabarito)
23. [Conclusão](#23-conclusão)

---

# 1. Introdução à linguagem Python

Python é uma linguagem de programação de alto nível, interpretada, de propósito geral e amplamente utilizada em áreas como desenvolvimento de software, ciência de dados, automação, inteligência artificial e desenvolvimento web.

Na disciplina de **Estrutura de Dados**, Python permite trabalhar com estruturas de forma bastante expressiva, sem exigir que o estudante gerencie manualmente a memória.

Entre as estruturas mais importantes da linguagem estão:

- listas;
- tuplas;
- conjuntos;
- dicionários;
- strings;
- classes e objetos;
- estruturas multidimensionais construídas a partir de listas.

Python também possui recursos que facilitam a modelagem de entidades, como classes e `dataclasses`.

---

# 2. Primeiro programa em Python

Um programa simples:

```python
print("Ola, mundo!")
```

A função `print()` exibe informações na tela.

Podemos também armazenar uma informação:

```python
nome = "Maria"

print(nome)
```

O programa produz:

```text
Maria
```

Python possui uma sintaxe relativamente simples, permitindo que o estudante concentre sua atenção nos conceitos de organização dos dados.

---

# 3. O que são dados?

Um dado é uma informação que pode ser armazenada e processada pelo computador.

Exemplos:

```python
25
3.14
"Maria"
'A'
True
```

Em programação, precisamos definir:

1. qual informação será armazenada;
2. qual tipo de dado ela representa;
3. como os dados serão organizados;
4. quais operações serão realizadas sobre eles.

É nesse contexto que estudamos **estruturas de dados**.

---

# 4. Estruturas de dados

Uma estrutura de dados é uma forma de organizar informações para facilitar seu armazenamento, acesso e processamento.

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

Exemplos de estruturas disponíveis ou construídas em Python:

- listas;
- matrizes;
- tuplas;
- conjuntos;
- dicionários;
- classes;
- listas de objetos;
- pilhas;
- filas;
- árvores;
- grafos.

Nesta apostila, começaremos pelas estruturas fundamentais.

---

# 5. Representação dos dados em memória

Quando um programa Python é executado, os dados utilizados pelo programa precisam ser representados na memória.

Considere:

```python
idade = 20
```

Uma representação conceitual seria:

```text
idade
  ↓
objeto inteiro
  ↓
20
```

Em Python, é importante compreender que as variáveis funcionam como **referências para objetos**.

Por exemplo:

```python
idade = 20
```

Podemos pensar que o nome `idade` está associado a um objeto que representa o valor `20`.

Essa característica é importante para compreender posteriormente:

- listas;
- objetos;
- cópia de dados;
- referências;
- mutabilidade;
- classes.

> **Observação:** detalhes internos da implementação do Python dependem da implementação utilizada, como CPython. Nesta etapa, o objetivo é compreender o conceito de referência, e não os detalhes internos do interpretador.

---

# 6. Variáveis e tipos de dados

Em Python, não precisamos declarar explicitamente o tipo de uma variável antes de utilizá-la.

Exemplo:

```python
idade = 20
nota = 8.5
nome = "Maria"
aprovado = True
```

Os principais tipos básicos incluem:

| Tipo | Exemplo | Utilização |
|---|---|---|
| `int` | `20` | Números inteiros |
| `float` | `8.5` | Números reais |
| `str` | `"Maria"` | Textos |
| `bool` | `True` | Valores lógicos |
| `NoneType` | `None` | Ausência de valor |

Podemos verificar o tipo de um objeto usando `type()`:

```python
idade = 20

print(type(idade))
```

Resultado aproximado:

```text
<class 'int'>
```

Outro exemplo:

```python
nome = "Maria"

print(type(nome))
```

---

# 7. Identidade e referências

Python fornece a função `id()` para obter um identificador associado ao objeto durante sua existência.

Exemplo:

```python
idade = 20

print(idade)
print(id(idade))
```

O valor retornado por `id()` não deve ser tratado como um endereço de memória que o programador precisa manipular diretamente.

Podemos pensar conceitualmente:

```text
idade ───────► objeto 20
```

## Duas variáveis e um objeto

Considere:

```python
a = [10, 20, 30]
b = a
```

Agora:

```text
a ─────┐
       ├────► [10, 20, 30]
b ─────┘
```

As duas variáveis referenciam a mesma lista.

Se fizermos:

```python
b.append(40)
```

teremos:

```python
print(a)
```

Resultado:

```text
[10, 20, 30, 40]
```

Isso ocorre porque `a` e `b` estão referenciando o mesmo objeto lista.

Esse conceito será importante quando estudarmos estruturas mutáveis.

---

# 8. Listas

A lista é uma das estruturas de dados mais importantes de Python.

Ela permite armazenar uma sequência de elementos.

Exemplo:

```python
notas = [8.5, 7.0, 9.0, 6.5, 8.0]
```

Podemos visualizar:

```text
Índice:    0     1     2     3     4
         +-----+-----+-----+-----+-----+
Valor:   | 8.5 | 7.0 | 9.0 | 6.5 | 8.0 |
         +-----+-----+-----+-----+-----+
```

Os índices começam em `0`.

## Acessando elementos

```python
print(notas[0])
print(notas[2])
print(notas[4])
```

Resultado:

```text
8.5
9.0
8.0
```

Também podemos utilizar índices negativos:

```python
print(notas[-1])
```

Resultado:

```text
8.0
```

`notas[-1]` representa o último elemento.

---

## Modificando elementos

Listas são mutáveis.

Podemos alterar um elemento:

```python
notas[0] = 9.0
```

Agora:

```python
print(notas)
```

Resultado:

```text
[9.0, 7.0, 9.0, 6.5, 8.0]
```

---

## Adicionando elementos

Utilizamos `append()`:

```python
notas.append(10.0)
```

Também podemos inserir em uma posição:

```python
notas.insert(1, 8.5)
```

---

## Removendo elementos

Podemos remover pelo valor:

```python
notas.remove(7.0)
```

Ou pelo índice:

```python
del notas[0]
```

---

## Tamanho da lista

Utilizamos `len()`:

```python
print(len(notas))
```

---

## Percorrendo uma lista

A forma mais simples:

```python
for nota in notas:
    print(nota)
```

Quando precisamos do índice:

```python
for i in range(len(notas)):
    print(i, notas[i])
```

Também podemos utilizar `enumerate()`:

```python
for i, nota in enumerate(notas):
    print(i, nota)
```

---

## Operações numéricas

Para uma lista de números:

```python
notas = [8.5, 7.0, 9.0, 6.5, 8.0]

soma = sum(notas)
media = soma / len(notas)

print(f"Soma: {soma}")
print(f"Média: {media:.2f}")
```

Também podemos encontrar:

```python
print(max(notas))
print(min(notas))
```

---

## Ordenação

Podemos ordenar uma lista:

```python
notas.sort()
```

Ou criar uma nova lista ordenada:

```python
ordenadas = sorted(notas)
```

---

# 9. Matrizes

Python não possui um tipo básico chamado "matriz" semelhante a algumas linguagens matemáticas.

Entretanto, podemos representar uma matriz utilizando uma **lista de listas**.

Exemplo:

```python
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Podemos visualizar:

```text
       Colunas

       0   1   2
     +---+---+---+
  0  | 1 | 2 | 3 |
     +---+---+---+
  1  | 4 | 5 | 6 |
     +---+---+---+
  2  | 7 | 8 | 9 |
     +---+---+---+

Linhas
```

## Acessando elementos

```python
print(matriz[0][0])
```

Resultado:

```text
1
```

Outro exemplo:

```python
print(matriz[2][1])
```

Resultado:

```text
8
```

O primeiro índice representa a linha e o segundo representa a coluna.

---

## Percorrendo uma matriz

Utilizamos dois `for`:

```python
for linha in matriz:
    for valor in linha:
        print(valor, end=" ")
    print()
```

Resultado:

```text
1 2 3
4 5 6
7 8 9
```

Outra forma:

```python
for i in range(len(matriz)):
    for j in range(len(matriz[i])):
        print(matriz[i][j], end=" ")
    print()
```

---

## Soma dos elementos

Podemos calcular a soma:

```python
soma = 0

for linha in matriz:
    for valor in linha:
        soma += valor

print(soma)
```

Ou, utilizando uma expressão:

```python
soma = sum(sum(linha) for linha in matriz)
```

---

## Diagonal principal

Considere:

```python
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

A diagonal principal é:

```text
1
   5
      9
```

Podemos calcular:

```python
soma = 0

for i in range(len(matriz)):
    soma += matriz[i][i]

print(soma)
```

Resultado:

```text
15
```

---

## Aplicações de matrizes

Matrizes podem representar:

- tabuleiros;
- mapas;
- tabelas;
- imagens;
- notas;
- dados científicos;
- matrizes matemáticas.

Exemplo:

```python
notas = [
    [8, 7, 9],
    [6, 8, 7],
    [10, 9, 8]
]
```

Podemos interpretar:

```text
             Prova 1  Prova 2  Prova 3

Aluno 1         8        7        9
Aluno 2         6        8        7
Aluno 3        10        9        8
```

---

# 10. Strings

Em Python, strings são objetos do tipo `str`.

Exemplo:

```python
nome = "Maria"
```

Diferentemente de C, não precisamos representar manualmente o caractere terminador `'\0'`.

Podemos acessar caracteres por índice:

```python
print(nome[0])
print(nome[2])
```

Resultado:

```text
M
r
```

Strings são sequências e possuem várias operações úteis:

```python
nome = "Maria"

print(len(nome))
print(nome.upper())
print(nome.lower())
```

Podemos verificar se determinado texto está contido na string:

```python
print("Mar" in nome)
```

---

## Entrada de texto

Utilizamos `input()`:

```python
nome = input("Digite seu nome: ")

print(f"Olá, {nome}!")
```

Para números, precisamos converter o texto recebido:

```python
idade = int(input("Digite sua idade: "))
nota = float(input("Digite sua nota: "))
```

---

# 11. Tuplas e conjuntos

Além das listas, Python possui outras estruturas importantes.

## Tuplas

Tuplas são sequências que não podem ser modificadas depois de criadas.

Exemplo:

```python
coordenada = (10, 20)
```

Podemos acessar:

```python
print(coordenada[0])
print(coordenada[1])
```

Uma tupla pode ser útil quando queremos representar um conjunto de valores que não deve ser alterado.

Exemplo:

```python
data_nascimento = (15, 8, 2000)
```

---

## Conjuntos

Um conjunto (`set`) armazena elementos sem duplicação.

Exemplo:

```python
numeros = {1, 2, 3, 3, 4}

print(numeros)
```

O valor `3` aparece apenas uma vez.

Podemos utilizar conjuntos para operações como união e interseção.

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)
print(a & b)
```

---

# 12. Dicionários

Dicionários são estruturas que associam **chaves** a **valores**.

Exemplo:

```python
aluno = {
    "nome": "Maria",
    "idade": 20,
    "matricula": 12345,
    "nota": 8.5
}
```

Podemos visualizar:

```text
aluno
  |
  +-- "nome"      → "Maria"
  +-- "idade"     → 20
  +-- "matricula" → 12345
  +-- "nota"      → 8.5
```

## Acessando valores

```python
print(aluno["nome"])
print(aluno["nota"])
```

---

## Alterando valores

```python
aluno["nota"] = 9.0
```

---

## Adicionando informações

```python
aluno["curso"] = "Computação"
```

---

## Percorrendo um dicionário

```python
for chave, valor in aluno.items():
    print(chave, ":", valor)
```

---

## Dicionário com listas

Podemos combinar estruturas:

```python
aluno = {
    "nome": "Maria",
    "idade": 20,
    "notas": [8.5, 9.0, 7.5]
}
```

Acessando:

```python
print(aluno["notas"])
print(aluno["notas"][0])
```

Essa combinação permite representar entidades de forma bastante flexível.

---

# 13. Dataclasses

Quando queremos representar entidades de maneira mais estruturada, podemos utilizar classes.

Python fornece o módulo `dataclasses`, que facilita a criação de classes voltadas para armazenamento de dados.

Exemplo:

```python
from dataclasses import dataclass

@dataclass
class Aluno:
    nome: str
    idade: int
    matricula: int
    nota: float
```

Agora podemos criar um aluno:

```python
aluno = Aluno(
    "Maria",
    20,
    12345,
    8.5
)
```

Acessando os atributos:

```python
print(aluno.nome)
print(aluno.idade)
print(aluno.nota)
```

---

## Por que utilizar `dataclass`?

Uma `dataclass` ajuda a representar uma entidade com:

- atributos;
- tipos;
- organização;
- comportamento associado, quando necessário.

Ela é especialmente útil quando temos vários objetos com a mesma estrutura.

---

## Método dentro de uma `dataclass`

Podemos criar comportamentos.

Exemplo:

```python
from dataclasses import dataclass

@dataclass
class Aluno:
    nome: str
    notas: list[float]

    def media(self) -> float:
        return sum(self.notas) / len(self.notas)
```

Criando um objeto:

```python
aluno = Aluno(
    "Maria",
    [8.5, 9.0, 7.5]
)

print(aluno.media())
```

---

# 14. Listas de objetos

Podemos armazenar vários objetos em uma lista.

Exemplo:

```python
from dataclasses import dataclass

@dataclass
class Aluno:
    nome: str
    idade: int
    nota: float

alunos = [
    Aluno("Maria", 20, 8.5),
    Aluno("João", 21, 7.0),
    Aluno("Ana", 19, 9.2)
]
```

Agora temos:

```text
alunos
   |
   +-- Aluno 0
   |     +-- nome
   |     +-- idade
   |     +-- nota
   |
   +-- Aluno 1
   |     +-- nome
   |     +-- idade
   |     +-- nota
   |
   +-- Aluno 2
         +-- nome
         +-- idade
         +-- nota
```

Podemos percorrer:

```python
for aluno in alunos:
    print(aluno.nome)
    print(aluno.nota)
```

Podemos acessar um objeto específico:

```python
print(alunos[0].nome)
print(alunos[1].nota)
```

Essa combinação é muito importante em Estrutura de Dados.

---

# 15. Modelagem de dados

Antes de escolher uma estrutura de dados, precisamos compreender o problema.

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

Uma possível representação:

```python
from dataclasses import dataclass

@dataclass
class Aluno:
    nome: str
    idade: int
    matricula: int
    curso: str
    notas: list[float]
```

## O que é modelagem?

**Modelagem de dados** é o processo de identificar e organizar as informações relevantes de um problema.

Por exemplo, em um sistema de biblioteca podemos identificar:

```text
Livro
Aluno
Emprestimo
```

Um livro pode possuir:

```text
titulo
autor
ISBN
ano
```

Em Python:

```python
from dataclasses import dataclass

@dataclass
class Livro:
    titulo: str
    autor: str
    isbn: str
    ano: int
```

---

# 16. Abstração

Abstração é concentrar-se nos aspectos importantes de um problema e ignorar detalhes que não são relevantes naquele contexto.

Imagine que precisamos representar um livro em uma biblioteca.

Podemos precisar de:

```text
título
autor
ISBN
ano
```

Mas talvez não seja necessário armazenar:

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
IMPLEMENTAÇÃO EM PYTHON
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
@dataclass
class Produto:
    nome: str
    preco: float
    quantidade: int
```

---

# 17. Implementação prática

## Sistema de produtos

Vamos desenvolver uma aplicação simples.

### Requisitos

O sistema deverá:

1. cadastrar cinco produtos;
2. armazenar nome, preço e quantidade;
3. exibir os produtos;
4. calcular o valor total do estoque;
5. identificar o produto mais caro.

## Código

```python
from dataclasses import dataclass


@dataclass
class Produto:
    nome: str
    preco: float
    quantidade: int

    def valor_estoque(self) -> float:
        return self.preco * self.quantidade


produtos = []

for i in range(5):
    print(f"\nProduto {i + 1}")

    nome = input("Nome: ")
    preco = float(input("Preço: "))
    quantidade = int(input("Quantidade: "))

    produto = Produto(
        nome=nome,
        preco=preco,
        quantidade=quantidade
    )

    produtos.append(produto)


print("\n===== ESTOQUE =====")

valor_total = 0.0

for produto in produtos:
    valor = produto.valor_estoque()

    print(f"\nProduto: {produto.nome}")
    print(f"Preço: R$ {produto.preco:.2f}")
    print(f"Quantidade: {produto.quantidade}")
    print(f"Valor em estoque: R$ {valor:.2f}")

    valor_total += valor


print(f"\nValor total do estoque: R$ {valor_total:.2f}")

produto_mais_caro = max(
    produtos,
    key=lambda produto: produto.preco
)

print("\nProduto mais caro:")
print(produto_mais_caro.nome)
print(f"Preço: R$ {produto_mais_caro.preco:.2f}")
```

---

## Analisando o programa

Observe:

```python
produtos = []
```

Criamos uma lista vazia.

Depois, cada objeto `Produto` é inserido nela:

```python
produtos.append(produto)
```

Assim, temos:

```text
produtos
   |
   +-- Produto 0
   +-- Produto 1
   +-- Produto 2
   +-- Produto 3
   +-- Produto 4
```

Cada objeto possui:

```text
nome
preco
quantidade
```

A combinação:

```python
list[Produto]
```

é um exemplo de estrutura composta.

---

# 18. Atividades

## Atividade 1 — Listas

Crie um programa que:

1. crie uma lista com 10 números inteiros;
2. solicite os valores ao usuário;
3. exiba todos os números;
4. calcule a soma;
5. calcule a média.

### Desafio

Além disso, encontre:

- o maior valor;
- o menor valor;
- a quantidade de números pares.

---

## Atividade 2 — Matrizes

Crie uma matriz `3 × 3`.

Solicite os valores ao usuário e:

1. exiba a matriz;
2. calcule a soma de todos os elementos;
3. calcule a soma da diagonal principal;
4. encontre o maior elemento.

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

## Atividade 3 — Dicionário

Crie um dicionário para representar um livro com:

```text
titulo
autor
ano
preco
```

Depois:

1. leia os dados;
2. armazene-os no dicionário;
3. exiba os dados;
4. altere o preço;
5. adicione uma informação chamada `categoria`.

---

## Atividade 4 — Dataclass

Crie uma `dataclass` chamada `Aluno` com:

```text
nome
matricula
nota1
nota2
```

Crie um método chamado `media()` que calcule a média das duas notas.

Exemplo:

```python
aluno = Aluno(
    "Maria",
    12345,
    8.0,
    9.0
)

print(aluno.media())
```

---

## Atividade 5 — Lista de objetos

Utilizando a `dataclass` `Aluno`, cadastre cinco alunos.

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

Crie uma `dataclass`:

```python
@dataclass
class Produto:
    codigo: int
    nome: str
    preco: float
    quantidade: int
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

# 19. Erros comuns

## Erro 1 — Índice inválido

Considere:

```python
numeros = [10, 20, 30]
```

Os índices válidos são:

```text
0
1
2
```

O acesso:

```python
numeros[3]
```

causa:

```text
IndexError
```

---

## Erro 2 — Confundir índice com quantidade

Em:

```python
numeros = [10, 20, 30, 40, 50]
```

existem cinco elementos.

Os índices são:

```text
0
1
2
3
4
```

O último índice é `len(numeros) - 1`.

---

## Erro 3 — Confundir atribuição e comparação

Atribuição:

```python
idade = 20
```

Comparação:

```python
idade == 20
```

O operador `=` atribui um valor.

O operador `==` compara valores.

---

## Erro 4 — Alteração inesperada por referência

Considere:

```python
a = [1, 2, 3]
b = a

b.append(4)

print(a)
```

Resultado:

```text
[1, 2, 3, 4]
```

Isso acontece porque `a` e `b` referenciam a mesma lista.

Para criar uma cópia superficial da lista:

```python
b = a.copy()
```

---

## Erro 5 — Compartilhamento acidental em matrizes

Uma forma problemática de criar uma matriz é:

```python
matriz = [[0] * 3] * 3
```

As linhas internas são referências para a mesma lista.

Uma forma adequada:

```python
matriz = [[0] * 3 for _ in range(3)]
```

Agora cada linha é uma lista independente.

---

# 20. Resumo

Nesta unidade aprendemos que:

### Variáveis

Em Python, os nomes das variáveis referenciam objetos.

```python
idade = 20
```

### Listas

Armazenam sequências mutáveis de elementos.

```python
numeros = [10, 20, 30]
```

### Matrizes

Podem ser representadas por listas de listas.

```python
matriz = [
    [1, 2],
    [3, 4]
]
```

### Strings

São objetos do tipo `str` utilizados para representar textos.

```python
nome = "Maria"
```

### Tuplas

São sequências que não podem ser modificadas após sua criação.

```python
coordenada = (10, 20)
```

### Conjuntos

Armazenam elementos sem duplicação.

```python
numeros = {1, 2, 3}
```

### Dicionários

Associam chaves a valores.

```python
aluno = {
    "nome": "Maria",
    "idade": 20
}
```

### Dataclasses

Facilitam a representação de entidades estruturadas.

```python
from dataclasses import dataclass

@dataclass
class Aluno:
    nome: str
    idade: int
```

### Listas de objetos

Permitem armazenar coleções de entidades.

```python
alunos = [
    Aluno("Maria", 20),
    Aluno("João", 21)
]
```

### Modelagem

Define quais entidades, atributos e relações são relevantes para o problema.

### Abstração

Permite concentrar a representação nos aspectos importantes.

---

# 21. Questões de revisão

### Questão 1

O que é uma estrutura de dados?

### Questão 2

Qual é a diferença entre uma variável e uma lista?

### Questão 3

Qual é o primeiro índice de uma lista em Python?

### Questão 4

Quantos elementos existem em:

```python
valores = [10, 20, 30, 40, 50]
```

E qual é o maior índice válido?

### Questão 5

O que representa:

```python
matriz[2][3]
```

?

### Questão 6

Qual é a diferença entre uma lista e uma tupla?

### Questão 7

Para que serve um dicionário?

### Questão 8

Para que podemos utilizar uma `dataclass`?

### Questão 9

Por que podemos utilizar uma lista de objetos?

### Questão 10

O que significa modelar um problema?

### Questão 11

Explique o conceito de abstração utilizando um exemplo de sistema computacional.

### Questão 12

Por que o código abaixo pode produzir um comportamento inesperado?

```python
matriz = [[0] * 3] * 3
```

---

# 22. Gabarito

**1.** Uma estrutura de dados é uma forma de organizar informações para facilitar seu armazenamento, acesso e processamento.

**2.** Uma variável referencia um objeto individual; uma lista permite organizar uma sequência de elementos.

**3.** `0`.

**4.** Cinco elementos; índices de `0` a `4`.

**5.** O elemento da linha de índice `2` e coluna de índice `3`. Para existir, a matriz precisa ter pelo menos quatro colunas e três linhas.

**6.** Listas são mutáveis; tuplas são imutáveis após sua criação.

**7.** Para associar chaves a valores e representar informações por meio dessas associações.

**8.** Para representar entidades estruturadas com atributos definidos e, quando necessário, comportamentos associados.

**9.** Para armazenar várias entidades que possuem a mesma estrutura, como uma lista de alunos ou produtos.

**10.** Identificar e organizar as informações relevantes de um problema.

**11.** Abstração é representar somente as características relevantes para determinado problema, ignorando detalhes desnecessários.

**12.** Porque as três linhas internas referenciam a mesma lista. Uma alteração em uma linha pode afetar as demais. Uma alternativa adequada é:

```python
matriz = [[0] * 3 for _ in range(3)]
```

---

# 23. Conclusão

O estudo de Estrutura de Dados começa pela compreensão de como os dados são representados e organizados.

Em Python, podemos trabalhar com estruturas de alto nível que tornam a representação dos dados bastante expressiva.

A progressão fundamental desta unidade é:

```text
VARIÁVEL
   ↓
LISTA
   ↓
MATRIZ
   ↓
DICIONÁRIO
   ↓
DATACLASS
   ↓
LISTA DE OBJETOS
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

Em Python, a facilidade da linguagem não elimina a necessidade de pensar sobre a organização dos dados. Pelo contrário: compreender as características de cada estrutura é essencial para escrever programas corretos, eficientes e fáceis de manter.
