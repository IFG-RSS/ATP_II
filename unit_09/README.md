# 📘 Unidade 9 — Arquivos: Armazenamento de Registros em Memória Secundária

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **arquivo** como mecanismo de armazenamento em memória secundária;
- Diferenciar **memória primária** e **memória secundária**;
- Entender por que vetores, matrizes e registros armazenados apenas em memória são perdidos ao final da execução;
- Trabalhar com arquivos em linguagem C utilizando a biblioteca `stdio.h`;
- Abrir, fechar, ler e escrever arquivos de texto;
- Armazenar registros (`struct`) em arquivos;
- Carregar dados de arquivos para vetores de registros;
- Salvar alterações feitas em memória de volta para arquivos;
- Compreender a diferença entre arquivos de texto e arquivos binários;
- Desenvolver programas com persistência simples de dados.

---

## 📚 2. Tópicos da Unidade

1. Revisão de registros e vetores de registros;
2. Memória primária e memória secundária;
3. Conceito de arquivo;
4. Arquivos de texto e arquivos binários;
5. Fluxo básico de manipulação de arquivos;
6. Ponteiro para arquivo: `FILE *`;
7. Abertura de arquivos com `fopen`;
8. Fechamento de arquivos com `fclose`;
9. Modos de abertura de arquivos;
10. Escrita em arquivos de texto com `fprintf`;
11. Leitura de arquivos de texto com `fscanf` e `fgets`;
12. Armazenamento de registros em arquivos;
13. Leitura de registros a partir de arquivos;
14. Persistência de vetores de registros;
15. Busca, alteração e remoção lógica de registros;
16. Introdução a arquivos binários com `fwrite` e `fread`;
17. Tratamento de erros em arquivos;
18. Boas práticas de organização e modularização;
19. Exemplos completos;
20. Lista de exercícios.

---

## 🧠 3. Por que estudar arquivos?

Até este momento da disciplina, os dados trabalhados em algoritmos e programas foram armazenados principalmente em variáveis, vetores, matrizes e registros.

Essas estruturas ficam armazenadas na **memória principal** durante a execução do programa.

👉 O problema é que, ao encerrar o programa, os dados são perdidos.

### Exemplo

Se um programa cadastra alunos em um vetor de registros, os dados existem apenas enquanto o programa está em execução.

```c
typedef struct {
    char nome[80];
    int matricula;
    float media;
} Aluno;

Aluno alunos[100];
```

Ao finalizar o programa, o vetor `alunos` deixa de existir.

Para manter os dados disponíveis em uma próxima execução, é necessário gravá-los em **memória secundária**, normalmente por meio de arquivos.

---

## 💾 4. Memória Primária e Memória Secundária

### 🔹 Memória Primária

É a memória utilizada diretamente durante a execução do programa.

Exemplos:

- RAM;
- Variáveis;
- Vetores;
- Matrizes;
- Registros em execução.

Características:

- Rápida;
- Volátil;
- Perde os dados quando o programa termina;
- Usada para processamento imediato.

### 🔹 Memória Secundária

É a memória utilizada para armazenamento permanente dos dados.

Exemplos:

- HD;
- SSD;
- Pendrive;
- Cartão de memória;
- Arquivos armazenados no sistema operacional.

Características:

- Mais lenta que a memória principal;
- Não volátil;
- Mantém os dados após o encerramento do programa;
- Usada para persistência.

---

## 📄 5. O que é um arquivo?

Um **arquivo** é uma estrutura de armazenamento mantida em memória secundária.

Em programação, usamos arquivos para:

- Salvar dados produzidos pelo programa;
- Ler dados já existentes;
- Guardar cadastros;
- Registrar histórico de operações;
- Exportar relatórios;
- Importar informações.

### Exemplos de arquivos

```text
alunos.txt
clientes.txt
produtos.txt
notas.csv
historico.dat
```

---

## 🧾 6. Arquivos de Texto e Arquivos Binários

### 🔹 Arquivos de Texto

São arquivos legíveis diretamente por pessoas.

