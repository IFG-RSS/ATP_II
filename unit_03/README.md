# 📘 Unidade 3 — Modularização: Funções, Procedimentos e Parâmetros

## 🎯 1. Objetivos da Aula
- Compreender o conceito de funções e procedimentos;
- Diferenciar funções de procedimentos;
- Entender o papel dos parâmetros de entrada;
- Compreender o retorno de dados;
- Aplicar modularização com passagem de dados entre módulos;
- Desenvolver algoritmos mais organizados e reutilizáveis.

## 🧠 2. Revisão: Modularização
> A modularização consiste em dividir um problema em partes menores chamadas módulos, cada uma responsável por uma tarefa específica.

👉 Na prática, esses módulos são implementados como:
- Funções
- Procedimentos

## ⚙️ 3. Procedimentos

### 🔹 Definição
> Um procedimento é um bloco de código que executa uma tarefa específica sem retornar valor.

### 🔹 Características
- Pode receber dados (parâmetros);
- Executa ações;
- Não retorna resultado diretamente;
- Pode produzir efeitos (ex: exibir na tela, alterar variáveis).

### 🔹 Exemplo
```PEQUI
   void exibirMensagem(){
      escreva("Bem-vindo ao sistema!");
}
```
### 🔹 Procedimento com Parâmetro
```PEQUI
   void exibirNome(string nome){
      escreva("Olá, ", nome);
   } 
```

## 🔁 4. Funções

### 🔹 Definição
Uma função é um módulo que:
- Recebe dados (opcional);
- Processa informações;
- Retorna um valor.

### 🔹 Características
- Sempre possui tipo de retorno;
- Pode ou não receber parâmetros;
- Deve retornar um valor compatível com o seu tipo.

### 🔹 Exemplo
```PEQUI
   inteiro somar(a, b){
      retorne a + b; 
   }
```

### 🔹 Uso da Função
```PEQUI
   ...
   inteiro resultado;
   resultado = somar(5, 3);
   escreva(resultado);
   ...
``` 

## 🔍 5. Diferença entre Função e Procedimento
| Característica    | Função              | Procedimento  |
|-------------------|---------------------|---------------|
| Retorno de valor  | Sim                 | Não           |
| Uso em expressões | Sim                 | Não           |
| Objetivo          | Calcular e retornar | Executar ação |

## 🔗 6. Parâmetros de Entrada

### 🔹 Definição
> Parâmetros são valores passados para funções ou procedimentos para serem utilizados no processamento.

### 🔹 Exemplo
```PEQUI
   real calcularMedia(n1, n2){
      retorne (n1 + n2) / 2;
   }
```

### 🔹 Tipos de Parâmetros

#### 📥 Por Valor
- Uma cópia do valor é passada;
- Alterações dentro da função não afetam a variável original.

#### 🔄 Por Referência (conceitual)
- A variável original é manipulada;
- Alterações afetam diretamente o valor externo.

### 🔹 Exemplo Conceitual
```PEQUI
   void incrementar(x){
      x ← x + 1;
   }
``` 
👉 Se for por valor → variável original não muda  
👉 Se for por referência → variável original é alterada

## 📤 7. Retorno de Dados

### 🔹 Definição
> O retorno é o valor produzido por uma função após o processamento.

### 🔹 Exemplo
```PEQUI
   inteiro quadrado(numero){
      retorne numero * numero;
   }
```

### 🔹 Uso Encadeado
Funções podem ser combinadas:
```PEQUI
   ...
   resultado = quadrado(somar(2, 3));
   ...
``` 

## 🧪 8. Exemplo Completo Modular
```PEQUI
   real calcularMedia(n1, n2){
      retorne (n1 + n2) / 2;
   }
   void verificarAprovacao(media){
      se (media >= 6) {
         escreva("Aprovado");
      } 
      senão{ 
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
- Evite dependências desnecessárias (baixo acoplamento).

## 10. Conteúdo adicional (Coesão e Acoplamento)
### 📌 Definição

> Alta coesão significa que um módulo (função, procedimento, classe) possui uma única responsabilidade bem definida e que todas as suas partes estão fortemente relacionadas entre si.

👉 Em termos práticos:
> Um módulo coeso faz uma coisa só — e faz bem-feito.

#### 🧠 Intuição

> Se você consegue descrever um módulo com uma única frase simples, ele provavelmente tem alta coesão.

✔ Exemplo:

* calcularMedia() → calcula média
* validarCPF() → valida CPF

❌ Não coeso:

* processarSistema() → faz muitas coisas diferentes

#### 🔍 Exemplos Comparativos

❌ Baixa Coesão (ruim)

```PEQUI
   void processarAluno(aluno){
      calcularMedia(aluno);
      imprimirRelatorio(aluno);
      salvarNoBanco(aluno);
      enviarEmail(aluno);
   }
```
#### 📌 Problemas:

* Múltiplas responsabilidades;
* Difícil manutenção;
* Baixa reutilização;
* Alto acoplamento implícito.

✅ Alta Coesão (bom)
```PEQUI
    real calcularMedia(n1, n2){
       retorne (n1 + n2) / 2;
    }
    void imprimirRelatorio(aluno){
       escreva(aluno.nome, aluno.media);
    }
```

#### 📌 Vantagens:

* Cada módulo tem uma função clara;
* Fácil de entender;
* Fácil de testar;
* Pode ser reutilizado em outros contextos.

#### ⚙️ Relação com Modularização

> Alta coesão é um dos pilares da boa modularização:

* Alta coesão → módulos bem definidos
* Baixo acoplamento → módulos independentes

👉 Juntos, garantem código de qualidade.

#### 📊 Benefícios da Alta Coesão

* ✔ Melhor legibilidade
* ✔ Facilidade de manutenção
* ✔ Reutilização de código
* ✔ Testes mais simples
* ✔ Redução de erros

#### ⚠️ Sinais de Baixa Coesão

* Funções muito longas;
* Muitos parâmetros sem relação clara;
* Nome genérico (ex: processar, executarTudo);
* Mistura de responsabilidades (cálculo + I/O + persistência).

#### 🧩 Regra Prática (Muito Importante)

👉 Se uma função está fazendo mais de uma coisa, divida-a.

#### 📌 Conclusão

> Alta coesão é um critério fundamental de qualidade de software.
> Ela garante que cada módulo seja simples, focado e reutilizável, facilitando tanto o desenvolvimento quanto a evolução do sistema.

## 📝 11. Lista de Exercícios

### 🔹 Nível Básico
- Defina função e procedimento.
- Qual a principal diferença entre função e procedimento?
- O que são parâmetros?
- O que é retorno de uma função?

### 🔹 Nível Intermediário
- Escreva uma função que receba dois números e retorne o maior.
- Crie um procedimento que receba um nome e exiba uma mensagem personalizada.
- Explique a diferença entre passagem por valor e por referência.
- Dado um algoritmo, identifique se um trecho deve ser função ou procedimento.

### 🔹 Nível Avançado
- Desenvolva um algoritmo modular para:
    - Ler três notas;
    - Calcular a média;
    - Informar aprovação.  
      *(Use função e procedimento)*
- Explique como funções contribuem para reutilização de código em sistemas maiores.

## 📌 Encerramento
> A utilização de funções e procedimentos é a base da modularização em programação. Esses mecanismos permitem construir soluções mais organizadas, reutilizáveis e fáceis de manter.

> O domínio de parâmetros e retorno de dados é essencial para garantir a comunicação eficiente entre módulos, sendo um passo fundamental para o desenvolvimento de sistemas mais complexos e profissionais.

