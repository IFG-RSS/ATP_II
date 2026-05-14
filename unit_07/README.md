# 📘 Unidade 7 — Estruturas de Dados: Variáveis Compostas Homogêneas Multidimensionais (Matrizes)

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **matrizes** (*arrays multidimensionais*);
- Entender o que são **Variáveis Compostas Homogêneas Multidimensionais (VCHM)**;
- Trabalhar com **índices** e **posições** em estruturas multidimensionais;
- Realizar operações básicas com matrizes;
- Aplicar matrizes em problemas práticos;
- Desenvolver algoritmos com estruturas multidimensionais.

---

## 🧠 2. Revisão: Vetores e Evolução para Matrizes

Na unidade anterior, estudamos os **vetores**, que armazenam vários valores do mesmo tipo em uma única dimensão.

Exemplo:

```PEQUI
inteiro numeros[5]
```

Esse vetor possui uma linha lógica de dados:

```text
[10] [20] [30] [40] [50]
```

Quando os dados precisam ser organizados em **linhas e colunas**, utilizamos matrizes.

Exemplo de organização tabular:

```text
[ 1] [ 2] [ 3]
[ 4] [ 5] [ 6]
[ 7] [ 8] [ 9]
```

---

## 🧩 3. Variáveis Compostas Homogêneas Multidimensionais — VCHM

### 🔹 Definição

Uma **Variável Composta Homogênea Multidimensional (VCHM)** é uma estrutura capaz de armazenar vários valores do mesmo tipo, organizados em **mais de uma dimensão**.

A forma mais comum é a **matriz bidimensional**, organizada em:

- Linhas;
- Colunas.

👉 Em termos práticos:

> Uma matriz é uma tabela de elementos do mesmo tipo, acessados por dois índices: linha e coluna.

### 🔹 Por que “homogênea”?

Porque todos os elementos são do mesmo tipo.

```PEQUI
inteiro matriz[3][3]
real notas[5][4]
caractere tabuleiro[8][8]
```

### 🔹 Por que “multidimensional”?

Porque o acesso ao dado depende de mais de um índice.

```PEQUI
matriz[linha][coluna]
```

---

## 📌 4. Linhas, Colunas e Índices

### 🔹 Exemplo de matriz 3x3

```text
           Coluna 0   Coluna 1   Coluna 2
Linha 0       10         20         30
Linha 1       40         50         60
Linha 2       70         80         90
```

Acesso aos elementos:

```PEQUI
matriz[0][0] = 10
matriz[0][1] = 20
matriz[1][2] = 60
matriz[2][2] = 90
```

⚠️ Em C, tanto linhas quanto colunas começam no índice `0`.

---

## 🧱 5. Declaração de Matrizes

### 🔹 Forma geral em PEQUI

```PEQUI
tipo nome[quantidadeLinhas][quantidadeColunas]
```

Exemplos:

```PEQUI
inteiro matriz[3][3]
real notas[5][4]
inteiro tabela[10][6]
```

### 🔹 Forma geral em C

```C
tipo nome[quantidadeLinhas][quantidadeColunas];
```

Exemplos:

```C
int matriz[3][3];
float notas[5][4];
char tabuleiro[8][8];
```

---

## 🔁 6. Percorrendo Matrizes com Laços Aninhados

Para percorrer uma matriz, normalmente usamos dois laços:

- Um para as linhas;
- Outro para as colunas.

### 🔹 Leitura de uma matriz

```PEQUI
algoritmo lerMatriz
    inteiro matriz[3][3]
    inteiro i, j

    para i de 0 até 2 faça {
        para j de 0 até 2 faça {
            escreva("Digite o valor da posição [", i, "][", j, "]: ")
            leia(matriz[i][j])
        }
    }
fimalgoritmo
```

### 🔹 Exibição de uma matriz

