# 📘 Unidade 8 — Estruturas de Dados: Variáveis Compostas Heterogêneas (Registros)
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **registros** (*records*);
- Entender o que são **estruturas de dados** e **Variáveis Compostas Heterogêneas (VCHeter)**;
- Trabalhar com **campos** e acesso a dados em registros;
- Utilizar **`typedef`** em C para definir tipos baseados em registros;
- Compreender **registros de registros**, também chamados de registros aninhados;
- Adicionar multidimensionalidade às VCHeter, por meio de **vetores e matrizes de registros**;
- Aplicar registros em problemas práticos;
- Desenvolver algoritmos modulares com registros.

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

Entretanto, muitos problemas exigem representar entidades compostas por dados de tipos diferentes. Um aluno, por exemplo, pode possuir nome, matrícula, notas, média, data de nascimento e endereço. Esses dados não pertencem todos ao mesmo tipo. Para esse caso, usamos **registros**.

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
 ├── nome        : texto
 ├── matricula   : inteiro
 ├── nota1       : real
 ├── nota2       : real
 └── media       : real
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

### 🔹 Forma geral em C com `struct`

```C
struct NomeDoRegistro {
    tipo campo1;
    tipo campo2;
    tipo campo3;
};
```

### 🔹 Exemplo em C com `struct`

```C
struct Aluno {
    char nome[60];
    int matricula;
    float nota1;
    float nota2;
    float media;
};
```

Nesse caso, a declaração de uma variável exige a palavra `struct`:

```C
struct Aluno aluno1;
```

---

## 🏷️ 5. Documento Extra — Uso de `typedef` com Registros em C

Em C, `typedef` permite criar um **nome de tipo** a partir de uma estrutura. Isso torna o código mais legível, reduz repetições e aproxima a sintaxe da ideia de criar um novo tipo abstrato para representar uma entidade.

### 🔹 Forma com `typedef struct` anônima

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
Aluno turma[30];
```

### 🔹 Forma com nome interno da `struct`

```C
typedef struct Aluno {
    char nome[60];
    int matricula;
    float nota1;
    float nota2;
    float media;
} Aluno;
```

Essa forma é útil quando a estrutura precisa referenciar a si mesma, como ocorre em estruturas encadeadas, ou quando se deseja manter um nome interno explícito.

### 🔹 Comparação rápida

```C
// Sem typedef
struct Aluno a1;

// Com typedef
typedef struct {
    char nome[60];
    int matricula;
} Aluno;

Aluno a2;
```

### ⚠️ Atenção

- `typedef` **não cria uma variável**; ele cria um nome de tipo;
- `typedef` **não elimina os campos**; o acesso continua sendo feito com `.` ou `->`;
- Em geral, usa-se nomes de tipos com inicial maiúscula, como `Aluno`, `Produto`, `Data`.

---

## 📌 6. Campos e Acesso aos Dados

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

## 🧪 7. Exemplo Básico — Cadastro de um Aluno

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
#include <string.h>

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
    fgets(aluno.nome, sizeof(aluno.nome), stdin);
    aluno.nome[strcspn(aluno.nome, "\n")] = '\0';

    printf("Matrícula: ");
    scanf("%d", &aluno.matricula);

    printf("Nota 1: ");
    scanf("%f", &aluno.nota1);

    printf("Nota 2: ");
    scanf("%f", &aluno.nota2);

    aluno.media = (aluno.nota1 + aluno.nota2) / 2;

    printf("Aluno: %s\n", aluno.nome);
    printf("Matrícula: %d\n", aluno.matricula);
    printf("Média: %.2f\n", aluno.media);

    return 0;
}
```

---

## 🔁 8. Registros com Modularização

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

### 🔹 Em C: `.` versus `->`

Em C, o acesso aos campos depende da forma como o registro é recebido:

```C
void exibirAluno(Aluno aluno) {
    printf("%s - %.2f\n", aluno.nome, aluno.media); // usa ponto
}

void atualizarMedia(Aluno *aluno) {
    aluno->media = (aluno->nota1 + aluno->nota2) / 2; // usa seta
}
```

- Use `.` quando tiver uma variável do tipo registro;
- Use `->` quando tiver um ponteiro para registro.

---

## 🧱 9. Documento Extra — Registros de Registros

### 🔹 Definição

Um **registro de registro** ocorre quando um campo de um registro também é um registro.

