# 📘 Unidade 1 — Apresentação da Disciplina e Introdução à Modularização

---

## 🎯 1. Objetivos da Aula

- Compreender a organização da disciplina (plano de ensino);
- Entender o que são algoritmos estruturados;
- Introduzir o conceito de **modularização**;
- Reconhecer a importância da decomposição de problemas;
- Relacionar modularização com **reutilização de código e bibliotecas**.

---

## 📖 2. Apresentação do Plano de Ensino

O plano de ensino é o documento que orienta toda a disciplina. Ele define:

- **Objetivos gerais e específicos** → o que se espera que o aluno aprenda;
- **Conteúdo programático** → tópicos que serão estudados;
- **Metodologia** → como as aulas serão conduzidas (teóricas, práticas, projetos);
- **Avaliação** → critérios (provas, trabalhos, participação);
- **Cronograma** → distribuição dos conteúdos ao longo do tempo.

👉 **Importância:**  
Permite ao aluno planejar seus estudos e compreender claramente as expectativas da disciplina.

---

## 🧠 3. Introdução aos Algoritmos Estruturados

Um **algoritmo** é uma sequência finita de passos bem definidos para resolver um problema.

### 🔹 Características de um bom algoritmo

- **Finitude** → sempre termina;
- **Precisão** → não ambíguo;
- **Entrada e saída definidas**;
- **Efetividade** → passos executáveis.

### 🔹 Estruturas Fundamentais

A programação estruturada é baseada em três estruturas de controle:

1. **Sequência** → execução linear de instruções
2. **Seleção** → tomada de decisão (if/else)
3. **Repetição** → execução iterativa (while, for)

---

## 🧩 4. Introdução à Modularização

### 🔹 Definição

**Modularização** é o processo de dividir um problema complexo em partes menores chamadas **módulos**, cada uma com responsabilidade bem definida.

### 🔹 Características dos Módulos

- Independência lógica;
- Responsabilidade única;
- Facilidade de teste;
- Possibilidade de reutilização.

---

### 🔹 Exemplo Conceitual

**Problema:** Sistema de cadastro de alunos.

**Sem modularização:**
- Um único bloco de código executa todas as tarefas.

**Com modularização:**
- `cadastrarAluno();`
- `validarDados();`
- `exibirInformacoes();`
- `salvarDados();`

---

### 🔹 Vantagens da Modularização

- Redução da complexidade;
- Melhoria da legibilidade;
- Facilidade de manutenção;
- Reutilização de código;
- Suporte ao desenvolvimento colaborativo.

---

### 🔹 Conceitos Fundamentais

- **Abstração** → focar no essencial;
- **Decomposição** → dividir o problema;
- **Coesão** → módulo com responsabilidade clara;
- **Acoplamento** → baixo nível de dependência entre módulos.

---

## 🧾 5. Exemplo Prático: Módulo de Validação de CPF

### 🔹 Contexto

O CPF é um identificador amplamente utilizado em diversos sistemas:

- Sistemas de cadastro
- Aplicações financeiras
- Sistemas governamentais
- Plataformas de e-commerce

👉 A validação deve ser consistente em todo o sistema, justificando a criação de um **módulo reutilizável**.

---

### 🔹 Responsabilidades do Módulo

- Normalizar entrada (remover pontos e traços);
- Verificar tamanho (11 dígitos);
- Identificar sequências inválidas (ex: todos os dígitos iguais);
- Calcular e validar dígitos verificadores;
- Retornar resultado booleano (válido/inválido).

---

### 🔹 Pseudocódigo do Módulo

```PEQUI
lógico validarCPF(cpf: cadeia){

    cpf ← removerCaracteresNaoNumericos(cpf);

    se comprimento(cpf) <> 11{
        retorne falso;
    }

    se todosDigitosIguais(cpf){
        retorne falso;
    }

    digito1 ← calcularPrimeiroDigito(cpf);
    digito2 ← calcularSegundoDigito(cpf);

    se (digito1 = obterDigito(cpf, 10)) e (digito2 = obterDigito(cpf, 11)) {
        retorne verdadeiro;
    }
    senão{
        retorne falso;
    }
}
```

### 🔹 Reutilização no Sistema

O módulo pode ser utilizado em:

- Cadastro de usuários
- Atualização cadastral
- Validação de formulários
- Integração com serviços externos

### 📌 Impacto direto:

* Elimina duplicação de código;
* Garante padronização;
* Reduz inconsistências.

## 📦 6. Modularização e Bibliotecas de Código
### 🔹 Conceito de Biblioteca

Uma biblioteca de código é um conjunto estruturado de funções ou módulos reutilizáveis, projetados para serem utilizados em múltiplos sistemas.

### 🔹 Relação com Modularização

A modularização é o fundamento para criação de bibliotecas:

* Modularização	Biblioteca
* Organização interna	Reutilização externa
* Escopo local	Escopo global
* Foco no problema atual	Foco em múltiplos projetos
### 🔹 Evolução do Módulo para Biblioteca

O módulo de CPF pode ser integrado em uma biblioteca maior:

```
bibliotecaValidacoes
    validarCPF();
    validarEmail();
    validarTelefone();
    validarCEP();
```
### 🔹 Benefícios das Bibliotecas
* Reutilização sistemática;
* Padronização de regras;
* Aumento da produtividade;
* Redução de retrabalho;
* Facilidade de manutenção e evolução.
### 🔹 Analogia
* Módulo → ferramenta individual
* Biblioteca → conjunto organizado de ferramentas
## 🧪 7. Exemplo de Estrutura Modular
```PEQUI
Algoritmo Principal {
    chamar lerDados();
    chamar validarCPF();
    chamar processarDados();
    chamar exibirResultado();
}
```
## 📝 8. Lista de Exercícios
### 🔹 Nível Básico

1. Defina algoritmo e cite duas características.

2. Diferencie:
   1. Sequência
   2. Seleção
   3. Repetição

3. Explique modularização.

4. Liste três vantagens da modularização.

### 🔹 Nível Intermediário

5. Desenvolva um algoritmo para calcular a média de três notas (sem modularização).

6. Reescreva o algoritmo anterior utilizando modularização.

7. Explique coesão com exemplo.

8. Explique acoplamento e sua importância.

### 🔹 Nível Avançado

9. Analise os benefícios de um módulo independente de validação de CPF.

10. Proponha uma biblioteca de validação contendo pelo menos cinco funções.

## 📌 Encerramento

A modularização é um princípio essencial na construção de software de qualidade. Ela permite organizar melhor a lógica, reduzir complexidade e preparar o sistema para evolução.

A evolução natural da modularização leva à construção de bibliotecas reutilizáveis, fundamentais em ambientes profissionais, onde produtividade, padronização e manutenção são requisitos críticos.