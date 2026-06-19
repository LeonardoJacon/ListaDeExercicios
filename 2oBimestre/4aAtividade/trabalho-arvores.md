# Atividade Avaliativa 4 – Estruturas Avançadas de Árvores

## Estruturas de Dados – 2º Bimestre

---

# Parte 1 – Tipos de Árvores

## Árvore AVL

### Conceito

A árvore AVL é uma Árvore Binária de Busca (BST) autobalanceada, criada por Georgy Adelson-Velsky e Evgenii Landis em 1962. Seu principal objetivo é manter a altura da árvore equilibrada para garantir operações eficientes.

Cada nó possui um **fator de balanceamento**, calculado pela diferença entre a altura da subárvore esquerda e da direita.

O fator de balanceamento deve ser:

- -1
- 0
- +1

Caso esse valor seja diferente, a árvore realiza rotações para restaurar o equilíbrio.

### Características

- É uma BST.
- Mantém balanceamento automático.
- Utiliza rotações simples e duplas.
- Busca muito eficiente.

### Vantagens

- Busca sempre em O(log n).
- Altura mínima da árvore.
- Excelente para aplicações com muitas consultas.

### Desvantagens

- Inserções e remoções exigem rotações.
- Implementação relativamente complexa.
- Maior custo de manutenção do balanceamento.

### Exemplo ilustrado

Antes do balanceamento:

```text
      30
     /
   20
  /
10
```

Após rotação à direita:

```text
     20
    /  \
  10   30
```

---

# Árvore Rubro-Negra

## Conceito

A árvore Rubro-Negra é uma BST autobalanceada que utiliza cores (vermelho e preto) para manter o equilíbrio de maneira aproximada.

É bastante utilizada em bibliotecas e sistemas operacionais por exigir menos rotações que a AVL.

## Regras de coloração

1. Todo nó é vermelho ou preto.
2. A raiz sempre é preta.
3. Todos os nós nulos são considerados pretos.
4. Um nó vermelho nunca pode ter filho vermelho.
5. Todo caminho da raiz até uma folha possui a mesma quantidade de nós pretos.

## Vantagens

- Busca em O(log n).
- Menos rotações durante inserções.
- Muito utilizada em aplicações reais.

## Desvantagens

- Implementação complexa.
- Balanceamento menos rigoroso que a AVL.

## Exemplo ilustrado

```text
        20(P)
       /     \
   10(V)    30(V)
```

(P = Preto)

(V = Vermelho)

---

# Árvore N-ária

## Conceito

Uma árvore N-ária é aquela em que cada nó pode possuir vários filhos, diferente da árvore binária que permite apenas dois.

## Diferenças em relação às árvores binárias

| Árvore Binária | Árvore N-ária |
|---------------|---------------|
| Até 2 filhos | Até N filhos |
| Estrutura simples | Estrutura mais flexível |
| Muito usada em busca | Muito usada em hierarquias |

## Vantagens

- Representa melhor estruturas hierárquicas.
- Menor profundidade.
- Organização mais natural.

## Desvantagens

- Implementação mais complexa.
- Algumas operações são mais difíceis.

## Exemplo ilustrado

```text
          A
      /   |   \
     B    C    D
   / | \
  E  F  G
```

## Aplicações práticas

- Sistemas de arquivos
- XML
- HTML
- Menus
- Organogramas
- Árvores genealógicas

---

# Parte 2 – Operações em Árvores

## Rotação Simples à Direita

### Objetivo

Corrigir o desbalanceamento quando existe excesso de nós à esquerda.

### Situação

Caso LL (Left-Left).

### Antes

```text
      30
     /
   20
  /
10
```

### Depois

```text
     20
    /  \
  10   30
```

---

# Rotação Simples à Esquerda

## Objetivo

Corrigir o excesso de nós à direita.

## Situação

Caso RR (Right-Right).

### Antes

```text
10
  \
   20
     \
      30
```

### Depois

```text
     20
    /  \
  10   30
```

---

# Rotação Dupla

## Esquerda-Direita (LR)

Ocorre quando o filho esquerdo está desbalanceado para a direita.

Antes

```text
      30
     /
   10
      \
      20
```

Depois

```text
      20
     /  \
   10   30
```

---

## Direita-Esquerda (RL)

Ocorre quando o filho direito está desbalanceado para a esquerda.

Antes

```text
10
   \
    30
   /
 20
```

Depois