Essa técnica permite modelar entidades compostas de forma mais organizada. Em vez de colocar todos os campos em um único registro muito grande, agrupamos informações relacionadas em subestruturas.

### 🔹 Exemplo conceitual

```text
Aluno
 ├── nome        : texto
 ├── matricula   : inteiro
 ├── nascimento  : Data
 │    ├── dia     : inteiro
 │    ├── mes     : inteiro
 │    └── ano     : inteiro
 └── endereco    : Endereco
      ├── rua     : texto
      ├── cidade  : texto
      └── uf      : texto
```

### 🔹 Exemplo em PEQUI

```PEQUI
registro Data {
    inteiro dia
    inteiro mes
    inteiro ano
}

registro Endereco {
    string rua
    string cidade
    string uf
}

registro Aluno {
    string nome
    inteiro matricula
    Data nascimento
    Endereco endereco
}
```

### 🔹 Exemplo em C com `typedef`

```C
typedef struct {
    int dia;
    int mes;
    int ano;
} Data;

typedef struct {
    char rua[80];
    char cidade[60];
    char uf[3];
} Endereco;

typedef struct {
    char nome[60];
    int matricula;
    Data nascimento;
    Endereco endereco;
} Aluno;
```

### 🔹 Acesso a campos internos

```C
Aluno aluno;

aluno.nascimento.dia = 10;
aluno.nascimento.mes = 5;
aluno.nascimento.ano = 2006;

snprintf(aluno.endereco.cidade, sizeof(aluno.endereco.cidade), "Inhumas");
snprintf(aluno.endereco.uf, sizeof(aluno.endereco.uf), "GO");
```

Em PEQUI, a ideia é equivalente:

```PEQUI
aluno.nascimento.dia ← 10
aluno.endereco.cidade ← "Inhumas"
```

---

## 📚 10. Vetores de Registros

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

## 🧮 11. Matrizes de Registros

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

Quando o registro possui outro registro como campo, o acesso combina índices e campos internos:

```PEQUI
laboratorio[2][4].nascimento.ano
laboratorio[1][3].endereco.cidade
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

## 🧬 12. Registros com Vetores Internos

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

## 🏗️ 13. Registros Aninhados e Registros de Registros

A expressão **registro aninhado** é outra forma de se referir a **registro de registro**.

### 🔹 Exemplo com atividade acadêmica

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

### 🔹 Exemplo com vida acadêmica

```PEQUI
registro Disciplina {
    string codigo
    string nome
    inteiro cargaHoraria
    string status
}

registro Historico {
    Disciplina cursadas[40]
    inteiro quantidadeCursadas
}

registro Estudante {
    string nome
    inteiro matricula
    Historico historico
}
```

Acesso:

```PEQUI
estudante.historico.cursadas[0].nome
estudante.historico.quantidadeCursadas
```

---

## 🔎 14. Busca em Vetor de Registros

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

## 🔄 15. Atualização de Dados em Registros

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

## 🧭 16. Aplicações Práticas de Registros

Registros são úteis quando precisamos modelar entidades do mundo real.

| Entidade | Campos possíveis |
|---|---|
| Aluno | nome, matrícula, notas, média, data de nascimento, endereço |
| Disciplina | código, nome, carga horária, período, status |
| Produto | código, descrição, preço, quantidade, fornecedor |
| Conta bancária | número, titular, saldo, limite, data de abertura |
| Atividade acadêmica | título, descrição, data, prioridade, concluída |
| Livro | título, autor, ano, editora |
| Endereço | rua, número, bairro, cidade, UF, CEP |
| Pessoa | nome, CPF, data de nascimento, endereço |

---

## 🧪 17. Exemplo Completo — Sistema Simples de Alunos com Registros de Registros

### 🔹 Problema

Crie um programa que cadastre 3 alunos, guarde nome, matrícula, data de nascimento, endereço e notas. O programa deve calcular a média e permitir buscar um aluno pela matrícula.

### 🔹 Solução em C

```C
#include <stdio.h>
#include <string.h>

#define TAM_NOME 60
#define TAM_RUA 80
#define TAM_CIDADE 60
#define TAM_UF 3
#define TAM_TURMA 3

typedef struct {
    int dia;
    int mes;
    int ano;
} Data;

typedef struct {
    char rua[TAM_RUA];
    char cidade[TAM_CIDADE];
    char uf[TAM_UF];
} Endereco;

