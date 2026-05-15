# 📘 Unidade 4 — Modularização na Prática: Escopo de Variáveis, Passagem por Valor e Referência
---

## 🪪 Identificação

- 👨‍🏫 **Professor:** Prof. Rogério S. Silva
- 📘 **Disciplina:** ATP-II (Algoritmos e Técnicas de Programação II)
- 🏫 **Instituição:** Instituto Federal de Goiás — Campus Inhumas-GO

---

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

* **Dentro da função** → `x = 5`;
* **Fora da função** → `x = 10`.

👉 Variáveis locais podem ocultar variáveis globais dentro do seu escopo.

## 🔄 3. Passagem de Parâmetros

Quando chamamos uma função ou procedimento, podemos passar valores de duas formas principais:

1. Por valor;
2. Por referência.

## 📥 4. Passagem por Valor

Na passagem por valor, uma cópia do valor é enviada para a função.

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

Resultado: `5`.

## 🔗 5. Passagem por Referência

Na passagem por referência, a função recebe o endereço ou a referência da variável original.

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

Resultado: `15`.

## ⚖️ 6. Comparação Direta

| Característica | Por Valor | Por Referência |
|---|---|---|
| O que é passado | Cópia | Endereço/referência |
| Altera variável original | Não | Sim |
| Segurança | Maior | Exige cuidado |
| Uso comum | Cálculos | Atualizações |

## ⚠️ 7. Efeitos Colaterais

Um efeito colateral ocorre quando uma função altera dados fora do seu escopo local.

```PEQUI
void atualizarSaldo(ref saldo){
    saldo = saldo - 100;
}
```

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

9. Crie um algoritmo que receba um número, use uma função para calcular o triplo por valor e use um procedimento para modificar o valor original por referência.
10. Analise o impacto do uso de variáveis globais combinado com passagem por referência em sistemas grandes.

## 🌐 Complemente seu estudo na web

Use a web como apoio para revisar conceitos, comparar explicações e praticar, mantendo o foco na implementação própria dos algoritmos.

- 🔎 **Pesquise por:** `passagem por valor C`; `passagem por referência C ponteiros`; `efeitos colaterais funções`; `escopo modularização`.
- 📚 **Leia materiais introdutórios sobre:** passagem por valor, passagem por referência e efeitos colaterais.
- 💻 **Pratique com:** funções que alteram e não alteram variáveis externas, comparando os resultados.
- 🧪 **Teste no computador:** crie pequenos programas, compile, execute e depure os exemplos da unidade.
- 🧭 **Compare abordagens:** observe como diferentes materiais explicam o mesmo conceito e registre as diferenças no seu caderno de estudos.
- ⚠️ **Cuidado:** use materiais da web como apoio, mas implemente os algoritmos por conta própria, testando cada solução no computador.

## 📌 Encerramento

O domínio do escopo e da passagem de parâmetros é essencial para controlar o fluxo de dados em programas modulares. A escolha entre valor e referência impacta diretamente o comportamento do sistema, influenciando segurança, previsibilidade e facilidade de manutenção.