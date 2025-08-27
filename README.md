# Projeto de Busca e Ordenação: KMP, Aho-Corasick e Verificação Ortográfica

Este repositório contém a implementação de algoritmos de busca de padrões e uma ferramenta de verificação ortográfica, desenvolvidos como parte do segundo projeto da disciplina de Busca e Ordenação. O trabalho foi realizado por Gabriel Davi e Giordani Andre.

## 📜 Sobre o Projeto

O objetivo principal foi implementar, analisar e comparar diferentes algoritmos para encontrar padrões em textos. As funcionalidades escolhidas foram:
* **Busca com KMP e Wildcard**: Implementação do algoritmo Knuth-Morris-Pratt (KMP) com a adição de um caractere curinga (`*`) para buscas mais flexíveis.
* **Busca de Múltiplas Palavras**: Utilização do algoritmo Aho-Corasick para buscar simultaneamente vários padrões em um texto de forma eficiente.
* **Verificação Ortográfica**: Uso de uma árvore Trie para carregar um dicionário e identificar palavras em um texto que não constam nele.

## ✨ Funcionalidades

### 1. KMP com Suporte a Wildcard (`*`)
O algoritmo KMP foi modificado para permitir o uso do caractere `*` como um curinga, que corresponde a qualquer caractere no texto.

* **Arquivo**: `kmp.cpp`
* **Destaque**: A busca é otimizada pelo uso da tabela LPS (*Longest Prefix Suffix*), que evita retrocessos desnecessários no texto, mesmo em falhas de correspondência.

### 2. Aho-Corasick para Múltiplas Buscas
Para a busca de múltiplas palavras de uma só vez, foi implementado o algoritmo Aho-Corasick.

* **Arquivos**: `aho_corasick.h`, `aho_corasick.cpp`
* **Estrutura**: Utiliza uma árvore Trie para armazenar os padrões e "ponteiros de falha" para otimizar a busca, permitindo que o texto seja percorrido uma única vez. A construção dos ponteiros de falha é feita com uma busca em largura (BFS).

### 3. Verificação Ortográfica com Trie
Uma árvore Trie é usada para armazenar eficientemente as palavras de um dicionário (`pt_BR.dic`) e depois verificar se as palavras de um arquivo de texto existem nesse dicionário.

* **Arquivos**: `trie.h`, `trie.cpp`
* **Suporte a UTF-8**: O projeto lida corretamente com caracteres acentuados e especiais graças ao uso da biblioteca `utf8.h`. As palavras são convertidas para minúsculas para garantir a correspondência, independentemente da capitalização.

## 📊 Análise de Desempenho

Foi realizada uma análise comparativa de desempenho entre os algoritmos **Busca Ingênua**, **KMP** e **Aho-Corasick**. O tempo de execução de cada busca foi medido utilizando `chrono::high_resolution_clock`.

Os resultados mostram que, para múltiplas buscas em textos maiores, o **Aho-Corasick** tende a ser o mais eficiente, apesar de seu maior consumo de memória e tempo de pré-processamento.

O programa apresentará um menu interativo para:
1.  Ler novas palavras para busca.
2.  Executar a busca com o algoritmo Ingênuo.
3.  Executar a busca com KMP.
4.  Executar a busca com Aho-Corasick.
5.  Realizar a verificação ortográfica do `texto.txt`.