```PEQUI
algoritmo exibirMatriz
    inteiro matriz[3][3]
    inteiro i, j

    para i de 0 até 2 faça {
        para j de 0 até 2 faça {
            escreva(matriz[i][j], " ")
        }
        escreva("\n")
    }
fimalgoritmo
```

---

## 🧮 7. Operações Básicas com Matrizes

### 🔹 Soma de todos os elementos

```PEQUI
inteiro matriz[3][3]
inteiro i, j, soma

soma ← 0

para i de 0 até 2 faça {
    para j de 0 até 2 faça {
        soma ← soma + matriz[i][j]
    }
}

escreva("Soma dos elementos: ", soma)
```

### 🔹 Maior e menor elemento

```PEQUI
inteiro matriz[3][3]
inteiro i, j, maior, menor

maior ← matriz[0][0]
menor ← matriz[0][0]

para i de 0 até 2 faça {
    para j de 0 até 2 faça {
        se (matriz[i][j] > maior) então {
            maior ← matriz[i][j]
        }

        se (matriz[i][j] < menor) então {
            menor ← matriz[i][j]
        }
    }
}

escreva("Maior: ", maior)
escreva("Menor: ", menor)
```

### 🔹 Soma dos elementos por linha

```PEQUI
inteiro matriz[3][3]
inteiro i, j, somaLinha

para i de 0 até 2 faça {
    somaLinha ← 0

    para j de 0 até 2 faça {
        somaLinha ← somaLinha + matriz[i][j]
    }

    escreva("Soma da linha ", i, ": ", somaLinha)
}
```

### 🔹 Soma dos elementos por coluna

```PEQUI
inteiro matriz[3][3]
inteiro i, j, somaColuna

para j de 0 até 2 faça {
    somaColuna ← 0

    para i de 0 até 2 faça {
        somaColuna ← somaColuna + matriz[i][j]
    }

    escreva("Soma da coluna ", j, ": ", somaColuna)
}
```

---

## 🧭 8. Diagonais de Matrizes Quadradas

Uma matriz é **quadrada** quando possui o mesmo número de linhas e colunas.

Exemplo:

```text
3x3, 4x4, 5x5
```

### 🔹 Diagonal principal

A diagonal principal é formada pelos elementos em que o índice da linha é igual ao índice da coluna.

```PEQUI
matriz[i][i]
```

Exemplo em uma matriz 3x3:

```text
[X] [ ] [ ]
[ ] [X] [ ]
[ ] [ ] [X]
```

### 🔹 Soma da diagonal principal

```PEQUI
inteiro matriz[3][3]
inteiro i, soma

soma ← 0

para i de 0 até 2 faça {
    soma ← soma + matriz[i][i]
}

escreva("Soma da diagonal principal: ", soma)
```

### 🔹 Diagonal secundária

A diagonal secundária é formada pelos elementos em que:

```PEQUI
linha + coluna = tamanho - 1
```

ou:

```PEQUI
matriz[i][tamanho - 1 - i]
```

Exemplo em uma matriz 3x3:

```text
[ ] [ ] [X]
[ ] [X] [ ]
[X] [ ] [ ]
```

---

## 🔄 9. Matriz Transposta

A **transposta** de uma matriz é obtida trocando linhas por colunas.

Se `A` é uma matriz `N x M`, sua transposta `T` será `M x N`.

### 🔹 Exemplo

Matriz original `2x3`:

```text
1 2 3
4 5 6
```

Matriz transposta `3x2`:

```text
1 4
2 5
3 6
```

### 🔹 Algoritmo

```PEQUI
inteiro matriz[2][3]
inteiro transposta[3][2]
inteiro i, j

para i de 0 até 1 faça {
    para j de 0 até 2 faça {
        transposta[j][i] ← matriz[i][j]
    }
}
```

---

## 🧪 10. Exemplo Completo — Operações em uma Matriz

### 🔹 Problema

Leia uma matriz `3x3`, exiba a matriz, calcule a soma total, o maior valor e a soma da diagonal principal.

### 🔹 Solução em PEQUI