Exemplo de conteúdo de um arquivo `alunos.txt`:

```text
1001;Ana Maria;8.5
1002;João Pedro;7.0
1003;Carla Souza;9.2
```

Vantagens:

- Fácil leitura;
- Fácil inspeção manual;
- Pode ser aberto em editores de texto;
- Útil para aprendizado e depuração.

Desvantagens:

- Exige conversão entre texto e tipos numéricos;
- Pode ocupar mais espaço;
- Pode ser mais trabalhoso quando há muitos campos.

### 🔹 Arquivos Binários

São arquivos armazenados em formato próximo ao formato interno da memória.

Vantagens:

- Escrita e leitura mais diretas de registros;
- Pode ocupar menos espaço;
- Mais eficiente em muitos cenários.

Desvantagens:

- Não é facilmente legível por pessoas;
- Pode depender da representação interna da máquina;
- Exige mais cuidado na portabilidade.

---

## 🔁 7. Fluxo Básico de Manipulação de Arquivos

A manipulação de arquivos normalmente segue quatro etapas:

1. Declarar um ponteiro para arquivo;
2. Abrir o arquivo;
3. Ler ou escrever dados;
4. Fechar o arquivo.

### Exemplo geral

```c
#include <stdio.h>

int main() {
    FILE *arquivo;

    arquivo = fopen("dados.txt", "w");

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    fprintf(arquivo, "Primeira linha do arquivo\n");

    fclose(arquivo);

    return 0;
}
```

---

## 📌 8. Ponteiro para Arquivo: `FILE *`

Em C, arquivos são manipulados por meio de um ponteiro do tipo `FILE *`.

```c
FILE *arquivo;
```

Esse ponteiro representa a ligação entre o programa e o arquivo armazenado no sistema operacional.

👉 O programa não manipula diretamente o arquivo físico. Ele manipula o arquivo por meio desse ponteiro.

---

## 🚪 9. Abertura de Arquivos com `fopen`

A função `fopen` é usada para abrir um arquivo.

### Sintaxe

```c
arquivo = fopen("nome_do_arquivo", "modo");
```

### Exemplo

```c
FILE *arquivo;
arquivo = fopen("alunos.txt", "w");
```

Nesse exemplo, o arquivo `alunos.txt` será aberto para escrita.

---

## 🔐 10. Fechamento de Arquivos com `fclose`

Todo arquivo aberto deve ser fechado com `fclose`.

```c
fclose(arquivo);
```

Fechar o arquivo é importante porque:

- Libera recursos do sistema operacional;
- Garante que os dados sejam efetivamente gravados;
- Evita corrupção de dados;
- Evita perda de informações ainda pendentes em buffer.

---

## ⚙️ 11. Modos de Abertura de Arquivos

| Modo | Significado | Observação |
|---|---|---|
| `"r"` | Leitura | O arquivo deve existir |
| `"w"` | Escrita | Cria o arquivo ou apaga o conteúdo existente |
| `"a"` | Acrescentar | Escreve no final do arquivo |
| `"r+"` | Leitura e escrita | O arquivo deve existir |
| `"w+"` | Leitura e escrita | Cria ou apaga o arquivo existente |
| `"a+"` | Leitura e acréscimo | Escreve ao final |
| `"rb"` | Leitura binária | Arquivo binário |
| `"wb"` | Escrita binária | Arquivo binário |
| `"ab"` | Acréscimo binário | Arquivo binário |

⚠️ Atenção:

O modo `"w"` apaga o conteúdo anterior do arquivo caso ele já exista.

---

## ✍️ 12. Escrita em Arquivos de Texto

A função `fprintf` funciona de forma semelhante ao `printf`, mas escreve em um arquivo.

### Exemplo

```c
#include <stdio.h>

int main() {
    FILE *arquivo = fopen("mensagem.txt", "w");

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    fprintf(arquivo, "Algoritmos e Técnicas de Programação II\n");
    fprintf(arquivo, "Unidade 9 - Arquivos\n");

    fclose(arquivo);

    return 0;
}
```

---

## 📖 13. Leitura de Arquivos de Texto com `fscanf`

