# 📘 Unidade 6 — Estruturas de Dados: Variáveis Compostas Homogêneas Unidimensionais (Vetores)
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **vetores** (*arrays*);
- Entender o que são **Variáveis Compostas Homogêneas Unidimensionais (VCHU)**;
- Trabalhar com **índices** e **posições**;
- Realizar operações básicas com vetores;
- Aplicar vetores em problemas práticos;
- Desenvolver algoritmos com estruturas unidimensionais.

---

## 🧠 2. Introdução às Estruturas de Dados

### 🔹 Definição

Uma **estrutura de dados** é uma forma organizada de armazenar e manipular dados em um programa.

👉 Até este momento, normalmente trabalhamos com variáveis simples:

```PEQUI
inteiro idade
real nota
caractere letra
```

Cada variável simples armazena **um único valor** por vez.

Quando precisamos armazenar vários valores relacionados, usar muitas variáveis isoladas torna o algoritmo repetitivo e difícil de manter.

Exemplo ruim:

```PEQUI
real nota1, nota2, nota3, nota4, nota5
```

Para resolver esse tipo de problema, utilizamos **variáveis compostas**.

---

## 🧩 3. Variáveis Compostas Homogêneas Unidimensionais — VCHU

### 🔹 Definição

Uma **Variável Composta Homogênea Unidimensional (VCHU)** é uma estrutura capaz de armazenar **vários valores do mesmo tipo**, organizados em **uma única dimensão**.

Em programação, essa estrutura é conhecida como **vetor** ou **array unidimensional**.

👉 Em termos práticos:

> Um vetor é uma sequência de posições, todas com o mesmo nome, diferenciadas por índices.

### 🔹 Por que “homogênea”?

Porque todos os elementos armazenados são do **mesmo tipo**.

Exemplos:

```PEQUI
inteiro numeros[10]
real notas[4]
caractere letras[26]
```

✔ `numeros` armazena apenas inteiros.  
✔ `notas` armazena apenas reais.  
✔ `letras` armazena apenas caracteres.

### 🔹 Por que “unidimensional”?

Porque os dados são acessados por **um único índice**.

```PEQUI
notas[0]
notas[1]
notas[2]
notas[3]
```

---

## 📌 4. Índices e Posições

### 🔹 Diferença entre posição e índice

No cotidiano, normalmente contamos posições a partir de 1:

| Posição humana | 1ª | 2ª | 3ª | 4ª | 5ª |
|---|---:|---:|---:|---:|---:|
| Índice no vetor | 0 | 1 | 2 | 3 | 4 |

Em C, o primeiro elemento de um vetor está no índice `0`.

```C
int numeros[5];
```

Esse vetor possui 5 elementos:

```text
numeros[0], numeros[1], numeros[2], numeros[3], numeros[4]
```

⚠️ O índice `5` não pertence ao vetor `numeros[5]`.

---

## 🧱 5. Declaração de Vetores

### 🔹 Forma geral em pseudocódigo

```PEQUI
tipo nome[tamanho]
```

Exemplos:

```PEQUI
inteiro idades[30]
real notas[10]
caractere vogais[5]
```

### 🔹 Forma geral em C

```C
tipo nome[tamanho];
```

Exemplos:

```C
int idades[30];
float notas[10];
char vogais[5];
```

---

## ✏️ 6. Acesso e Alteração de Elementos

### 🔹 Atribuindo valores

```PEQUI
notas[0] ← 8.5
notas[1] ← 7.0
notas[2] ← 9.2
```

### 🔹 Lendo valores

```PEQUI
leia(notas[0])
leia(notas[1])
leia(notas[2])
```

### 🔹 Exibindo valores

```PEQUI
escreva(notas[0])
escreva(notas[1])
escreva(notas[2])
```

👉 O acesso direto por índice é útil, mas, quando o vetor possui muitos elementos, devemos usar estruturas de repetição.

---

## 🔁 7. Percorrendo Vetores com Laços

### 🔹 Leitura de um vetor

```PEQUI
algoritmo lerVetor
    inteiro numeros[5]
    inteiro i

    para i de 0 até 4 faça {
        escreva("Digite um número: ")
        leia(numeros[i])
    }
fimalgoritmo
```

### 🔹 Exibição de um vetor

```PEQUI
algoritmo exibirVetor
    inteiro numeros[5]
    inteiro i

    para i de 0 até 4 faça {
        escreva("Valor da posição ", i, ": ", numeros[i])
    }
fimalgoritmo
```

