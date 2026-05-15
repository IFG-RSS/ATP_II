# 📘 Unidade 10 — Bibliotecas Customizadas, Organização de Projetos e Preparação para o Projeto Final
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **bibliotecas** em linguagem C;
- Diferenciar arquivos de cabeçalho (`.h`) e arquivos de implementação (`.c`);
- Organizar programas maiores em múltiplos arquivos;
- Reutilizar funções, registros e constantes em diferentes partes do projeto;
- Preparar a estrutura inicial para projetos completos em C;
- Consolidar os conteúdos de modularização, registros, matrizes e arquivos.

---

## 📚 2. O que são Bibliotecas?

Bibliotecas são conjuntos de funções, tipos e constantes que podem ser reutilizados em um programa.

Em C, existem bibliotecas padrão, como:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
```

Também é possível criar bibliotecas próprias para organizar melhor o código.

---

## 🧱 3. Arquivo de Cabeçalho `.h`

O arquivo `.h` declara o que estará disponível para outros arquivos do programa.

```c
#ifndef ALUNO_H
#define ALUNO_H

typedef struct {
    char nome[80];
    int matricula;
    float media;
} Aluno;

void exibirAluno(Aluno aluno);
float calcularMedia(float n1, float n2);

#endif
```

---

## ⚙️ 4. Arquivo de Implementação `.c`

O arquivo `.c` implementa as funções declaradas no arquivo `.h`.

```c
#include <stdio.h>
#include "aluno.h"

void exibirAluno(Aluno aluno) {
    printf("Nome: %s\n", aluno.nome);
    printf("Matrícula: %d\n", aluno.matricula);
    printf("Média: %.2f\n", aluno.media);
}

float calcularMedia(float n1, float n2) {
    return (n1 + n2) / 2.0;
}
```

---

## 🧪 5. Programa Principal

```c
#include "aluno.h"

int main() {
    Aluno a = {"Maria", 123, 8.5};
    exibirAluno(a);
    return 0;
}
```

---

## 🗂️ 6. Organização Recomendada

```text
projeto/
├── main.c
├── aluno.h
├── aluno.c
├── arquivo.h
├── arquivo.c
└── README.md
```

### 🔹 Vantagens

- Código mais organizado;
- Reutilização de funções;
- Facilidade de manutenção;
- Separação de responsabilidades;
- Preparação para projetos maiores.

---

## 🧩 7. Relação com o Projeto Final

A organização em bibliotecas próprias permite separar:

- Funções de menu;
- Funções de leitura e escrita em arquivos;
- Funções de cadastro;
- Funções de busca;
- Funções de listagem;
- Tipos definidos com `typedef struct`;
- Validações e operações específicas.

---

## ⚠️ 8. Boas Práticas

- Use nomes claros para arquivos e funções;
- Separe declaração e implementação;
- Use proteção de inclusão com `#ifndef`, `#define` e `#endif`;
- Evite concentrar todo o código no `main.c`;
- Documente como compilar e executar o projeto;
- Teste cada módulo separadamente.

---

## 📝 9. Lista de Exercícios

### 🔹 Nível Básico

1. O que é uma biblioteca em C?
2. Qual a diferença entre arquivo `.h` e arquivo `.c`?
3. Para que serve o comando `#include`?
4. O que é uma biblioteca customizada?

### 🔹 Nível Intermediário

5. Crie uma biblioteca `matematica.h` e `matematica.c` com funções de soma, subtração e média.
6. Crie uma biblioteca `aluno.h` e `aluno.c` contendo um registro `Aluno` e uma função para exibir seus dados.
7. Separe um programa com menu em pelo menos dois arquivos `.c`.
8. Explique a função da proteção `#ifndef` em arquivos de cabeçalho.

### 🔹 Nível Avançado

9. Crie um projeto em C com bibliotecas para cadastro, listagem e persistência de registros em arquivo.
10. Organize um projeto com `main.c`, `menu.c`, `menu.h`, `cliente.c`, `cliente.h`, `arquivo.c` e `arquivo.h`.
11. Explique como a separação em bibliotecas contribui para coesão e baixo acoplamento.
12. Descreva uma estrutura de pastas para o projeto final da disciplina.

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `bibliotecas em C`; `arquivo header .h C`; `projeto C com múltiplos arquivos`; `compilar múltiplos arquivos gcc`.
- 📚 **Leia materiais introdutórios sobre:** bibliotecas customizadas, arquivos .h e .c, organização de projetos e modularização.
- 💻 **Pratique com:** separação de funções em bibliotecas, organização de tipos e criação de projetos modulares.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.

## 📌 Encerramento

A criação de bibliotecas customizadas é um passo importante para desenvolver programas maiores em C. Ela consolida a modularização e prepara o estudante para estruturar projetos completos com registros, vetores, matrizes, arquivos e funções reutilizáveis.