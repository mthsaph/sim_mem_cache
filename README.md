# 📘 Simulador de Memória Cache — README

## 🧩 Visão Geral

Este projeto implementa um **simulador educacional de memória cache**, permitindo visualizar o funcionamento de:

* Memória Principal (MP)
* Memória Cache com mapeamento por conjunto
* Cálculo de **hits**, **misses** e **substituições (LFU)**
* Acessos individuais ou sequenciais a endereços
* Estatísticas completas de desempenho

O objetivo principal é ajudar estudantes de Arquitetura de Computadores a entender memória cache na prática.

---

## 📁 Estrutura do Projeto

O arquivo principal é:

```
arquitetura_trab_cache.py
```

Ele contém:

* Funções de conversão (binário ↔ decimal)
* Geração da MP e Cache
* Leitura de arquivos externos
* Simulação de acessos
* Menu interativo via terminal

---

## 🧠 Como Funciona

### 🔹 1. **Memória Principal (MP)**

Gerada como uma matriz onde cada posição representa:

* Endereço binário
* Palavra de dados pseudoaleatória

A MP é configurada a partir de arquivo externo contendo:

```
256KB
4
32KB
4
```

Onde:

1. Tamanho da MP
2. Tamanho do bloco da MP
3. Tamanho da cache
4. Tamanho do bloco da cache

---

### 🔹 2. **Memória Cache**

A cache é gerada com:

* Número de blocos computed automaticamente
* Linhas internas contendo:

```json
{"Add": "", "Freq": 0}
```

A política de substituição usada é **LFU (Least Frequently Used)**.

---

### 🔹 3. **Simulação HIT/MISS**

Para cada endereço:

1. Ajusta o tamanho do endereço
2. Calcula o bloco da MP
3. Mapeia para o bloco correspondente da cache
4. Verifica:

   * **HIT** → endereço já está lá
   * **MISS** → linha vazia
   * **SUBSTITUIÇÃO** → se bloco cheio → remove o menos usado

O programa imprime informações detalhadas durante a simulação.

---

### 🔹 4. **Estatísticas**

Ao finalizar a execução:

* Hit rate (%)
* Miss rate (%)
* Total de substituições realizadas

---

## 🏁 Como Executar

### **Requisitos**

* Python 3.x

### **Execução**

No terminal:

```bash
python arquitetura_trab_cache.py
```

O menu principal será exibido:

```
1 - Ler arquivo de informações
2 - Informar endereço de acesso
3 - Ler arquivo de sequência de endereços
4 - Imprimir MP
5 - Imprimir Cache
6 - Informações do programa
0 - Sair
```

---

## 📄 Formato dos arquivos de entrada

### 🔹 Arquivo de informações (`info.txt`)

Cada linha contém um valor:

```
256KB      ← tamanho da MP
4          ← tamanho do bloco da MP
32KB       ← tamanho da cache
4          ← tamanho do bloco da cache
```

Unidades suportadas:

* `K` → 2¹⁰ bits
* `B` → 8 bits
* `b` → 1 bit

---

### 🔹 Arquivo de endereços (`enderecos.txt`)

Os endereços devem estar em uma única linha:

```
0101, 1010, 1111, 0001
```

Separados por: **", " (vírgula + espaço)**

---

## 📦 Funções Principais

### 🔧 Conversão

* `dec_to_bin()`
* `bin_to_dec()`
* `size_to_bits()`

### 🏗️ Geração

* `gen_MP()` → memória principal
* `gen_cache()` → cache

### 📥 Entrada

* `read_info()`
* `read_adds()`

### ⚙️ Execução

* `hit_or_miss()` → Simulação completa
* `print_menu()` → menu interativo

---

## 🧪 Exemplo de Uso

Após carregar o arquivo de informações, você pode:

### ✔ Inserir endereço manualmente:

```
Digite o endereço de acesso (em binário): 00010110
```

### ✔ Ou ler uma sequência:

```
Digite o nome do arquivo de sequência de endereços: enderecos.txt
```

---

## 📊 Resultados Finais

Ao escolher **0 - Sair**, será exibido:

```
Cache hit rate: 37.50%
Cache miss rate: 62.50%
Cache substituições: 4
```

---
