# 📘 Unidade 5 — Recursividade, Ponteiros, Arrays e Strings
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **recursividade**;
- Identificar caso base e passo recursivo;
- Introduzir o conceito de **ponteiros** em C;
- Relacionar ponteiros com passagem por referência;
- Compreender que arrays e strings possuem relação direta com endereços de memória;
- Desenvolver funções recursivas simples e manipulações iniciais com ponteiros.

---

## 🔁 2. Recursividade

### 🔹 Definição

Uma função recursiva é uma função que chama a si mesma para resolver uma versão menor do problema.

### 🔹 Estrutura básica

Toda recursão precisa de:

- **Caso base:** condição de parada;
- **Passo recursivo:** chamada da função para um problema menor.

### 🔹 Exemplo: fatorial

```c
int fatorial(int n) {
    if (n == 0) {
        return 1;
    }
    return n * fatorial(n - 1);
}
```

---

## 📍 3. Ponteiros

### 🔹 Definição

Um ponteiro é uma variável que armazena o endereço de memória de outra variável.

```c
int x = 10;
int *p = &x;
```

### 🔹 Operadores principais

| Operador | Significado |
|---|---|
| `&` | Obtém o endereço de uma variável |
| `*` | Acessa o conteúdo apontado pelo ponteiro |

---

## 🔄 4. Ponteiros e Passagem por Referência

Em C, a passagem por referência é realizada com ponteiros.

```c
void alterar(int *x) {
    *x = *x + 10;
}

int main() {
    int valor = 5;
    alterar(&valor);
    printf("%d", valor);
    return 0;
}
```

Resultado: `15`.

---

## 🧩 5. Arrays e Strings como Estruturas Relacionadas a Ponteiros

Em C, o nome de um vetor representa o endereço do primeiro elemento.

```c
int numeros[3] = {10, 20, 30};
printf("%d", numeros[0]);
```

Strings são vetores de caracteres terminados por `\0`.

```c
char nome[20] = "Ana";
```

---

## ⚠️ 6. Cuidados Importantes

- Toda recursão precisa de caso base;
- Ponteiros não inicializados podem causar erros graves;
- Ao usar ponteiros, diferencie endereço e conteúdo;
- Strings precisam de espaço para o caractere `\0`;
- Teste funções recursivas com valores pequenos.

---

## 📝 7. Lista de Exercícios

### 🔹 Nível Básico

1. O que é recursividade?
2. Explique o que é caso base.
3. O que é um ponteiro?
4. Qual a diferença entre `&x` e `*p`?

### 🔹 Nível Intermediário

5. Implemente uma função recursiva para calcular o fatorial de um número.
6. Implemente uma função recursiva para imprimir números de 1 até `n`.
7. Crie uma função que receba um ponteiro para inteiro e dobre seu valor.
8. Explique por que arrays podem ser tratados como endereços em C.

### 🔹 Nível Avançado

9. Implemente uma função recursiva que calcule a soma dos elementos de um vetor.
10. Crie uma função que receba uma string e conte quantos caracteres ela possui, sem usar `strlen`.
11. Explique os riscos de uma função recursiva sem caso base.
12. Crie um programa que use ponteiros para trocar o valor de duas variáveis inteiras.

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `recursividade em C`; `ponteiros em C`; `arrays e ponteiros C`; `strings em C char array`.
- 📚 **Leia materiais introdutórios sobre:** recursividade, ponteiros, arrays e strings na linguagem C.
- 💻 **Pratique com:** fatorial, contagem recursiva, troca de valores com ponteiros e manipulação básica de strings.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.

## 📌 Encerramento

Recursividade e ponteiros ampliam a capacidade de resolver problemas em C, mas exigem atenção. Esses conceitos serão importantes para compreender passagem por referência, manipulação de vetores, strings, registros e arquivos.