```text
     20
    /  \
  10   30
```

---

# Inversão (Espelhamento)

## Conceito

Consiste em trocar todos os filhos esquerdos pelos direitos, produzindo a imagem espelhada da árvore.

## Aplicação

- Algoritmos
- Processamento de árvores
- Computação gráfica
- Exercícios de estruturas de dados

### Antes

```text
      A
     / \
    B   C
```

### Depois

```text
      A
     / \
    C   B
```

---

# Parte 3 – Aplicação Prática

## Banco de Dados

Uma das aplicações mais comuns das árvores balanceadas é em bancos de dados.

A estrutura mais indicada é a **Árvore Rubro-Negra**.

### Justificativa

Os bancos de dados realizam milhares de operações de inserção, remoção e busca constantemente.

A árvore Rubro-Negra mantém o balanceamento com menor quantidade de rotações quando comparada à AVL, oferecendo excelente desempenho para operações frequentes de atualização.

Por esse motivo, diversas bibliotecas e estruturas internas utilizam árvores Rubro-Negras para armazenar índices e coleções ordenadas.

---

# Parte 4 – Comparação entre Estruturas

| Estrutura | Nº Máximo de Filhos | Balanceamento | Complexidade de Busca | Complexidade de Inserção | Vantagem Principal | Desvantagem Principal | Exemplo de Aplicação |
|------------|--------------------|---------------|----------------------|--------------------------|-------------------|----------------------|---------------------|
| BST | 2 | Não possui balanceamento automático | O(log n) melhor caso / O(n) pior caso | O(log n) melhor caso / O(n) pior caso | Simples de implementar | Pode ficar totalmente desbalanceada | Árvores de busca básicas |
| AVL | 2 | Sim, através de rotações | O(log n) | O(log n) | Busca extremamente eficiente | Mais rotações durante inserções e remoções | Índices de banco de dados e sistemas de busca |
| Rubro-Negra | 2 | Sim, usando cores e rotações | O(log n) | O(log n) | Menor custo de manutenção | Implementação mais difícil | Bibliotecas da linguagem Java, C++ STL e sistemas operacionais |
| N-ária | N | Depende da implementação | O(log n) em versões balanceadas | O(log n) em versões balanceadas | Representa hierarquias naturalmente | Estrutura mais complexa | Sistemas de arquivos, XML e HTML |

---

# Explicação da Tabela

## Número Máximo de Filhos

Define quantos filhos cada nó pode possuir.

- BST, AVL e Rubro-Negra possuem no máximo dois filhos.
- Árvores N-árias podem possuir vários filhos.

## Balanceamento

Indica se a árvore mantém sua altura automaticamente.

- BST não possui balanceamento.
- AVL utiliza fator de balanceamento e rotações.
- Rubro-Negra utiliza regras de coloração e rotações.
- Árvores N-árias dependem da implementação.

## Complexidade de Busca

Quanto menor a altura da árvore, mais rápida será a busca.

Árvores balanceadas mantêm complexidade O(log n).

## Complexidade de Inserção

AVL e Rubro-Negra realizam rotações para manter o equilíbrio, garantindo O(log n).

Na BST, pode chegar a O(n) quando desbalanceada.

## Vantagem Principal

Cada estrutura possui um objetivo específico:

- BST → simplicidade.
- AVL → buscas extremamente rápidas.
- Rubro-Negra → melhor desempenho em inserções.
- N-ária → representação eficiente de hierarquias.

## Desvantagem Principal

Quanto maior o controle do balanceamento, maior a complexidade da implementação.

## Exemplo de Aplicação

Cada estrutura é utilizada conforme sua finalidade:

- BST → estudos e algoritmos simples.
- AVL → sistemas com muitas consultas.
- Rubro-Negra → bibliotecas e sistemas internos.
- N-ária → sistemas de arquivos, XML, HTML e menus.

---

# Conclusão

As árvores balanceadas foram desenvolvidas para resolver problemas de desempenho encontrados nas Árvores Binárias de Busca tradicionais.

A árvore AVL oferece buscas extremamente rápidas devido ao seu balanceamento rigoroso. Já a árvore Rubro-Negra realiza menos rotações, tornando inserções e remoções mais eficientes. As árvores N-árias são ideais para representar estruturas hierárquicas com múltiplos filhos, como sistemas de arquivos e documentos XML.

A escolha da estrutura depende da aplicação e das operações realizadas com maior frequência.