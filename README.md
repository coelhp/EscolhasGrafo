# Análise de Grafos e Determinação do Menor Caminho em R

Implementação em R para modelagem e análise de grafos ponderados, com aplicação na determinação do caminho de menor custo entre dois vértices utilizando a biblioteca `igraph`.

Projeto acadêmico desenvolvido na disciplina **Informática Aplicada à Engenharia**, do curso de Engenharia de Controle e Automação.

---

## Sumário

* [1. Sobre o projeto](#1-sobre-o-projeto)
* [2. Objetivos](#2-objetivos)
* [3. Fundamentação teórica](#3-fundamentação-teórica)
* [4. Modelagem do problema](#4-modelagem-do-problema)
* [5. Metodologia](#5-metodologia)
* [6. Tecnologias utilizadas](#6-tecnologias-utilizadas)
* [7. Estrutura do repositório](#7-estrutura-do-repositório)
* [8. Instalação e execução](#8-instalação-e-execução)
* [9. Resultados](#9-resultados)
* [10. Limitações](#10-limitações)
* [11. Possíveis melhorias](#11-possíveis-melhorias)
* [12. Contexto acadêmico](#12-contexto-acadêmico)

---

## 1. Sobre o projeto

A teoria dos grafos permite representar problemas que envolvem conexões entre diferentes elementos. Suas aplicações incluem problemas de transporte, logística, redes de comunicação, planejamento de rotas e análise de sistemas interconectados.

Neste trabalho, é desenvolvido um programa em R para determinar o caminho de menor custo entre dois vértices de um grafo ponderado.

O problema consiste em encontrar uma rota entre o vértice de origem `0` e o vértice de destino `3`, considerando os pesos associados às conexões existentes no grafo.

Para isso, utiliza-se a biblioteca `igraph`, que disponibiliza funções para construção, análise e visualização de grafos, incluindo algoritmos para determinação de caminhos mínimos.

O resultado é apresentado graficamente, destacando os vértices e as arestas que compõem o caminho selecionado.

## 2. Objetivos

### 2.1. Objetivo geral

Desenvolver uma aplicação em R para representar um grafo ponderado e determinar o caminho de menor custo entre dois vértices, utilizando recursos da biblioteca `igraph`.

### 2.2. Objetivos específicos

* Representar um problema de conectividade por meio de um grafo.
* Definir os vértices e as arestas da estrutura.
* Associar pesos às conexões entre os vértices.
* Calcular a distância mínima entre uma origem e um destino.
* Identificar os vértices e as arestas pertencentes ao caminho encontrado.
* Apresentar graficamente a solução.
* Aplicar conceitos de teoria dos grafos e otimização em um problema computacional.

## 3. Fundamentação teórica

### 3.1. Teoria dos grafos

Um grafo é uma estrutura matemática utilizada para representar elementos e as relações existentes entre eles.

Formalmente:

$G=(V,E)$

Em que:

* \(V\) representa o conjunto de vértices;
* \(E\) representa o conjunto de arestas.

Neste trabalho, os vértices representam os pontos do problema, enquanto as arestas representam as conexões possíveis entre esses pontos.

### 3.2. Grafos ponderados

Um grafo ponderado possui valores associados às suas arestas. Esses valores podem representar distâncias, custos, tempos ou outras grandezas relevantes para o problema.

O peso de uma aresta \(e\) é representado por:

$w(e)$

O custo total de um caminho corresponde à soma dos pesos das arestas percorridas.

### 3.3. Problema do menor caminho

O problema do menor caminho consiste em encontrar uma sequência de arestas que conecte dois vértices com o menor custo acumulado possível.

Para uma origem \(s\) e um destino \(t\), busca-se:

$P^*=\underset{P:s\rightarrow t}{\arg\min}\sum_{e\in P}w(e)$

Neste projeto:

* **Origem:** vértice `0`.
* **Destino:** vértice `3`.
* **Critério de otimização:** minimizar a soma dos pesos das arestas percorridas.

O caminho com menor custo não precisa ser aquele que utiliza a menor quantidade de arestas. Uma rota com mais conexões pode apresentar custo total inferior ao de uma rota mais curta em número de segmentos.

## 4. Modelagem do problema

O grafo é definido no código por meio da função `graph()` da biblioteca `igraph`.

A estrutura possui sete vértices, identificados pelos rótulos `0`, `1`, `2`, `3`, `4`, `5` e `6`.

As conexões são representadas por onze arestas, cada uma associada a um peso.

O grafo é **não direcionado**, ou seja, as conexões podem ser percorridas nos dois sentidos. Os pesos representam os custos associados a cada conexão.

### 4.1. Definição dos vértices e das arestas

A estrutura de conexões inclui os seguintes pares de vértices:

| Origem | Destino | Peso |
| -----: | ------: | ---: |
|      0 |       1 |  5,0 |
|      0 |       2 |  3,1 |
|      0 |       5 |  5,2 |
|      1 |       2 |  4,9 |
|      1 |       6 |  5,2 |
|      2 |       4 |  6,0 |
|      2 |       5 |  3,2 |
|      2 |       6 |  3,0 |
|      4 |       5 |  4,7 |
|      4 |       3 |  5,5 |
|      3 |       6 |  4,8 |

Os valores correspondem aos pesos definidos no script `TrabalhoGrafo.R`.

### 4.2. Formulação do objetivo

O algoritmo procura uma rota entre os vértices `0` e `3` que minimize o custo acumulado.

A distância mínima é dada por:

$d(0,3)=\min_{P:0\rightarrow3}\sum_{e\in P}w(e)$

Essa formulação permite comparar diferentes rotas e identificar aquela que apresenta o menor valor total.

## 5. Metodologia

O programa é organizado em etapas que vão da construção do grafo à apresentação da solução.

### Etapa 1: Preparação do ambiente

A biblioteca `igraph` é carregada para disponibilizar as funções de construção, análise e visualização de grafos.

### Etapa 2: Construção do grafo

As conexões entre os vértices são declaradas no código por meio da função `graph()`.

Como o grafo é não direcionado, cada conexão pode ser percorrida em ambos os sentidos.

### Etapa 3: Definição dos pesos

Os pesos são atribuídos às arestas por meio do atributo `weight`.

Esses valores são utilizados para calcular o custo acumulado de cada rota.

### Etapa 4: Cálculo da distância mínima

A função `distances()` calcula a distância entre os vértices de origem e destino.

O resultado corresponde ao menor custo acumulado entre os pontos considerados.

### Etapa 5: Identificação do caminho

A função `shortest_paths()` identifica os vértices e as arestas que compõem o caminho selecionado.

Essa informação permite recuperar a sequência de conexões que conduz da origem ao destino.

### Etapa 6: Visualização da solução

O programa modifica as cores dos vértices e das arestas para destacar o caminho encontrado.

A representação gráfica facilita a interpretação do resultado e a comparação entre a rota selecionada e as demais conexões do grafo.

## 6. Tecnologias utilizadas

| Tecnologia                           | Finalidade                                                    |
| ------------------------------------ | ------------------------------------------------------------- |
| R                                    | Linguagem utilizada na implementação do algoritmo.            |
| `igraph`                             | Biblioteca para construção, análise e visualização de grafos. |
| RStudio ou outro ambiente compatível | Edição e execução do código R.                                |

## 7. Estrutura do repositório

```text
EscolhasGrafo/
├── README.md
└── TrabalhoGrafo.R
```

### Descrição dos arquivos

* **`README.md`:** documentação do projeto, da modelagem e dos procedimentos de execução.
* **`TrabalhoGrafo.R`:** implementação em R para construir o grafo, calcular o menor caminho e visualizar a solução.

## 8. Instalação e execução

### 8.1. Pré-requisitos

Para executar o projeto, é necessário ter:

* R instalado;
* acesso à internet durante a instalação inicial do pacote, caso ele ainda não esteja disponível;
* um editor ou ambiente compatível com a execução de scripts R.

O RStudio é uma opção de ambiente de desenvolvimento, mas não é obrigatório.

### 8.2. Obtenção do projeto

Clone o repositório:

```bash
git clone https://github.com/coelhp/EscolhasGrafo.git
```

Entre no diretório:

```bash
cd EscolhasGrafo
```

### 8.3. Instalação da biblioteca

No console do R, execute:

```r
install.packages("igraph")
```

Essa etapa precisa ser realizada somente quando o pacote ainda não estiver instalado no ambiente.

### 8.4. Execução

Abra o arquivo `TrabalhoGrafo.R` no ambiente R e execute o script.

Alternativamente, no console do R, a partir do diretório do projeto, utilize:

```r
source("TrabalhoGrafo.R")
```

O programa construirá o grafo, calculará o caminho mínimo entre os vértices `0` e `3` e apresentará a representação gráfica da solução.

![image](https://github.com/riquelmept/EscolhasGrafo/assets/100944831/07be69bd-b74c-4230-a519-8b4155e17eb2)

## 9. Resultados

A partir das conexões e dos pesos definidos no código, o caminho de menor custo entre os vértices `0` e `3` é:

$\boxed{0\rightarrow2\rightarrow6\rightarrow3}$

O custo acumulado é calculado pela soma dos pesos das três arestas:

$d(0,3)=w(0,2)+w(2,6)+w(6,3)$

Substituindo os valores:

$d(0,3)=3{,}1+3{,}0+4{,}8$

Portanto:

$\boxed{d(0,3)=10{,}9}$

### 9.1. Interpretação

A solução percorre os vértices `0`, `2`, `6` e `3`, utilizando três arestas.

O resultado minimiza a soma dos pesos entre as rotas possíveis no grafo definido.

A visualização gerada pelo programa destaca essa sequência, facilitando a identificação do caminho selecionado.

### 9.2. Registro gráfico

![image](https://github.com/riquelmept/EscolhasGrafo/assets/100944831/62f8e0e6-cdb2-44cf-9201-55ccfc282df1)

## 10. Limitações

O escopo do trabalho está restrito ao grafo definido no código.

Algumas considerações importantes:

* Os vértices e as arestas são especificados diretamente no script.
* Os pesos são definidos manualmente.
* O programa considera um único grafo e um par específico de origem e destino.
* O modelo é não direcionado, portanto as conexões podem ser percorridas em ambos os sentidos.
* A interpretação física dos pesos depende das informações do enunciado original.
* O resultado depende da estrutura de conexões e dos valores utilizados como pesos.

Essas limitações não comprometem o objetivo acadêmico do exercício, mas delimitam as condições em que a solução pode ser aplicada.

## 11. Possíveis melhorias

Como evolução do projeto, podem ser consideradas as seguintes funcionalidades:

* Permitir que o usuário informe os vértices de origem e destino.
* Ler as conexões e os pesos a partir de uma tabela ou arquivo externo.
* Comparar diferentes rotas e seus respectivos custos.
* Implementar uma interface para entrada dos dados.
* Melhorar a apresentação gráfica, incluindo uma legenda para o caminho mínimo.
* Validar automaticamente a distância calculada.
* Permitir a representação de grafos direcionados, quando aplicável.
* Adicionar testes para verificar os resultados em diferentes configurações de grafos.

Essas melhorias ampliariam a flexibilidade do programa e permitiriam explorar outras aplicações de algoritmos de caminhos mínimos.

## 12. Contexto acadêmico

**Disciplina:** Informática Aplicada à Engenharia
**Curso:** Engenharia de Controle e Automação
**Tema:** teoria dos grafos e determinação do menor caminho
**Linguagem:** R
**Biblioteca principal:** `igraph`

**Repositório:** [github.com/coelhp/EscolhasGrafo](https://github.com/coelhp/EscolhasGrafo)

Projeto desenvolvido para fins acadêmicos, com o objetivo de aplicar conceitos de teoria dos grafos por meio de uma implementação computacional.