A função `fscanf` permite ler dados formatados de um arquivo.

### Exemplo de arquivo `numeros.txt`

```text
10 20 30
```

### Programa

```c
#include <stdio.h>

int main() {
    FILE *arquivo = fopen("numeros.txt", "r");
    int a, b, c;

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    fscanf(arquivo, "%d %d %d", &a, &b, &c);

    printf("Valores lidos: %d, %d, %d\n", a, b, c);

    fclose(arquivo);

    return 0;
}
```

---

## 🧵 14. Leitura de Linhas com `fgets`

A função `fgets` é usada para ler uma linha inteira do arquivo.

```c
fgets(linha, tamanho, arquivo);
```

### Exemplo

```c
#include <stdio.h>

int main() {
    FILE *arquivo = fopen("texto.txt", "r");
    char linha[120];

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    while (fgets(linha, 120, arquivo) != NULL) {
        printf("%s", linha);
    }

    fclose(arquivo);

    return 0;
}
```

👉 `fgets` é especialmente útil quando o arquivo contém nomes, frases ou textos com espaços.

---

## 🧱 15. Revisão: Registro em C

Um registro agrupa dados de tipos diferentes em uma única estrutura.

```c
typedef struct {
    int matricula;
    char nome[80];
    float media;
} Aluno;
```

Nesse exemplo, `Aluno` é um tipo composto heterogêneo que reúne:

- Matrícula;
- Nome;
- Média.

---

## 💾 16. Salvando um Registro em Arquivo de Texto

### Exemplo

```c
#include <stdio.h>

typedef struct {
    int matricula;
    char nome[80];
    float media;
} Aluno;

int main() {
    FILE *arquivo;
    Aluno aluno = {1001, "Ana Maria", 8.5};

    arquivo = fopen("alunos.txt", "w");

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    fprintf(arquivo, "%d;%s;%.2f\n", aluno.matricula, aluno.nome, aluno.media);

    fclose(arquivo);

    return 0;
}
```

### Conteúdo gerado no arquivo

```text
1001;Ana Maria;8.50
```

---

## 📥 17. Lendo um Registro de Arquivo de Texto

Considere o arquivo `alunos.txt`:

```text
1001;Ana Maria;8.50
```

### Programa

```c
#include <stdio.h>

#define TAM_NOME 80

typedef struct {
    int matricula;
    char nome[TAM_NOME];
    float media;
} Aluno;

int main() {
    FILE *arquivo;
    Aluno aluno;

    arquivo = fopen("alunos.txt", "r");

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    fscanf(arquivo, "%d;%79[^;];%f", &aluno.matricula, aluno.nome, &aluno.media);

    printf("Matrícula: %d\n", aluno.matricula);
    printf("Nome: %s\n", aluno.nome);
    printf("Média: %.2f\n", aluno.media);

    fclose(arquivo);

    return 0;
}
```

### Explicação do formato `%79[^;]`

Esse formato indica que o programa deve ler até encontrar o caractere `;`.

Assim, é possível ler nomes com espaços, como `Ana Maria`.

---

## 📚 18. Vetor de Registros + Arquivo

Um caso comum é manter os dados em um vetor de registros durante a execução e salvá-los em arquivo ao final.

### Estrutura

```c
#define MAX_ALUNOS 100

typedef struct {
    int matricula;
    char nome[80];
    float media;
} Aluno;
```

### Salvando vários alunos

```c
void salvarAlunos(Aluno alunos[], int quantidade) {
    FILE *arquivo = fopen("alunos.txt", "w");

    if (arquivo == NULL) {
        printf("Erro ao salvar alunos.\n");
        return;
    }

    for (int i = 0; i < quantidade; i++) {
        fprintf(arquivo, "%d;%s;%.2f\n",
                alunos[i].matricula,
                alunos[i].nome,
                alunos[i].media);
    }

    fclose(arquivo);
}
```

---

## 📤 19. Carregando Vários Registros do Arquivo

