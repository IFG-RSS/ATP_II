# 📘 Unidade 4 — Modularização na Prática: Escopo de Variáveis, Passagem por Valor e Referência

## 🎯 1. Objetivos da Aula

* Aplicar o conceito de escopo de variáveis na prática;
* Diferenciar claramente escopo local, global e de bloco em algoritmos;
* Compreender passagem por valor e passagem por referência;
* Analisar efeitos colaterais em funções e procedimentos;
* Desenvolver código modular com controle adequado de dados.

## 🧠 2. Escopo de Variáveis, na Prática!

### 🔹 Revisão Rápida

O escopo define onde uma variável pode ser acessada.

### 🔹 Exemplo Prático

```PEQUI
    inteiro x = 10;
    
    VOID teste(){
        inteiro x = 5;
        escreva(x);
    }
    
    algoritmo principal{
        teste();
        escreva(x);
    }
```

#### 🔍 Análise
* **Dentro da função** → `x = 5` (escopo local)
* **Fora da função** → `x = 10` (escopo global)

👉 **Conclusão:** variáveis locais sobrescrevem (*shadowing*) variáveis globais dentro do seu escopo.

### 🔹 Escopo e Blocos

```PEQUI
    void exemplo(){
        se (verdadeiro) {
            inteiro y = 20;
            escreva(y);
        }
        escreva(y); // erro
    }
```

👉 `y` só existe dentro do bloco `se`.

### 🔹 Problemas Comuns

* Uso de variáveis fora do escopo;
* Confusão entre variáveis com mesmo nome;
* Dependência de variáveis globais;
* Dificuldade de rastreamento de valores.

## 🔄 3. Passagem de Parâmetros

Quando chamamos uma função ou procedimento, podemos passar valores de duas formas principais:

1. Por valor
2. Por referência

## 📥 4. Passagem por Valor

### 🔹 Definição

Na passagem por valor, uma cópia do valor é enviada para a função.

👉 Alterações dentro da função não afetam a variável original.

### 🔹 Exemplo

```PEQUI
    void alterarValor(x){
        x = x + 10;
    }
    
    algoritmo principal{
        inteiro a = 5;
        alterarValor(a);
        escreva(a);
    }
```

#### 🔍 Resultado
`5`

👉 O valor original não foi alterado.

### 🔹 Interpretação

* `x` é uma cópia de `a`;
* Alterações são locais;
* Seguro e previsível.

## 🔗 5. Passagem por Referência

### 🔹 Definição

Na passagem por referência, a função recebe o endereço da variável original.

👉 Alterações dentro da função afetam diretamente a variável original.

### 🔹 Exemplo Conceitual

```PEQUI
    void alterarValor(ref x){
        x = x + 10;
    }
    
    algoritmo principal{
        inteiro a = 5;
        alterarValor(a);
        escreva(a);
    }
```

#### 🔍 Resultado
`15`

### 🔹 Interpretação

* `x` referencia `a`;
* Alterações são persistentes;
* Pode gerar efeitos colaterais.

## ⚖️ 6. Comparação Direta

| Característica           | Por Valor | Por Referência |
|:-------------------------|:----------|:---------------|
| O que é passado          | Cópia     | Endereço       |
| Altera variável original | ❌ Não    | ✅ Sim         |
| Segurança                | Alta      | Menor          |
| Uso comum                | Cálculos  | Atualizações   |

## ⚠️ 7. Efeitos Colaterais

### 🔹 Definição

Um efeito colateral ocorre quando uma função altera dados fora do seu escopo local.

### 🔹 Exemplo

```PEQUI
    void atualizarSaldo(ref saldo){
        saldo = saldo - 100;
    }
```

👉 A variável externa é modificada diretamente.

### 🔹 Riscos

* Dificuldade de depuração;
* Comportamento inesperado;
* Dependência implícita entre módulos.

## ✅ 8. Boas Práticas

* Prefira passagem por valor quando possível;
* Use referência apenas quando necessário;
* Evite alterar variáveis globais dentro de funções;
* Nomeie parâmetros claramente;
* Documente efeitos colaterais;
* Mantenha alta coesão e baixo acoplamento.

## 🧪 9. Exemplo Completo

```PEQUI
    inteiro calcularDobro(x){
        retorne x * 2;
    }
    
    void dobrarValor(ref x){
        x = x * 2;
    }
    
    algoritmo principal{
        inteiro a = 10;
        inteiro b;
    
        b = calcularDobro(a);
        escreva("Valor de a: ", a);
        escreva("Valor de b: ", b);
    
        dobrarValor(a);
        escreva("Novo valor de a: ", a);
    }
```

## 📝 10. Lista de Exercícios

### 🔹 Nível Básico

1. O que é escopo de variável?
2. Qual a diferença entre escopo local e global?
3. O que é passagem por valor?
4. O que é passagem por referência?

### 🔹 Nível Intermediário

5. Analise o código e diga o resultado:

```PEQUI
    void teste(x){
        x = x + 5;
    }
    
    algoritmo principal{
        inteiro a = 10;
        teste(a);
        escreva(a);
    }
```

6. Reescreva o exercício anterior utilizando passagem por referência.
7. Explique o que é efeito colateral.
8. Dê um exemplo onde passagem por referência é necessária.

### 🔹 Nível Avançado

9. Crie um algoritmo que:
    * Receba um número;
    * Use uma função para calcular o triplo (por valor);
    * Use um procedimento para modificar o valor original (por referência).

10. Analise o impacto do uso de variáveis globais combinado com passagem por referência em sistemas grandes.

## 📌 Encerramento

O domínio do escopo e da passagem de parâmetros é essencial para controlar o fluxo de dados em programas modulares.

A escolha entre valor e referência impacta diretamente o comportamento do sistema, influenciando segurança, previsibilidade e facilidade de manutenção.