typedef struct {
    char nome[TAM_NOME];
    int matricula;
    Data nascimento;
    Endereco endereco;
    float nota1;
    float nota2;
    float media;
} Aluno;

void removerQuebraLinha(char texto[]) {
    texto[strcspn(texto, "\n")] = '\0';
}

float calcularMedia(Aluno aluno) {
    return (aluno.nota1 + aluno.nota2) / 2;
}

void lerData(Data *data) {
    printf("Dia: ");
    scanf("%d", &data->dia);
    printf("Mês: ");
    scanf("%d", &data->mes);
    printf("Ano: ");
    scanf("%d", &data->ano);
}

void limparBuffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF) {}
}

void lerAluno(Aluno *aluno) {
    printf("Nome: ");
    fgets(aluno->nome, TAM_NOME, stdin);
    removerQuebraLinha(aluno->nome);

    printf("Matrícula: ");
    scanf("%d", &aluno->matricula);

    printf("Data de nascimento:\n");
    lerData(&aluno->nascimento);
    limparBuffer();

    printf("Rua: ");
    fgets(aluno->endereco.rua, TAM_RUA, stdin);
    removerQuebraLinha(aluno->endereco.rua);

    printf("Cidade: ");
    fgets(aluno->endereco.cidade, TAM_CIDADE, stdin);
    removerQuebraLinha(aluno->endereco.cidade);

    printf("UF: ");
    fgets(aluno->endereco.uf, TAM_UF, stdin);
    removerQuebraLinha(aluno->endereco.uf);
    limparBuffer();

    printf("Nota 1: ");
    scanf("%f", &aluno->nota1);
    printf("Nota 2: ");
    scanf("%f", &aluno->nota2);
    limparBuffer();

    aluno->media = calcularMedia(*aluno);
}

