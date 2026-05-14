# 📘 Unidade 8 — Estruturas de Dados: Variáveis Compostas Heterogêneas (Registros)

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **registros** (*records*);
- Entender o que são **estruturas de dados** e **Variáveis Compostas Heterogêneas (VCHeter)**;
- Adicionar multidimensionalidade às VCHeter, por meio de **vetores e matrizes de registros**;
- Trabalhar com **campos** e acesso a dados em registros;
- Aplicar registros em problemas práticos;
- Desenvolver algoritmos com registros.

---

## 🧠 2. Revisão: Estruturas Homogêneas x Heterogêneas

Nas unidades anteriores, estudamos estruturas homogêneas:

- **Vetores**: vários valores do mesmo tipo em uma dimensão;
- **Matrizes**: vários valores do mesmo tipo em duas ou mais dimensões.

Exemplo de vetor homogêneo:

```PEQUI
real notas[4]
```

Esse vetor armazena apenas valores reais.

Entretanto, muitos problemas exigem representar entidades compostas por dados de tipos diferentes.

Exemplo: um aluno possui:

- Nome: texto;
- Matrícula: inteiro;
- Média: real;
- Situação: texto ou caractere.

Para esse caso, usamos **registros**.

---

## 🧩 3. Variáveis Compostas Heterogêneas — VCHeter

### 🔹 Definição

Uma **Variável Composta Heterogênea (VCHeter)** é uma estrutura capaz de armazenar vários dados relacionados, podendo cada dado possuir um tipo diferente.

Em programação, essa estrutura é normalmente chamada de:

- Registro;
- Record;
- Struct, em linguagem C.

👉 Em termos práticos:

> Um registro agrupa diferentes campos que descrevem uma mesma entidade.

### 🔹 Exemplo conceitual

```text
Aluno
 ├── nome       : texto
 ├── matricula  : inteiro
 ├── nota1      : real
 ├── nota2      : real
 └── media      : real
```

---

## 🧱 4. Declaração de Registros

### 🔹 Forma geral em PEQUI

```PEQUI
registro NomeDoRegistro {
    tipo campo1
    tipo campo2
    tipo campo3
}
```

### 🔹 Exemplo em PEQUI

```PEQUI
registro Aluno {
    string nome
    inteiro matricula
    real nota1
    real nota2
    real media
}
```

### 🔹 Forma geral em C

```C
struct NomeDoRegistro {
    tipo campo1;
    tipo campo2;
    tipo campo3;
};
```

### 🔹 Exemplo em C

```C
struct Aluno {
    char nome[60];
    int matricula;
    float nota1;
    float nota2;
    float media;
};
```

### 🔹 Usando `typedef` em C

```C
typedef struct {
    char nome[60];
    int matricula;
    float nota1;
    float nota2;
    float media;
} Aluno;
```

Com `typedef`, podemos declarar variáveis diretamente:

```C
Aluno aluno1;
```

---

## 📌 5. Campos e Acesso aos Dados

### 🔹 O que são campos?

Campos são as partes internas de um registro.

No registro `Aluno`, os campos são:

```PEQUI
nome
matricula
nota1
nota2
media
```

### 🔹 Acesso aos campos em PEQUI

```PEQUI
aluno.nome ← "Ana"
aluno.matricula ← 12345
aluno.nota1 ← 8.0
aluno.nota2 ← 7.5
aluno.media ← (aluno.nota1 + aluno.nota2) / 2
```

### 🔹 Acesso aos campos em C

```C
Aluno aluno;

aluno.matricula = 12345;
aluno.nota1 = 8.0;
aluno.nota2 = 7.5;
aluno.media = (aluno.nota1 + aluno.nota2) / 2;
```

Para texto em C, geralmente usamos funções próprias para strings:

```C
snprintf(aluno.nome, sizeof(aluno.nome), "Ana");
```

---

## 🧪 6. Exemplo Básico — Cadastro de um Aluno

### 🔹 Solução em PEQUI