```c
int carregarAlunos(Aluno alunos[]) {
    FILE *arquivo = fopen("alunos.txt", "r");
    int quantidade = 0;

    if (arquivo == NULL) {
        return 0;
    }

    while (fscanf(arquivo, "%d;%79[^;];%f\n",
                  &alunos[quantidade].matricula,
                  alunos[quantidade].nome,
                  &alunos[quantidade].media) == 3) {
        quantidade++;
    }

    fclose(arquivo);
    return quantidade;
}
```

### Interpretação

- O arquivo é aberto para leitura;
- Cada linha representa um aluno;
- Cada aluno é carregado para uma posição do vetor;
- A função retorna a quantidade de alunos carregados.

---

## 🔎 20. Busca em Vetor Carregado de Arquivo

Depois de carregar os dados do arquivo para o vetor, as operações podem ser feitas normalmente em memória.

```c
int buscarPorMatricula(Aluno alunos[], int quantidade, int matricula) {
    for (int i = 0; i < quantidade; i++) {
        if (alunos[i].matricula == matricula) {
            return i;
        }
    }

    return -1;
}
```

👉 Se retornar `-1`, o aluno não foi encontrado.

---

## ✏️ 21. Alteração de Registros

Uma estratégia simples para alterar dados é:

1. Carregar todos os registros do arquivo para um vetor;
2. Buscar o registro desejado;
3. Alterar os dados no vetor;
4. Salvar novamente todo o vetor no arquivo.

### Exemplo conceitual

```c
int posicao = buscarPorMatricula(alunos, quantidade, 1001);

if (posicao != -1) {
    alunos[posicao].media = 9.0;
    salvarAlunos(alunos, quantidade);
}
```

---

## 🗑️ 22. Remoção Lógica de Registros

Em vez de apagar fisicamente uma linha do arquivo, pode-se usar um campo de status.

```c
typedef struct {
    int matricula;
    char nome[80];
    float media;
    int ativo;
} Aluno;
```

Nesse caso:

- `ativo = 1` indica registro válido;
- `ativo = 0` indica registro removido.

### Vantagem

A remoção lógica permite manter histórico e simplificar algumas operações.

---

## 🧩 23. Exemplo Completo: Cadastro Simples de Alunos

```c
#include <stdio.h>
#include <string.h>

#define MAX_ALUNOS 100
#define TAM_NOME 80

typedef struct {
    int matricula;
    char nome[TAM_NOME];
    float media;
    int ativo;
} Aluno;

void limparEnter(char texto[]) {
    texto[strcspn(texto, "\n")] = '\0';
}

void salvarAlunos(Aluno alunos[], int quantidade) {
    FILE *arquivo = fopen("alunos.txt", "w");

    if (arquivo == NULL) {
        printf("Erro ao abrir arquivo para escrita.\n");
        return;
    }

    for (int i = 0; i < quantidade; i++) {
        fprintf(arquivo, "%d;%s;%.2f;%d\n",
                alunos[i].matricula,
                alunos[i].nome,
                alunos[i].media,
                alunos[i].ativo);
    }

    fclose(arquivo);
}

int carregarAlunos(Aluno alunos[]) {
    FILE *arquivo = fopen("alunos.txt", "r");
    int quantidade = 0;

    if (arquivo == NULL) {
        return 0;
    }

    while (quantidade < MAX_ALUNOS &&
           fscanf(arquivo, "%d;%79[^;];%f;%d\n",
                  &alunos[quantidade].matricula,
                  alunos[quantidade].nome,
                  &alunos[quantidade].media,
                  &alunos[quantidade].ativo) == 4) {
        quantidade++;
    }

    fclose(arquivo);
    return quantidade;
}

void cadastrarAluno(Aluno alunos[], int *quantidade) {
    if (*quantidade >= MAX_ALUNOS) {
        printf("Limite de alunos atingido.\n");
        return;
    }

    printf("Matrícula: ");
    scanf("%d", &alunos[*quantidade].matricula);
    getchar();

    printf("Nome: ");
    fgets(alunos[*quantidade].nome, TAM_NOME, stdin);
    limparEnter(alunos[*quantidade].nome);

    printf("Média: ");
    scanf("%f", &alunos[*quantidade].media);

    alunos[*quantidade].ativo = 1;

    (*quantidade)++;

    salvarAlunos(alunos, *quantidade);
}

void listarAlunos(Aluno alunos[], int quantidade) {
    printf("\n--- Lista de Alunos ---\n");

    for (int i = 0; i < quantidade; i++) {
        if (alunos[i].ativo == 1) {
            printf("%d - %s - Média: %.2f\n",
                   alunos[i].matricula,
                   alunos[i].nome,
                   alunos[i].media);
        }
    }
}

int main() {
    Aluno alunos[MAX_ALUNOS];
    int quantidade;
    int opcao;

    quantidade = carregarAlunos(alunos);

    do {
        printf("\n1 - Cadastrar aluno\n");
        printf("2 - Listar alunos\n");
        printf("0 - Sair\n");
        printf("Opção: ");
        scanf("%d", &opcao);

        switch (opcao) {
            case 1:
                cadastrarAluno(alunos, &quantidade);
                break;
            case 2:
                listarAlunos(alunos, quantidade);
                break;
            case 0:
                printf("Encerrando...\n");
                break;
            default:
                printf("Opção inválida.\n");
        }
    } while (opcao != 0);

    return 0;
}
```

