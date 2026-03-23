# 📘 Unidade 5 — Modularização: Recursividade e Ponteiros

## 🎯 1. Objetivos da Aula

* Compreender o conceito de recursividade;
* Diferenciar soluções iterativas e recursivas;
* Identificar caso base e caso recursivo;
* Entender o conceito de ponteiros;
* Relacionar ponteiros com passagem por referência;
* Compreender por que arrays e strings são ponteiros;
* Aplicar esses conceitos em exemplos práticos.

## 🔁 2. Recursividade

### 🔹 Definição

Recursividade é uma técnica onde uma função chama a si mesma para resolver um problema.

### 🔹 Estrutura de uma Função Recursiva

Uma função recursiva deve ter:

* **Caso base** → condição de parada
* **Caso recursivo** → chamada da própria função

### 🔹 Exemplo Clássico: Fatorial

```PEQUI
inteiro fatorial(n){
    se n = 0
        retorne 1;
    senão
        retorne n * fatorial(n - 1);
}
```

### 🔍 Execução (fatorial de 3)

```text
    fatorial(3)
    → 3 * fatorial(2)
    → 3 * (2 * fatorial(1))
    → 3 * (2 * (1 * fatorial(0)))
    → 3 * 2 * 1 * 1 = 6
```

### 🔹 Exemplo: Soma Recursiva

```PEQUI
    inteiro soma(n){
        se n = 0
            retorne 0;
        senão
            retorne n + soma(n - 1);
    }   
    
```

### ⚠️ Cuidados com Recursividade

* Esquecer o caso base → loop infinito;
* Alto consumo de memória (pilha);
* Pode ser menos eficiente que iteração.

## 🔄 3. Recursivo vs Iterativo

| Aspecto            | Recursivo                 | Iterativo        |
|:-------------------|:--------------------------|:-----------------|
| **Clareza**        | Alta (problemas naturais) | Média            |
| **Performance**    | Pode ser menor            | Geralmente maior |
| **Uso de memória** | Alto (pilha)              | Baixo            |

## 🧠 4. Ponteiros — Conceito Fundamental

### 🔹 Definição

Um ponteiro é uma variável que armazena o endereço de memória de outra variável.

👉 **Em vez de guardar o valor, ele guarda onde o valor está.**

### 🔹 Representação Conceitual

```
    inteiro x = 10;
    ponteiro p = <endereço de> x;
```

### 🔹 Interpretação

* `x` → valor = 10
* `p` → aponta para `x`

## 🔗 5. Ponteiros e Passagem por Referência

A passagem por referência é implementada usando ponteiros.

### 🔹 Exemplo Conceitual

```PEQUI
    void alterarValor(ref x){
        x = x + 5;
    }
```

👉 **Internamente:** `x` é um ponteiro para a variável original.

### 🔹 Analogia

* **Valor** → cópia do conteúdo
* **Referência** → acesso direto ao endereço

## 📦 6. Arrays são Ponteiros

### 🔹 Conceito

Em linguagens como C: O nome de um array representa o endereço do primeiro elemento.

### 🔹 Exemplo

```PEQUI
    inteiro vetor[3] = {1, 2, 3};
```

👉 `vetor` aponta para o primeiro elemento (`vetor[0]`)

### 🔹 Uso em Funções

```
    void imprimirVetor(v){
        escreva(v[0], v[1], v[2])]
    }
```

👉 O vetor é passado por referência (ponteiro).

### 🔹 Consequência

Alterar o vetor dentro da função → altera o original.

## 🔤 7. Strings são Ponteiros

### 🔹 Conceito

Strings são arrays de caracteres, logo também são ponteiros.

### 🔹 Exemplo

```PEQUI
    char nome[] = "Ana"
```

👉 **Internamente:** `'A' 'n' 'a' '\0'`

### 🔹 Uso em Funções

```PEQUI
    void alterarNome(nome){
        nome[0] = 'M';
    }
```

👉 Modifica diretamente a string original.

## ⚠️ 8. Cuidados com Ponteiros

* Acesso à memória inválida;
* Modificações indesejadas;
* Dificuldade de depuração;
* Necessidade de controle rigoroso.

## 🧪 9. Exemplo Integrado

```PEQUI
    inteiro fatorial(n){
        se n = 0 
            retorne 1;
        senão
            retorne n * fatorial(n - 1);
    }
    
    void dobrarVetor(v){
        v[0] = v[0] * 2;
        v[1] = v[1] * 2;
    }
    
    algoritmo principal{
        inteiro resultado;
        inteiro vetor[2] = {2, 3};
    
        resultado = fatorial(4);
        escreva(resultado);
    
        dobrarVetor(vetor);
        escreva(vetor[0], vetor[1]);
    }
```

## ⚙️ 10. Boas Práticas

* Sempre definir caso base em recursão;
* Evitar recursão profunda sem necessidade;
* Usar ponteiros com cuidado;
* Documentar funções que alteram dados externos;
* Testar funções com dados simples antes de escalar.

## 📝 11. Lista de Exercícios

### 🔹 Nível Básico

1. O que é recursividade?
2. O que é caso base?
3. O que é um ponteiro?
4. Por que arrays são considerados ponteiros?

### 🔹 Nível Intermediário

5. Escreva uma função recursiva para calcular a soma de 1 até n.
6. Explique a diferença entre passagem por valor e por referência usando ponteiros.
7. O que acontece ao alterar um array dentro de uma função?
8. Explique por que strings são ponteiros.

### 🔹 Nível Avançado

9. Implemente uma função recursiva para calcular potência (base^expoente).
10. Desenvolva um algoritmo que:
    * Receba um vetor;
    * Use ponteiros para modificar seus valores;
    * Exiba o resultado antes e depois da modificação.

## 📌 Encerramento

A recursividade é uma ferramenta poderosa para resolução de problemas estruturados, enquanto os ponteiros fornecem controle direto sobre a memória.

A combinação desses conceitos permite desenvolver soluções eficientes e flexíveis, sendo fundamentais para programação em baixo nível e para compreensão profunda do funcionamento dos sistemas computacionais.