```PEQUI
registro Aluno {
    string nome
    inteiro matricula
    real nota1
    real nota2
    real media
}

algoritmo cadastroAluno
    Aluno aluno

    escreva("Nome: ")
    leia(aluno.nome)

    escreva("Matrícula: ")
    leia(aluno.matricula)

    escreva("Nota 1: ")
    leia(aluno.nota1)

    escreva("Nota 2: ")
    leia(aluno.nota2)

    aluno.media ← (aluno.nota1 + aluno.nota2) / 2

    escreva("Aluno: ", aluno.nome)
    escreva("Matrícula: ", aluno.matricula)
    escreva("Média: ", aluno.media)
fimalgoritmo
```

### 🔹 Solução em C

```C
#include <stdio.h>

typedef struct {
    char nome[60];
    int matricula;
    float nota1;
    float nota2;
    float media;
} Aluno;

int main() {
    Aluno aluno;

    printf("Nome: ");
    fgets(aluno.nome, 60, stdin);

    printf("Matrícula: ");
    scanf("%d", &aluno.matricula);

    printf("Nota 1: ");
    scanf("%f", &aluno.nota1);

    printf("Nota 2: ");
    scanf("%f", &aluno.nota2);

    aluno.media = (aluno.nota1 + aluno.nota2) / 2;

    printf("Matrícula: %d\n", aluno.matricula);
    printf("Média: %.2f\n", aluno.media);

    return 0;
}
```

---

## 🔁 7. Registros com Modularização

Registros podem ser passados para funções e procedimentos.

### 🔹 Função para calcular média

```PEQUI
real calcularMedia(Aluno aluno){
    retorne (aluno.nota1 + aluno.nota2) / 2
}
```

### 🔹 Procedimento para exibir aluno

```PEQUI
void exibirAluno(Aluno aluno){
    escreva("Nome: ", aluno.nome)
    escreva("Matrícula: ", aluno.matricula)
    escreva("Média: ", aluno.media)
}
```

### 🔹 Alteração por referência

Quando uma função ou procedimento precisa alterar o registro original, utiliza-se passagem por referência.

```PEQUI
void atualizarMedia(ref Aluno aluno){
    aluno.media ← (aluno.nota1 + aluno.nota2) / 2
}
```

---

## 📚 8. Vetores de Registros

### 🔹 Definição

Um **vetor de registros** armazena vários registros do mesmo tipo.

Exemplo:

```PEQUI
Aluno turma[30]
```

Esse vetor pode armazenar 30 alunos, e cada aluno possui vários campos.

### 🔹 Acesso aos dados

```PEQUI
turma[0].nome
turma[0].matricula
turma[0].media
```

### 🔹 Exemplo — Leitura de uma turma

```PEQUI
registro Aluno {
    string nome
    inteiro matricula
    real nota1
    real nota2
    real media
}

algoritmo vetorDeRegistros
    Aluno turma[3]
    inteiro i

    para i de 0 até 2 faça {
        escreva("Nome do aluno ", i + 1, ": ")
        leia(turma[i].nome)

        escreva("Matrícula: ")
        leia(turma[i].matricula)

        escreva("Nota 1: ")
        leia(turma[i].nota1)

        escreva("Nota 2: ")
        leia(turma[i].nota2)

        turma[i].media ← (turma[i].nota1 + turma[i].nota2) / 2
    }

    para i de 0 até 2 faça {
        escreva(turma[i].nome, " - Média: ", turma[i].media)
    }
fimalgoritmo
```

---

## 🧮 9. Matrizes de Registros

### 🔹 Definição

Uma **matriz de registros** organiza registros em linhas e colunas.

Exemplo:

```PEQUI
Aluno laboratorio[4][5]
```

Esse exemplo pode representar um laboratório com 4 fileiras e 5 lugares, em que cada posição contém os dados de um aluno.

### 🔹 Acesso aos dados

```PEQUI
laboratorio[0][0].nome
laboratorio[1][3].matricula
laboratorio[2][4].media
```

### 🔹 Exemplo conceitual

```PEQUI
para linha de 0 até 3 faça {
    para coluna de 0 até 4 faça {
        escreva("Nome do aluno da posição [", linha, "][", coluna, "]: ")
        leia(laboratorio[linha][coluna].nome)
    }
}
```

---

## 🧬 10. Registros com Vetores Internos

Um registro também pode possuir vetores como campos.

### 🔹 Exemplo

```PEQUI
registro Aluno {
    string nome
    inteiro matricula
    real notas[4]
    real media
}
```