---

## 🗃️ 24. Introdução a Arquivos Binários

Em arquivos binários, é possível gravar o registro inteiro diretamente.

### Escrita com `fwrite`

```c
FILE *arquivo = fopen("alunos.dat", "wb");

if (arquivo != NULL) {
    fwrite(alunos, sizeof(Aluno), quantidade, arquivo);
    fclose(arquivo);
}
```

### Leitura com `fread`

```c
FILE *arquivo = fopen("alunos.dat", "rb");

if (arquivo != NULL) {
    quantidade = fread(alunos, sizeof(Aluno), MAX_ALUNOS, arquivo);
    fclose(arquivo);
}
```

### Interpretação

- `sizeof(Aluno)` informa o tamanho de cada registro;
- `quantidade` informa quantos registros serão gravados;
- `MAX_ALUNOS` informa o limite máximo de registros a serem lidos.

---

## ⚠️ 25. Tratamento de Erros

Sempre verifique se o arquivo foi aberto corretamente.

```c
FILE *arquivo = fopen("dados.txt", "r");

if (arquivo == NULL) {
    printf("Arquivo não encontrado ou erro de abertura.\n");
    return 1;
}
```

Situações comuns de erro:

- Arquivo inexistente;
- Falta de permissão;
- Caminho incorreto;
- Nome digitado incorretamente;
- Arquivo em uso por outro programa;
- Disco cheio;
- Falha na gravação.

---

## ✅ 26. Boas Práticas

- Sempre feche arquivos com `fclose`;
- Sempre teste se `fopen` retornou `NULL`;
- Use nomes de arquivos claros;
- Evite misturar lógica de menu, leitura de teclado e gravação em arquivo na mesma função;
- Crie funções específicas para salvar e carregar dados;
- Use constantes para tamanhos máximos;
- Use `typedef struct` para organizar registros;
- Prefira arquivos de texto durante o aprendizado;
- Use arquivos binários apenas quando compreender bem a estrutura dos dados;
- Faça backup antes de testar operações de sobrescrita;
- Cuidado com o modo `"w"`, pois ele apaga o conteúdo anterior do arquivo.

---

## 🧪 27. Estratégia Recomendada de Desenvolvimento

Para desenvolver programas com arquivos, recomenda-se seguir a sequência:

1. Criar o registro;
2. Criar o vetor de registros;
3. Implementar cadastro em memória;
4. Implementar listagem em memória;
5. Implementar busca em memória;
6. Implementar alteração em memória;
7. Implementar remoção lógica em memória;
8. Criar função para salvar dados em arquivo;
9. Criar função para carregar dados do arquivo;
10. Testar o sistema com dados reais.

Essa estratégia evita que o estudante tente resolver persistência antes de dominar a organização dos dados em memória.

