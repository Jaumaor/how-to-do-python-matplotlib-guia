# 🐍📊 How-To-Do: Visualização de Dados com Python e Matplotlib

-----

## 📖 Sobre o Projeto

Este repositório é um guia prático para desenvolvedores que desejam iniciar na visualização de dados. O objetivo é demonstrar como criar gráficos simples e informativos usando a biblioteca **Matplotlib** em Python, a partir de um conjunto de dados real, para identificar padrões e tendências.

-----

## 🎨 O que é Matplotlib?

O **Matplotlib** é a biblioteca fundamental para a criação de gráficos e visualizações em Python. É considerado o "canivete suíço" da plotagem, permitindo um controle detalhado sobre cada aspecto de uma figura.

👉 Imagine ter uma caixa de ferramentas completa para desenhar, com lápis de todas as cores, réguas, compassos e papéis milimetrados. Isso é o Matplotlib para um cientista de dados.

### 🌟 Principais características:

  - 🎯 **Poderoso:** Capaz de criar desde os gráficos mais simples (barras, linhas, pizza) até visualizações complexas.
  - ⚙️ **Customizável:** Permite controlar cada detalhe de um gráfico: cores, fontes, títulos, legendas, eixos, etc.
  - 🤝 **Integrado:** Funciona perfeitamente com as estruturas de dados nativas do Python, como listas e dicionários.
  - 📚 **Comunidade:** Por ser uma das bibliotecas mais antigas e populares, possui uma vasta documentação e incontáveis exemplos online.

-----

## 🔬 Nosso Estudo de Caso: Análise de Dados de Diabetes

Para este guia, vamos utilizar uma pequena amostra de dados do dataset **Pima Indians Diabetes Database**. Para focar exclusivamente no Matplotlib, vamos definir esses dados diretamente em nosso código Python usando listas, baseados nos exemplos realistas que vimos anteriormente.

-----

## 🚀 Passo a Passo: Da Análise à Visualização

### 1\. Preparando o Ambiente

Primeiro, vamos instalar a única biblioteca que precisaremos. Com seu ambiente virtual (`venv`) ativado, execute no terminal:

```bash
pip install matplotlib
```

### 2\. Criando Gráficos Simples com Matplotlib

Agora, vamos direto para a criação das visualizações. Cada exemplo abaixo é um script completo e autônomo.

#### **A. Gráfico de Linhas - Analisando Tendências**

**Pergunta:** Em nossa amostra, existe uma tendência na predisposição genética ao diabetes conforme a idade das pacientes aumenta?

```python
import matplotlib.pyplot as plt

# --- Dados ---
idades = [21, 26, 30, 31, 32, 33, 50, 51, 53, 59]
pedigree = [0.167, 0.248, 0.201, 0.351, 0.672, 2.288, 0.627, 0.587, 0.158, 0.398]

# --- Visualização ---
plt.figure(figsize=(10, 6))

# Adicionamos o parâmetro 'label' para identificar esta linha de dados.
plt.plot(idades, pedigree, marker='o', linestyle='--', color='purple', label='Predisposição Genética')

plt.title('Tendência da Predisposição Genética por Idade (Amostra)', fontsize=16)
plt.xlabel('Idade (anos)', fontsize=12)
plt.ylabel('Diabetes Pedigree Function', fontsize=12)
plt.grid(True, alpha=0.5)

# O comando plt.legend() lê o 'label' que definimos no plt.plot() e exibe a legenda.
plt.legend()

plt.savefig('grafico_de_linhas_idade_pedigree.png')
plt.show()
```

#### **B. Gráfico de Pizza - Visualizando Proporções**

**Pergunta:** Qual a proporção de pacientes com e sem diabetes em nossa amostra?

```python
import matplotlib.pyplot as plt

# --- Dados ---
labels = ['Sem Diabetes', 'Com Diabetes']
sizes = [12, 8]
colors = ['#66b3ff', '#ff9999']
explode = (0.05, 0)

# --- Visualização ---
plt.figure(figsize=(8, 8))

# O gráfico de pizza já usa o parâmetro 'labels' para criar as legendas diretamente nas fatias.
# Uma legenda separada com plt.legend() seria redundante, mas poderia ser adicionada se necessário.
plt.pie(sizes, explode=explode, labels=labels, colors=colors,
        autopct='%1.1f%%', shadow=True, startangle=140)

plt.title('Proporção de Diagnósticos de Diabetes (Amostra)', fontsize=16)
plt.axis('equal')

plt.savefig('grafico_de_pizza_diagnostico.png')
plt.show()
```