Nesse caso, cada aluno possui um vetor de 4 notas.

### 🔹 Cálculo da média

```PEQUI
real calcularMedia(Aluno aluno){
    inteiro i
    real soma

    soma ← 0

    para i de 0 até 3 faça {
        soma ← soma + aluno.notas[i]
    }

    retorne soma / 4
}
```

---

## 🏗️ 11. Registros Aninhados

Um registro pode conter outro registro como campo.

### 🔹 Exemplo

```PEQUI
registro Data {
    inteiro dia
    inteiro mes
    inteiro ano
}

registro Atividade {
    string descricao
    Data prazo
    logico concluida
}
```

Acesso aos campos:

```PEQUI
atividade.prazo.dia
atividade.prazo.mes
atividade.prazo.ano
```

---

## 🔎 12. Busca em Vetor de Registros

### 🔹 Problema

Buscar um aluno pela matrícula.

```PEQUI
inteiro buscarAlunoPorMatricula(Aluno turma[], inteiro tamanho, inteiro matriculaBuscada){
    inteiro i

    para i de 0 até tamanho - 1 faça {
        se (turma[i].matricula = matriculaBuscada) então {
            retorne i
        }
    }

    retorne -1
}
```

👉 Retornar `-1` é uma estratégia comum para indicar que o aluno não foi encontrado.

---

## 🔄 13. Atualização de Dados em Registros

### 🔹 Exemplo

Atualizar as notas de um aluno encontrado pela matrícula.

```PEQUI
void atualizarNotas(ref Aluno aluno){
    escreva("Nova nota 1: ")
    leia(aluno.nota1)

    escreva("Nova nota 2: ")
    leia(aluno.nota2)

    aluno.media ← (aluno.nota1 + aluno.nota2) / 2
}
```

Quando o registro precisa ser alterado, a passagem por referência é a forma mais adequada.

---

## 🧭 14. Aplicações Práticas de Registros

Registros são úteis quando precisamos modelar entidades do mundo real.

Exemplos:

| Entidade | Campos possíveis |
|---|---|
| Aluno | nome, matrícula, notas, média, situação |
| Disciplina | código, nome, carga horária, período, status |
| Produto | código, descrição, preço, quantidade |
| Conta bancária | número, titular, saldo, limite |
| Atividade acadêmica | título, descrição, data, prioridade, concluída |
| Livro | título, autor, ano, editora |

---

## 🧪 15. Exemplo Completo — Sistema Simples de Alunos

### 🔹 Problema

Crie um programa que cadastre 3 alunos, calcule a média de cada um e permita buscar um aluno pela matrícula.

### 🔹 Solução em PEQUI

```PEQUI
registro Aluno {
    string nome
    inteiro matricula
    real nota1
    real nota2
    real media
}

real calcularMedia(Aluno aluno){
    retorne (aluno.nota1 + aluno.nota2) / 2
}

inteiro buscarPorMatricula(Aluno turma[], inteiro tamanho, inteiro matriculaBuscada){
    inteiro i

    para i de 0 até tamanho - 1 faça {
        se (turma[i].matricula = matriculaBuscada) então {
            retorne i
        }
    }

    retorne -1
}

algoritmo sistemaAlunos
    Aluno turma[3]
    inteiro i, matriculaBuscada, posicao

    para i de 0 até 2 faça {
        escreva("Nome: ")
        leia(turma[i].nome)

        escreva("Matrícula: ")
        leia(turma[i].matricula)

        escreva("Nota 1: ")
        leia(turma[i].nota1)

        escreva("Nota 2: ")
        leia(turma[i].nota2)

        turma[i].media ← calcularMedia(turma[i])
    }

    escreva("Digite a matrícula procurada: ")
    leia(matriculaBuscada)

    posicao ← buscarPorMatricula(turma, 3, matriculaBuscada)

    se (posicao <> -1) então {
        escreva("Aluno encontrado: ", turma[posicao].nome)
        escreva("Média: ", turma[posicao].media)
    } senão {
        escreva("Aluno não encontrado")
    }
fimalgoritmo
```

---

## ⚠️ 16. Erros Comuns com Registros