---

## 🧩 28. Aplicação Prática: Sistema de Cadastro

A Unidade 9 permite evoluir programas anteriores para sistemas com persistência.

Exemplos:

- Cadastro de alunos;
- Cadastro de clientes;
- Cadastro de produtos;
- Controle de estoque;
- Agenda de compromissos;
- Histórico escolar;
- Venda de ingressos;
- Matriz curricular armazenada em arquivo;
- Registro de notas e faltas.

A ideia principal é:

> O programa carrega os dados do arquivo ao iniciar, manipula os dados em memória durante a execução e salva os dados novamente no arquivo após alterações.

---

## 📝 29. Lista de Exercícios

### 🔹 Nível Básico

1. Explique a diferença entre memória primária e memória secundária.
2. O que acontece com os dados armazenados em um vetor quando o programa é encerrado?
3. O que é um arquivo?
4. Para que serve o tipo `FILE *` em C?
5. Qual função é usada para abrir um arquivo em C?
6. Qual função é usada para fechar um arquivo em C?
7. Explique a diferença entre os modos `"r"`, `"w"` e `"a"`.
8. Crie um programa que escreva seu nome e seu curso em um arquivo chamado `dados.txt`.
9. Crie um programa que leia e exiba o conteúdo do arquivo `dados.txt`.
10. Crie um programa que leia três números de um arquivo e exiba a soma deles.

### 🔹 Nível Intermediário

11. Crie um programa que leia 5 números inteiros do teclado e grave todos em um arquivo chamado `numeros.txt`.
12. Crie um programa que leia os números gravados em `numeros.txt` e calcule a média.
13. Crie um registro `Produto` com código, nome, quantidade e preço. Grave um produto em arquivo de texto.
14. Altere o exercício anterior para gravar 5 produtos em um arquivo.
15. Crie uma função `salvarProdutos` que receba um vetor de produtos e grave seus dados em arquivo.
16. Crie uma função `carregarProdutos` que leia os produtos do arquivo e armazene em um vetor.
17. Crie uma função para listar apenas produtos com quantidade maior que zero.
18. Crie uma função para buscar um produto pelo código após carregar os dados do arquivo.
19. Crie uma função para alterar o preço de um produto e salvar novamente o arquivo.
20. Crie uma função para marcar um produto como inativo usando remoção lógica.

### 🔹 Nível Avançado

21. Desenvolva um sistema de cadastro de alunos com as funcionalidades: cadastrar, listar, buscar, alterar média e remover logicamente.
22. O sistema anterior deve carregar os alunos do arquivo ao iniciar e salvar os dados sempre que houver alteração.
23. Crie um sistema de agenda com registros contendo data, horário, descrição e status. Os dados devem ser armazenados em arquivo.
24. Crie um sistema de controle de estoque com vetor de registros e persistência em arquivo de texto.
25. Implemente paginação simples na listagem de registros carregados de arquivo.
26. Implemente uma busca parcial por nome em um vetor de registros carregado de arquivo.
27. Crie um relatório em arquivo contendo apenas registros ativos.
28. Refaça o cadastro de produtos usando arquivo binário com `fwrite` e `fread`.
29. Compare a implementação com arquivo de texto e arquivo binário. Indique vantagens e desvantagens de cada uma.
30. Desenvolva um pequeno sistema de venda de ingressos em que clientes e poltronas sejam armazenados em arquivos.

---

## 📌 30. Encerramento

O uso de arquivos permite que programas deixem de ser apenas soluções temporárias em memória e passem a armazenar dados de forma persistente.

Nesta unidade, os registros deixam de existir apenas durante a execução do programa e passam a ser gravados em memória secundária, permitindo que cadastros, históricos e configurações sejam recuperados em execuções futuras.

O domínio de arquivos é um passo essencial para a construção de sistemas mais completos, pois aproxima os algoritmos acadêmicos de aplicações reais com armazenamento permanente de informações.


## 🌐 Complemente seu estudo na web

[W3-Schools - C-Files](https://www.w3schools.com/c/c_files.php)