---

## 🧮 8. Operações Básicas com Vetores

### 🔹 Soma dos elementos

```PEQUI
inteiro numeros[5]
inteiro i, soma

soma ← 0

para i de 0 até 4 faça {
    soma ← soma + numeros[i]
}

escreva("Soma: ", soma)
```

### 🔹 Média dos elementos

```PEQUI
real notas[4]
real soma, media
inteiro i

soma ← 0

para i de 0 até 3 faça {
    soma ← soma + notas[i]
}

media ← soma / 4
escreva("Média: ", media)
```

### 🔹 Maior elemento

```PEQUI
inteiro numeros[5]
inteiro maior, i

maior ← numeros[0]

para i de 1 até 4 faça {
    se (numeros[i] > maior) então {
        maior ← numeros[i]
    }
}

escreva("Maior valor: ", maior)
```

### 🔹 Menor elemento

```PEQUI
inteiro numeros[5]
inteiro menor, i

menor ← numeros[0]

para i de 1 até 4 faça {
    se (numeros[i] < menor) então {
        menor ← numeros[i]
    }
}

escreva("Menor valor: ", menor)
```

---

## 🔎 9. Busca em Vetores

### 🔹 Busca sequencial

A **busca sequencial** percorre o vetor elemento por elemento até encontrar o valor procurado ou chegar ao final.

```PEQUI
inteiro numeros[10]
inteiro i, procurado, posicao

posicao ← -1

escreva("Digite o valor procurado: ")
leia(procurado)

para i de 0 até 9 faça {
    se (numeros[i] = procurado) então {
        posicao ← i
    }
}

se (posicao <> -1) então {
    escreva("Valor encontrado no índice ", posicao)
} senão {
    escreva("Valor não encontrado")
}
```

⚠️ Quando houver valores repetidos, esse algoritmo guarda a última posição encontrada. Para guardar a primeira, basta interromper a busca quando encontrar o elemento.

---

## 🔄 10. Cópia, Inversão e Troca de Elementos

### 🔹 Copiando um vetor

```PEQUI
inteiro origem[5]
inteiro destino[5]
inteiro i

para i de 0 até 4 faça {
    destino[i] ← origem[i]
}
```

### 🔹 Exibindo um vetor em ordem inversa

```PEQUI
inteiro numeros[5]
inteiro i

para i de 4 até 0 passo -1 faça {
    escreva(numeros[i])
}
```

### 🔹 Trocando dois elementos

```PEQUI
inteiro temp

temp ← numeros[0]
numeros[0] ← numeros[1]
numeros[1] ← temp
```

---

## 🧪 11. Exemplo Completo — Notas de uma Turma

### 🔹 Problema

Leia as notas de 5 alunos, armazene-as em um vetor, calcule a média da turma e informe quantos alunos ficaram acima da média.

### 🔹 Solução em PEQUI

```PEQUI
algoritmo notasTurma
    real notas[5]
    real soma, media
    inteiro i, acimaMedia

    soma ← 0
    acimaMedia ← 0

    para i de 0 até 4 faça {
        escreva("Digite a nota do aluno ", i + 1, ": ")
        leia(notas[i])
        soma ← soma + notas[i]
    }

    media ← soma / 5

    para i de 0 até 4 faça {
        se (notas[i] > media) então {
            acimaMedia ← acimaMedia + 1
        }
    }

    escreva("Média da turma: ", media)
    escreva("Alunos acima da média: ", acimaMedia)
fimalgoritmo
```

---

## 🧩 12. Vetores com Modularização

Vetores podem ser usados em funções e procedimentos. Em geral, passamos o vetor e o seu tamanho.

### 🔹 Exemplo conceitual

```PEQUI
void lerVetor(ref vetor, tamanho){
    inteiro i

    para i de 0 até tamanho - 1 faça {
        leia(vetor[i])
    }
}

real calcularMedia(vetor, tamanho){
    inteiro i
    real soma

    soma ← 0

    para i de 0 até tamanho - 1 faça {
        soma ← soma + vetor[i]
    }

    retorne soma / tamanho
}
```

### 🔹 Exemplo em C

