# 📘 Unidade 3 — Modularização: Funções, Procedimentos e Parâmetros
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de funções e procedimentos;
- Diferenciar funções de procedimentos;
- Entender o papel dos parâmetros de entrada;
- Compreender o retorno de dados;
- Aplicar modularização com passagem de dados entre módulos;
- Desenvolver algoritmos mais organizados e reutilizáveis.

## 🧠 2. Revisão: Modularização

> A modularização consiste em dividir um problema em partes menores chamadas módulos, cada uma responsável por uma tarefa específica.

Na prática, esses módulos são implementados como:

- Funções;
- Procedimentos.

## ⚙️ 3. Procedimentos

### 🔹 Definição

Um procedimento é um bloco de código que executa uma tarefa específica sem retornar valor.

### 🔹 Características

- Pode receber dados por parâmetros;
- Executa ações;
- Não retorna resultado diretamente;
- Pode exibir mensagens, alterar variáveis ou organizar etapas do programa.

### 🔹 Exemplo

```PEQUI
void exibirMensagem(){
    escreva("Bem-vindo ao sistema!");
}
```

### 🔹 Procedimento com parâmetro

```PEQUI
void exibirNome(string nome){
    escreva("Olá, ", nome);
}
```

## 🔁 4. Funções

### 🔹 Definição

Uma função é um módulo que recebe dados, processa informações e retorna um valor.

### 🔹 Características

- Possui tipo de retorno;
- Pode receber parâmetros;
- Deve retornar um valor compatível com o tipo declarado;
- Pode ser usada dentro de expressões.

### 🔹 Exemplo

```PEQUI
inteiro somar(a, b){
    retorne a + b;
}
```

### 🔹 Uso da função

```PEQUI
inteiro resultado;
resultado = somar(5, 3);
escreva(resultado);
```

## 🔍 5. Diferença entre Função e Procedimento

| Característica | Função | Procedimento |
|---|---|---|
| Retorno de valor | Sim | Não |
| Uso em expressões | Sim | Não |
| Objetivo principal | Calcular e retornar | Executar uma ação |

## 🔗 6. Parâmetros de Entrada

Parâmetros são valores enviados para funções ou procedimentos para serem utilizados no processamento.

```PEQUI
real calcularMedia(n1, n2){
    retorne (n1 + n2) / 2;
}
```

### 🔹 Por valor

- Uma cópia do valor é passada;
- Alterações internas não afetam a variável original.

### 🔹 Por referência

- A variável original é acessada;
- Alterações internas podem afetar o valor externo.

## 📤 7. Retorno de Dados

O retorno é o valor produzido por uma função após o processamento.

```PEQUI
inteiro quadrado(numero){
    retorne numero * numero;
}
```

Funções também podem ser combinadas:

```PEQUI
resultado = quadrado(somar(2, 3));
```

## 🧪 8. Exemplo Completo Modular

```PEQUI
real calcularMedia(n1, n2){
    retorne (n1 + n2) / 2;
}

void verificarAprovacao(media){
    se (media >= 6) {
        escreva("Aprovado");
    } senão {
        escreva("Reprovado");
    }
}

algoritmo principal {
    real m;
    m = calcularMedia(7, 5);
    verificarAprovacao(m);
}
```

## ⚠️ 9. Boas Práticas

- Use funções para cálculos e retornos;
- Use procedimentos para ações;
- Nomeie módulos de forma clara e descritiva;
- Evite funções muito longas;
- Prefira módulos com alta coesão;
- Evite dependências desnecessárias entre módulos.

## 🧩 10. Coesão e Acoplamento

Alta coesão significa que um módulo possui uma responsabilidade bem definida. Baixo acoplamento significa que um módulo depende pouco de outros módulos.

### ✅ Exemplo com alta coesão

```PEQUI
real calcularMedia(n1, n2){
    retorne (n1 + n2) / 2;
}

void imprimirRelatorio(aluno){
    escreva(aluno.nome, aluno.media);
}
```

### ❌ Exemplo com baixa coesão

```PEQUI
void processarAluno(aluno){
    calcularMedia(aluno);
    imprimirRelatorio(aluno);
    salvarNoBanco(aluno);
    enviarEmail(aluno);
}
```

## 📝 11. Lista de Exercícios

### 🔹 Nível Básico

1. Defina função e procedimento.
2. Qual a principal diferença entre função e procedimento?
3. O que são parâmetros?
4. O que é retorno de uma função?

### 🔹 Nível Intermediário

5. Escreva uma função que receba dois números e retorne o maior.
6. Crie um procedimento que receba um nome e exiba uma mensagem personalizada.
7. Explique a diferença entre passagem por valor e por referência.
8. Dado um algoritmo, identifique se um trecho deve ser função ou procedimento.

### 🔹 Nível Avançado

9. Desenvolva um algoritmo modular para ler três notas, calcular a média e informar aprovação.
10. Explique como funções contribuem para reutilização de código em sistemas maiores.

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `funções em C`; `procedimentos algoritmos`; `parâmetros em C`; `retorno de função C`.
- 📚 **Leia materiais introdutórios sobre:** modularização, funções, procedimentos, parâmetros e retorno de dados.
- 💻 **Pratique com:** funções pequenas para cálculo, validação, exibição e organização de programas.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.


## 📌 Encerramento

A utilização de funções e procedimentos é a base da modularização em programação. Esses mecanismos permitem construir soluções mais organizadas, reutilizáveis e fáceis de manter.