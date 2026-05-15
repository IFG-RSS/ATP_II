# 📘 Unidade 2 — Escopo de Variáveis, Modificadores e Depuração com IDE (CLion)
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

---

## 🎯 1. Objetivos da Aula

- Compreender o conceito de **escopo de variáveis**;
- Diferenciar variáveis **locais** e **globais**;
- Entender o papel dos **modificadores de acesso e armazenamento**;
- Identificar problemas comuns relacionados a escopo;
- Introduzir práticas de **depuração (debugging)**;
- Utilizar uma IDE profissional (**CLion**) para análise e correção de código.

---

## 🧠 2. Escopo de Variáveis

### 🔹 Definição

O **escopo** de uma variável define **onde ela pode ser acessada no programa**.

👉 Em termos práticos:
> “Em quais partes do código essa variável existe e pode ser utilizada?”

---

### 🔹 Tipos de Escopo

#### 📍 Escopo Local

> Variáveis declaradas dentro de funções, blocos ou estruturas de controle.

```text
void exemplo(){
    inteiro x = 10;
    escreva(x);
}
```

✔ A variável `x` só existe dentro da função.

#### 🌐 Escopo Global

> Variáveis declaradas fora de funções, acessíveis em todo o programa.

```PEQUI
inteiro contador = 0

void incrementar(){
   contador ← contador + 1
}
```

✔ Pode ser acessada por múltiplas funções.

⚠ Cuidado: uso excessivo de variáveis globais aumenta o *acoplamento*.

#### 🔹 Escopo de Bloco

> Variáveis declaradas dentro de estruturas como `se`, `para`, `enquanto`.

```PEQUI
se (condição){
    inteiro y = 5;
}
// y não existe aqui
```

### 🔹 Problemas Comuns de Escopo

- Uso de variável fora do seu escopo;
- Sobrescrita acidental de valores;
- Dificuldade de rastrear alterações;
- Dependência excessiva de variáveis globais.

---

## 🐞 3. Depuração de Código (Debugging)

### 🔹 Definição

> Depuração é o processo de identificar e corrigir erros no código.

### 🔹 Tipos de Erros

| Tipo de Erro | Descrição |
|---|---|
| Sintático | Erro de escrita, como falta de ponto e vírgula |
| Semântico | Código compila, mas faz algo inadequado |
| Lógico | Resultado incorreto devido à lógica |

### 🔹 Estratégias de Depuração

- Inserir comandos de saída;
- Testar partes isoladas do código;
- Verificar valores de variáveis;
- Utilizar ferramentas de depuração da IDE.

### 🔹 Exemplo de Erro Lógico

```PEQUI
inteiro soma = 0;
para i de 1 até 5 faça{
    soma = i;
}
escreva(soma);
```

❌ Resultado incorreto, pois a soma não foi acumulada.

✔ Correção:

```PEQUI
soma ← soma + i
```

---

## 🖥️ 4. Uso de IDE — CLion

O CLion é uma IDE profissional voltada para desenvolvimento em C e C++.

### 🔹 Principais Recursos

- Destaque de sintaxe;
- Autocompletar inteligente;
- Análise estática de código;
- Integração com compiladores;
- Ferramentas avançadas de depuração.

---

## ⚠️ 5. Boas Práticas

- Prefira variáveis locais;
- Evite uso excessivo de globais;
- Nomeie variáveis de forma clara;
- Utilize constantes sempre que possível;
- Depure frequentemente;
- Use a IDE como ferramenta de apoio, não apenas execução.

---

## 📝 6. Lista de Exercícios

### 🔹 Nível Básico

1. Defina escopo de variável.
2. Diferencie variável local e global.
3. O que acontece ao acessar uma variável fora do escopo?
4. Cite dois tipos de erro em programação.

### 🔹 Nível Intermediário

5. Analise o código abaixo e identifique o problema:

```PEQUI
void teste(){
    se (verdadeiro){
        inteiro x = 5;
    }
    escreva(x);
}
```

6. Explique o funcionamento de uma variável `static`.
7. Qual a vantagem de usar constantes?
8. Descreva o que é um breakpoint.

### 🔹 Nível Avançado

9. Explique como o uso excessivo de variáveis globais impacta o acoplamento.
10. Descreva um cenário real onde o uso do debugger é essencial para encontrar um erro.

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `escopo de variáveis C`; `variáveis locais e globais C`; `debugging C`; `breakpoint IDE`.
- 📚 **Leia materiais introdutórios sobre:** escopo de variáveis, variáveis locais e globais, modificadores e depuração.
- 💻 **Pratique com:** exemplos de escopo, shadowing, variáveis globais e correção de erros lógicos.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.

## 📌 Encerramento

O domínio do escopo de variáveis e dos modificadores é essencial para o desenvolvimento de código organizado, previsível e seguro. Aliado a isso, o uso de ferramentas de depuração eleva a capacidade de identificar e corrigir erros.