```C
#include <stdio.h>

void lerVetor(int vetor[], int tamanho) {
    for (int i = 0; i < tamanho; i++) {
        printf("Digite o valor %d: ", i + 1);
        scanf("%d", &vetor[i]);
    }
}

int encontrarMaior(int vetor[], int tamanho) {
    int maior = vetor[0];

    for (int i = 1; i < tamanho; i++) {
        if (vetor[i] > maior) {
            maior = vetor[i];
        }
    }

    return maior;
}

int main() {
    int numeros[10];

    lerVetor(numeros, 10);
    printf("Maior valor: %d\n", encontrarMaior(numeros, 10));

    return 0;
}
```

---

## ⚠️ 13. Erros Comuns com Vetores

| Erro | Exemplo | Problema |
|---|---|---|
| Acessar índice inexistente | `vetor[10]` em vetor de tamanho 10 | O último índice é 9 |
| Esquecer inicialização | `soma ← soma + vetor[i]` com `soma` sem valor inicial | Resultado imprevisível |
| Confundir posição com índice | Usar `1` para o primeiro elemento | Em C, o primeiro índice é 0 |
| Repetir código desnecessariamente | Ler `nota1`, `nota2`, `nota3`... | Vetor resolveria melhor |
| Usar tamanho fixo em vários lugares | `para i de 0 até 9` espalhado no código | Dificulta manutenção |

---

## ✅ 14. Boas Práticas

- Use nomes no plural para vetores: `notas`, `idades`, `salarios`;
- Crie constantes para representar tamanhos fixos;
- Sempre valide os limites dos índices;
- Inicialize acumuladores antes de usar;
- Use laços para percorrer vetores;
- Prefira funções e procedimentos para leitura, exibição, busca e cálculo;
- Evite duplicação de código;
- Teste o algoritmo com valores simples antes de usar entradas maiores.

---

## 📝 15. Lista de Exercícios

### 🔹 Nível Básico

1. Explique, com suas palavras, o que é um vetor.
2. Defina o que é uma Variável Composta Homogênea Unidimensional.
3. Qual é o primeiro índice de um vetor em C?
4. Declare um vetor de 20 números inteiros.
5. Declare um vetor de 4 notas reais.
6. Escreva um algoritmo que leia 5 números inteiros e os apresente na mesma ordem.
7. Escreva um algoritmo que leia 5 números inteiros e os apresente na ordem inversa.
8. Escreva um algoritmo que leia 10 números e calcule a soma dos valores.

### 🔹 Nível Intermediário

9. Leia 10 números inteiros e informe o maior e o menor valor.
10. Leia 8 notas reais e calcule a média da turma.
11. Leia 10 números inteiros e conte quantos são pares.
12. Leia 10 números inteiros e conte quantos são positivos, negativos e iguais a zero.
13. Leia um vetor de 10 posições e um número procurado. Informe se o número está no vetor.
14. Leia dois vetores de 5 posições e gere um terceiro vetor contendo a soma dos elementos correspondentes.
15. Leia um vetor de 10 posições e copie apenas os valores pares para outro vetor.

### 🔹 Nível Avançado

16. Crie um algoritmo modular que leia 10 números e use uma função para retornar o maior valor.
17. Crie um algoritmo modular que leia 10 números e use funções para calcular soma, média, maior e menor.
18. Leia um vetor com 10 números inteiros e ordene os valores em ordem crescente.
19. Leia um vetor com 10 números inteiros e remova logicamente os valores repetidos.
20. Leia as notas de uma turma e informe quais alunos ficaram acima da média.
21. Crie um menu com as opções: ler vetor, exibir vetor, calcular média, buscar valor e sair.
22. Refaça o exercício anterior usando funções e procedimentos para cada opção do menu.

---

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `vetores em C`; `arrays unidimensionais C`; `percorrer vetor C`; `maior menor vetor C`.
- 📚 **Leia materiais introdutórios sobre:** vetores, índices, percorrimento, busca, soma, média e maior/menor valor.
- 💻 **Pratique com:** leitura, exibição, soma, média, contagem de pares e inversão de vetores.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.

## 📌 Encerramento

Vetores são a base para o estudo de estruturas de dados em programação. Eles permitem armazenar vários valores do mesmo tipo sob um único nome, reduzindo repetição de código e facilitando a resolução de problemas com listas, séries, notas, idades, medidas e outros conjuntos lineares de dados.

O domínio de índices, laços e operações básicas com vetores é essencial para compreender estruturas mais complexas, como matrizes, strings, registros com vetores internos e arquivos de dados.