| Erro | Exemplo | Problema |
|---|---|---|
| Esquecer o nome da variável antes do campo | `nome ← "Ana"` | O correto seria `aluno.nome` |
| Confundir tipo do registro com variável | `Aluno.nome` | `Aluno` é o tipo; o campo pertence a uma variável |
| Não recalcular campos derivados | Alterar notas e manter média antiga | Dados ficam inconsistentes |
| Passar por valor quando precisa alterar | `atualizarMedia(aluno)` | Pode não modificar o registro original |
| Não controlar tamanho do vetor de registros | Percorrer além da quantidade cadastrada | Acesso inválido à memória |
| Ler strings de forma incorreta em C | Misturar `scanf` e `fgets` sem cuidado | Pode pular leituras |

---

## ✅ 17. Boas Práticas

- Nomeie registros com substantivos no singular: `Aluno`, `Produto`, `Disciplina`;
- Nomeie vetores de registros no plural ou por coleção: `turma`, `produtos`, `disciplinas`;
- Agrupe campos que pertencem à mesma entidade;
- Evite registros com responsabilidades demais;
- Use funções para cálculos e procedimentos para leitura/exibição;
- Atualize campos derivados sempre que os campos base forem modificados;
- Passe registros por referência quando precisar alterar o original;
- Use constantes para controlar o tamanho máximo de vetores e matrizes de registros;
- Valide buscas antes de acessar posições retornadas.

---

## 📝 18. Lista de Exercícios

### 🔹 Nível Básico

1. Explique, com suas palavras, o que é um registro.
2. Defina o que é uma Variável Composta Heterogênea.
3. Qual é a diferença entre vetor e registro?
4. Qual é a diferença entre matriz e registro?
5. Crie um registro chamado `Produto` com os campos: código, descrição, preço e quantidade.
6. Crie um registro chamado `Aluno` com os campos: nome, matrícula, nota1, nota2 e média.
7. Escreva um algoritmo que leia os dados de um aluno e exiba sua média.
8. Escreva um algoritmo que leia os dados de um produto e calcule o valor total em estoque.

### 🔹 Nível Intermediário

9. Crie um vetor de 5 alunos e leia os dados de todos eles.
10. Altere o exercício anterior para calcular a média de cada aluno.
11. Liste apenas os alunos com média maior ou igual a 6.
12. Busque um aluno pela matrícula em um vetor de registros.
13. Atualize as notas de um aluno encontrado pela matrícula.
14. Crie um registro `Disciplina` com nome, código, carga horária, período e status.
15. Crie um vetor de disciplinas e liste apenas as disciplinas já cursadas.
16. Crie um registro `Data` e utilize-o dentro de um registro `Atividade`.

### 🔹 Nível Avançado

17. Crie um programa modular para cadastro, listagem, busca e alteração de alunos usando vetor de registros.
18. Crie um sistema de agenda acadêmica com registros contendo título, descrição, data, prioridade e status de conclusão.
19. Crie uma matriz de registros para representar os assentos de um laboratório. Cada posição deve armazenar nome e matrícula do aluno.
20. Crie um registro `Aluno` que contenha um vetor de 4 notas. Calcule a média usando uma função.
21. Crie um vetor de registros `Produto` e implemente funções para calcular valor total do estoque, buscar produto por código e listar produtos com quantidade baixa.
22. Crie um menu com as opções: cadastrar, listar, buscar, alterar, remover logicamente e sair.
23. Modele, em registros, parte da vida acadêmica de um estudante: disciplinas cursadas, disciplinas em curso, atividades complementares, estágio e TCC.
24. Desenvolva um algoritmo que use registros aninhados, vetor de registros e passagem por referência no mesmo problema.

---

## 📌 Encerramento

Registros permitem representar entidades mais próximas da realidade, agrupando campos de diferentes tipos em uma mesma estrutura. Enquanto vetores e matrizes organizam coleções homogêneas, os registros possibilitam modelar dados compostos, como alunos, disciplinas, produtos, atividades e compromissos.

O domínio de registros, vetores de registros, matrizes de registros e registros aninhados é fundamental para construir programas mais completos, organizados e próximos de sistemas reais. Esse conteúdo também prepara o estudante para manipulação de arquivos, persistência de dados e desenvolvimento de projetos maiores em linguagem C.
