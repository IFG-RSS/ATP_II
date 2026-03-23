# 📘 Unidade 2 — Escopo de Variáveis, Modificadores e Depuração com IDE (CLion)

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

✔ A variável x só existe dentro da função.

#### 🌐 Escopo Global

> Variáveis declaradas fora de funções, acessíveis em todo o programa.
> > inteiro contador = 0

```PEQUI
   void incrementar()
      contador ← contador + 1
```

✔ Pode ser acessada por múltiplas funções.

⚠ Cuidado: uso excessivo de variáveis globais aumenta o *acoplamento*.

#### 🔹 Escopo de Bloco
> Variáveis declaradas dentro de estruturas como se, para, enquanto.
```PEQUI
    se (condição){
        inteiro y = 5;
    } 
    // y não existe aqui
```

🔹 Problemas Comuns de Escopo
* Uso de variável fora do seu escopo;
* Sobrescrita acidental de valores;
* Dificuldade de rastrear alterações;
* Dependência excessiva de variáveis globais.

## 🐞 3. Depuração de Código (Debugging)
### 🔹 Definição
> Depuração é o processo de identificar e corrigir erros no código.

### 🔹 Tipos de Erros

| Tipo de Erro | Descrição                                      |
|--------------|------------------------------------------------|
|   Sintático  | Erro de escrita (ex: falta de ponto e vírgula) |
|  Semântico   | Código compila, mas faz algo errado            |
|    Lógico    | Resultado incorreto devido à lógica            |

🔹 Estratégias de Depuração
* Inserir comandos de saída (print, escreva);
* Testar partes isoladas do código;
* Verificar valores de variáveis;
* Utilizar ferramentas de depuração da IDE.

### 🔹 Exemplo de Erro Lógico
```PEQUI
    inteiro soma = 0;
    para i de 1 até 5 faça{
        soma = i;
    }
    escreva(soma);
```

> ❌ Resultado incorreto (esperado: soma acumulada)

✔ Correção:
```PEQUI
   soma ← soma + i
```

## 🖥️ 4. Uso de IDE — CLion

### 🔹 O que é o CLion

> O CLion é uma IDE profissional da JetBrains voltada para desenvolvimento em C e C++.

### 🔹 Principais Recursos
* Destaque de sintaxe;
* Autocompletar inteligente;
* Análise estática de código;
* Integração com compiladores;
* Ferramentas avançadas de debug.

### 🔹 Fluxo Básico de Uso
* Criar projeto
* Escrever código
* Compilar
* Executar
* Depurar

## 🐞 5. Depuração no CLion

### 🔹 Breakpoints
> Permitem pausar a execução em pontos específicos.

👉 Clique na margem esquerda do código.

🔹 Execução Passo a Passo
* Step Over → executa linha atual
* Step Into → entra na função
* Step Out → sai da função

### 🔹 Inspeção de Variáveis

Durante a execução:

* Visualizar valores em tempo real;
* Identificar inconsistências;
* Acompanhar mudanças de estado.

### 🔹 Exemplo de Uso
```PEQUI
    inteiro x = 10;
    inteiro y = 0;
    inteiro resultado;
    
    resultado = x / y;
```
👉 O debugger permite identificar divisão por zero antes da falha total.

## ⚠️ 6. Boas Práticas

* Prefira variáveis locais;
* Evite uso excessivo de globais;
* Nomeie variáveis de forma clara;
* Utilize const sempre que possível;
* Depure frequentemente, não apenas ao final;
* Use a IDE como ferramenta de apoio, não apenas execução.
* Cuidado com os assistentes de IA nessa etapa de aprendizado.

## 📝 7. Lista de Exercícios

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

6. Explique o funcionamento de uma variável static.
7. Qual a vantagem de usar const?
8. Descreva o que é um breakpoint.

### 🔹 Nível Avançado

9. Explique como o uso excessivo de variáveis globais impacta o acoplamento.
10. Descreva um cenário real onde o uso do debugger é essencial para encontrar um erro.

## 📌 Encerramento

O domínio do escopo de variáveis e dos modificadores é essencial para o desenvolvimento de código organizado, previsível e seguro.
Aliado a isso, o uso de ferramentas de depuração em IDEs profissionais como o CLion eleva significativamente a capacidade de identificar e corrigir erros, tornando o processo de desenvolvimento mais eficiente e robusto.