#### **C. Gráfico de Barras - Comparando Categorias**

**Pergunta:** Qual a média de glicose para pacientes com e sem diabetes em nossa amostra?

```python
import matplotlib.pyplot as plt

# --- Dados ---
categorias = ['Sem Diabetes', 'Com Diabetes']
media_glicose = [99.7, 155.0]

# --- Visualização ---
plt.figure(figsize=(8, 6))

# Adicionamos o parâmetro 'label' a cada barra ou conjunto de barras.
plt.bar(categorias, media_glicose, color=['skyblue', 'salmon'], edgecolor='black', label='Média de Glicose')

plt.title('Média de Glicose por Diagnóstico (Amostra)', fontsize=16)
plt.xlabel('Diagnóstico', fontsize=12)
plt.ylabel('Nível Médio de Glicose', fontsize=12)
plt.grid(axis='y', linestyle='--', alpha=0.7)

# O comando plt.legend() exibe a legenda que definimos no plt.bar().
plt.legend()

plt.savefig('barras_media_glicose.png')
plt.show()
```

-----

### ✨ Personalizando seus Gráficos (Estilos e Cores)

Uma das maiores vantagens do Matplotlib é a sua capacidade de personalização.

#### Estilos Prontos (`plt.style.use()`)

A biblioteca já vem com vários **estilos visuais prontos** que mudam completamente a aparência de todos os seus gráficos com uma única linha de código. É como aplicar um "tema". Basta adicionar `plt.style.use('nome_do_estilo')` no início do seu script.

**Exemplo:**

```python
import matplotlib.pyplot as plt

# Esta linha muda o visual de TODOS os gráficos feitos depois dela.
plt.style.use('ggplot')

# (Resto do seu código de gráfico de barras aqui...)
```

> **💡 Outros estilos populares para testar:** `'seaborn-v0_8-pastel'`, `'fivethirtyeight'`, `'dark_background'`.

-----

### 🛠️ Principais Métodos do Matplotlib: Um Guia Rápido

Para fixar o conhecimento e mostrar o poder da biblioteca, aqui está uma lista de alguns dos métodos mais utilizados e o que eles fazem.

#### **Configuração da Figura e Eixos**

  - `plt.figure(figsize=(w, h))`: Cria a "tela" em branco para o seu gráfico, com uma largura (`w`) e altura (`h`) definidas.
  - `plt.subplots(rows, cols)`: Cria uma figura com múltiplos sub-gráficos organizados em `rows` linhas e `cols` colunas. É extremamente poderoso para criar dashboards.
  - `plt.title('Texto')`: Adiciona um título principal ao gráfico.
  - `plt.xlabel('Texto')`: Adiciona um rótulo ao eixo X (horizontal).
  - `plt.ylabel('Texto')`: Adiciona um rótulo ao eixo Y (vertical).
  - `plt.xticks()` e `plt.yticks()`: Permitem customizar as marcações e os rótulos nos eixos X e Y.

#### **Comandos de Plotagem (Tipos de Gráfico)**

  - `plt.plot(x, y)`: O comando principal para **gráficos de linhas**.
  - `plt.scatter(x, y)`: Cria **gráficos de dispersão**, mostrando a relação entre duas variáveis.
  - `plt.bar(categorias, valores)`: Cria **gráficos de barras** verticais.
  - `plt.barh(categorias, valores)`: Cria **gráficos de barras** horizontais.
  - `plt.hist(dados)`: Cria um **histograma** para visualizar a distribuição de uma única variável.
  - `plt.pie(valores)`: Cria um **gráfico de pizza** para mostrar proporções.
  - `plt.boxplot(dados)`: Cria um **boxplot**, ótimo para visualizar a distribuição de dados e identificar outliers.

#### **Customização e Finalização**

  - `plt.grid(True)`: Adiciona uma grade de fundo ao gráfico.
  - `plt.legend()`: Exibe a legenda do gráfico (requer que você tenha definido `label` nos seus comandos de plotagem).
  - `plt.text(x, y, 'Texto')`: Adiciona um texto qualquer em uma coordenada `(x, y)` específica do gráfico.
  - `plt.savefig('nome_arquivo.png')`: Salva o gráfico gerado como um arquivo de imagem.
  - `plt.show()`: Exibe a janela com o gráfico finalizado. É um comando essencial no final de cada script.
  - `plt.close()`: Fecha a janela do gráfico, útil para liberar memória em scripts que geram muitas figuras.