int buscarPorMatricula(Aluno turma[], int tamanho, int matriculaBuscada) {
    for (int i = 0; i < tamanho; i++) {
        if (turma[i].matricula == matriculaBuscada) {
            return i;
        }
    }
    return -1;
}
```

---

## ⚠️ 18. Erros Comuns com Registros

| Erro | Exemplo | Problema |
|---|---|---|
| Esquecer o nome da variável antes do campo | `nome ← "Ana"` | O correto seria `aluno.nome` |
| Confundir tipo do registro com variável | `Aluno.nome` | `Aluno` é o tipo; o campo pertence a uma variável |
| Achar que `typedef` cria variável | `typedef struct {...} Aluno;` | Isso cria um tipo, não uma instância |
| Confundir `.` com `->` em C | `aluno->nome` quando `aluno` não é ponteiro | O operador depende da forma de acesso |
| Não inicializar registros internos | `aluno.nascimento.ano` sem leitura prévia | Pode usar lixo de memória |
| Não recalcular campos derivados | Alterar notas e manter média antiga | Dados ficam inconsistentes |
| Passar por valor quando precisa alterar | `atualizarMedia(aluno)` | Pode não modificar o registro original |
| Não controlar tamanho do vetor de registros | Percorrer além da quantidade cadastrada | Acesso inválido à memória |
| Ler strings de forma incorreta em C | Misturar `scanf` e `fgets` sem cuidado | Pode pular leituras |

---

## ✅ 19. Boas Práticas

- Nomeie registros com substantivos no singular: `Aluno`, `Produto`, `Disciplina`;
- Nomeie vetores de registros no plural ou por coleção: `turma`, `produtos`, `disciplinas`;
- Use `typedef` para tornar o código em C mais legível;
- Defina registros auxiliares para dados compostos recorrentes, como `Data`, `Endereco`, `Contato`;
- Evite registros grandes demais; agrupe campos relacionados em registros internos;
- Agrupe campos que pertencem à mesma entidade;
- Use constantes para controlar tamanhos de strings, vetores e matrizes;
- Use funções para cálculos e procedimentos para leitura/exibição;
- Atualize campos derivados sempre que os campos base forem modificados;
- Passe registros por referência quando precisar alterar o original;
- Valide buscas antes de acessar posições retornadas;
- Documente claramente quais funções apenas consultam e quais funções modificam registros.

---

## 📝 20. Lista de Exercícios

### 🔹 Nível Básico

1. Explique, com suas palavras, o que é um registro.
2. Defina o que é uma Variável Composta Heterogênea.
3. Qual é a diferença entre vetor e registro?
4. Qual é a diferença entre matriz e registro?
5. Explique a utilidade de `typedef` em C.
6. Qual é a diferença entre declarar `struct Aluno aluno;` e declarar `Aluno aluno;` usando `typedef`?
7. Crie um registro chamado `Produto` com os campos: código, descrição, preço e quantidade.
8. Crie um tipo `Produto` em C usando `typedef struct`.
9. Crie um registro chamado `Data` com os campos: dia, mês e ano.
10. Crie um registro chamado `Aluno` com os campos: nome, matrícula, nota1, nota2 e média.
11. Escreva um algoritmo que leia os dados de um aluno e exiba sua média.
12. Escreva um algoritmo que leia os dados de um produto e calcule o valor total em estoque.

### 🔹 Nível Intermediário

13. Crie um vetor de 5 alunos e leia os dados de todos eles.
14. Altere o exercício anterior para calcular a média de cada aluno.
15. Liste apenas os alunos com média maior ou igual a 6.
16. Busque um aluno pela matrícula em um vetor de registros.
17. Atualize as notas de um aluno encontrado pela matrícula.
18. Crie um registro `Disciplina` com nome, código, carga horária, período e status.
19. Crie um vetor de disciplinas e liste apenas as disciplinas já cursadas.
20. Crie um registro `Data` e utilize-o dentro de um registro `Atividade`.
21. Crie um registro `Endereco` e utilize-o dentro de um registro `Pessoa`.
22. Crie um registro `Aluno` contendo os registros internos `Data nascimento` e `Endereco endereco`.
23. Escreva um procedimento em C que receba `Data *data` e leia dia, mês e ano usando o operador `->`.
24. Escreva um procedimento em C que receba `Aluno *aluno` e altere seu endereço.

### 🔹 Nível Avançado

25. Crie um programa modular para cadastro, listagem, busca e alteração de alunos usando vetor de registros.
26. Crie um sistema de agenda acadêmica com registros contendo título, descrição, data, prioridade e status de conclusão.
27. Crie uma matriz de registros para representar os assentos de um laboratório. Cada posição deve armazenar nome, matrícula e data de nascimento do aluno.
28. Crie um registro `Aluno` que contenha um vetor de 4 notas. Calcule a média usando uma função.
29. Crie um vetor de registros `Produto` e implemente funções para calcular valor total do estoque, buscar produto por código e listar produtos com quantidade baixa.
30. Crie um menu com as opções: cadastrar, listar, buscar, alterar, remover logicamente e sair.
31. Modele, em registros, parte da vida acadêmica de um estudante: disciplinas cursadas, disciplinas em curso, atividades complementares, estágio e TCC.
32. Desenvolva um algoritmo que use registros aninhados, vetor de registros e passagem por referência no mesmo problema.
33. Modele uma biblioteca usando os tipos `Autor`, `Editora`, `Data` e `Livro`, de forma que `Livro` contenha registros internos.
34. Crie um sistema de produtos em que `Produto` contenha `Fornecedor`, `Data validade` e vetor de preços históricos.
35. Implemente uma função que receba um vetor de `Aluno` e retorne a posição do aluno mais velho, considerando o campo `Data nascimento`.
36. Implemente um programa em C usando `typedef struct`, registros de registros, vetor de registros, busca por código e alteração por referência.

---

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `struct em C`; `typedef struct C`; `vetor de registros C`; `registro dentro de registro C`.
- 📚 **Leia materiais introdutórios sobre:** registros, campos, vetores de registros, matrizes de registros, registros de registros e typedef struct.
- 💻 **Pratique com:** cadastros de alunos, clientes, produtos e sistemas com registros compostos.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.

## 📌 Encerramento

Registros permitem representar entidades mais próximas da realidade, agrupando campos de diferentes tipos em uma mesma estrutura. Enquanto vetores e matrizes organizam coleções homogêneas, os registros possibilitam modelar dados compostos, como alunos, disciplinas, produtos, atividades e compromissos.

O uso de `typedef` torna a escrita em C mais limpa e facilita o uso de registros como tipos definidos pelo programador. Já os registros de registros permitem organizar melhor entidades complexas, evitando estruturas excessivamente grandes e favorecendo modularização, legibilidade e manutenção.

O domínio de registros, `typedef`, registros de registros, vetores de registros, matrizes de registros e registros com vetores internos é fundamental para construir programas mais completos, organizados e próximos de sistemas reais. Esse conteúdo também prepara o estudante para manipulação de arquivos, persistência de dados e desenvolvimento de projetos maiores em linguagem C.