```PEQUI
algoritmo operacoesMatriz
    inteiro matriz[3][3]
    inteiro i, j, soma, maior, somaDiagonal

    soma ← 0
    somaDiagonal ← 0

    para i de 0 até 2 faça {
        para j de 0 até 2 faça {
            escreva("Digite matriz[", i, "][", j, "]: ")
            leia(matriz[i][j])
        }
    }

    maior ← matriz[0][0]

    para i de 0 até 2 faça {
        para j de 0 até 2 faça {
            escreva(matriz[i][j], " ")
            soma ← soma + matriz[i][j]

            se (matriz[i][j] > maior) então {
                maior ← matriz[i][j]
            }
        }
        escreva("\n")
    }

    para i de 0 até 2 faça {
        somaDiagonal ← somaDiagonal + matriz[i][i]
    }

    escreva("Soma total: ", soma)
    escreva("Maior valor: ", maior)
    escreva("Soma da diagonal principal: ", somaDiagonal)
fimalgoritmo
```

---

## 🧩 11. Matrizes com Modularização

As operações com matrizes devem ser organizadas em funções e procedimentos.

### 🔹 Exemplo em C

```C
#include <stdio.h>

#define LINHAS 3
#define COLUNAS 3

void lerMatriz(int matriz[LINHAS][COLUNAS]) {
    for (int i = 0; i < LINHAS; i++) {
        for (int j = 0; j < COLUNAS; j++) {
            printf("Digite matriz[%d][%d]: ", i, j);
            scanf("%d", &matriz[i][j]);
        }
    }
}

void exibirMatriz(int matriz[LINHAS][COLUNAS]) {
    for (int i = 0; i < LINHAS; i++) {
        for (int j = 0; j < COLUNAS; j++) {
            printf("%d ", matriz[i][j]);
        }
        printf("\n");
    }
}

int somarMatriz(int matriz[LINHAS][COLUNAS]) {
    int soma = 0;

    for (int i = 0; i < LINHAS; i++) {
        for (int j = 0; j < COLUNAS; j++) {
            soma += matriz[i][j];
        }
    }

    return soma;
}

int main() {
    int matriz[LINHAS][COLUNAS];

    lerMatriz(matriz);
    exibirMatriz(matriz);

    printf("Soma: %d\n", somarMatriz(matriz));

    return 0;
}
```

---

## 🧠 12. Matrizes Especiais

### 🔹 Matriz quadrada

Uma matriz é quadrada quando:

```PEQUI
quantidadeLinhas = quantidadeColunas
```

### 🔹 Matriz diagonal

Uma matriz quadrada é diagonal quando todos os elementos fora da diagonal principal são iguais a zero.

```text
5 0 0
0 2 0
0 0 9
```

### 🔹 Matriz identidade

Uma matriz identidade é uma matriz quadrada em que:

- Os elementos da diagonal principal são iguais a `1`;
- Os demais elementos são iguais a `0`.

```text
1 0 0
0 1 0
0 0 1
```

### 🔹 Verificação de matriz identidade

```PEQUI
logico identidade
inteiro i, j

identidade ← verdadeiro

para i de 0 até n - 1 faça {
    para j de 0 até n - 1 faça {
        se (i = j e matriz[i][j] <> 1) então {
            identidade ← falso
        }

        se (i <> j e matriz[i][j] <> 0) então {
            identidade ← falso
        }
    }
}

se (identidade) então {
    escreva("É matriz identidade")
} senão {
    escreva("Não é matriz identidade")
}
```

---

## ⚠️ 13. Erros Comuns com Matrizes

| Erro | Exemplo | Problema |
|---|---|---|
| Acessar linha inexistente | `matriz[3][0]` em matriz 3x3 | Última linha é `2` |
| Acessar coluna inexistente | `matriz[0][3]` em matriz 3x3 | Última coluna é `2` |
| Inverter linha e coluna | Usar `matriz[coluna][linha]` sem intenção | Altera a lógica do algoritmo |
| Inicializar acumulador no lugar errado | `somaLinha ← 0` fora do laço da linha | Resultado acumulado incorretamente |
| Usar diagonal em matriz não quadrada | `matriz[i][i]` em matriz 2x5 | Conceito de diagonal exige matriz quadrada |

---

## ✅ 14. Boas Práticas

- Use nomes claros para os índices, como `linha` e `coluna`;
- Inicialize acumuladores no escopo correto;
- Verifique se a matriz é quadrada antes de trabalhar com diagonais;
- Use constantes para representar dimensões fixas;
- Separe leitura, exibição e processamento em funções/procedimentos;
- Teste com matrizes pequenas antes de aumentar as dimensões;
- Tome cuidado ao copiar, transpor ou ordenar dados em estruturas multidimensionais.

---

## 📝 15. Lista de Exercícios

### 🔹 Nível Básico

1. Explique, com suas palavras, o que é uma matriz.
2. Defina o que é uma Variável Composta Homogênea Multidimensional.
3. Qual é a diferença entre vetor e matriz?
4. Declare uma matriz `3x3` de inteiros.
5. Declare uma matriz `5x4` de notas reais.
6. Escreva um algoritmo que leia uma matriz `2x2` e a exiba em formato de matriz.
7. Escreva um algoritmo que leia uma matriz `3x3` e calcule a soma de todos os elementos.
8. Escreva um algoritmo que leia uma matriz `3x3` e encontre o maior valor.

### 🔹 Nível Intermediário

9. Leia uma matriz `3x3` e apresente a soma da diagonal principal.
10. Leia uma matriz `3x3` e apresente a soma da diagonal secundária.
11. Leia uma matriz `4x4` e apresente a soma de cada linha.
12. Leia uma matriz `4x4` e apresente a soma de cada coluna.
13. Leia uma matriz `N x M` e gere sua matriz transposta.
14. Leia uma matriz quadrada e verifique se ela é diagonal.
15. Leia uma matriz quadrada e verifique se ela é identidade.
16. Leia 10 números inteiros e armazene-os em um vetor. Em seguida, organize-os em uma matriz `2x5` e apresente-a em formato de matriz.
17. Leia 5 nomes de alunos e as 4 notas de cada aluno. Armazene as notas em matriz, calcule a média e apresente o nome do aluno e sua média na mesma linha.

### 🔹 Nível Avançado

18. Altere o exercício dos alunos e notas para apresentar a listagem em ordem decrescente pela média.
19. Crie um algoritmo que receba uma sequência de `k` números inteiros e dois valores `n` e `m`. Em seguida, crie uma matriz `n x m` e a preencha com os elementos da sequência, na mesma ordem.
20. Crie um programa modular que leia uma matriz `N x M`, encontre o maior e o menor elemento, some linhas, some colunas e gere a transposta.
21. Crie um menu com as opções: ler matriz, exibir matriz, somar linhas, somar colunas, verificar identidade, gerar transposta e sair.
22. Resolva problemas práticos com matrizes, como tabuleiro de jogo, mapa de ocupação de sala ou tabela de notas.
23. Resolva exercícios de matrizes em plataformas de programação, como beecrowd: 1181, 1182, 1183, 1184, 1190, 1435, 1478 e 2450.

---

## 📌 Encerramento

Matrizes ampliam o conceito de vetor ao permitir a organização de dados em múltiplas dimensões. Elas são especialmente úteis para representar tabelas, mapas, tabuleiros, planilhas, notas, imagens e estruturas matemáticas.

O domínio de laços aninhados, índices de linha e coluna, diagonais, transposição e modularização é essencial para resolver problemas mais complexos e preparar o estudante para estruturas de dados heterogêneas, arquivos e projetos completos em C.

## 🌐 Complemente seu estudo na web

[W3-Schools - Arrays](https://www.w3schools.com/c/c_arrays.php)