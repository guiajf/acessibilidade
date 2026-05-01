# 🍺 Análise de Acessibilidade com Osmnx e NetworkX

[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![OSMnx](https://img.shields.io/badge/OSMnx-2.0+-orange.svg)](https://osmnx.readthedocs.io/)

Este notebook realiza uma **análise completa de acessibilidade viária** entre 40 bares participantes do concurso *Comida di Buteco* em Juiz de Fora (MG), utilizando dados reais de rotas urbanas obtidos via **OpenStreetMap** e processados com bibliotecas Python de análise espacial e redes.

## 📌 Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Resultados Principais](#resultados-principais)
- [Como Executar](#como-executar)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Arquivos Gerados](#arquivos-gerados)
- [Visualizações](#visualizações)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Observações Técnicas](#observações-técnicas)
- [Limitações e Melhorias Futuras](#limitações-e-melhorias-futuras)
- [Licença](#licença)

## 🎯 Visão Geral

O projeto calcula e compara a acessibilidade entre **todos os 40 bares** do evento, gerando métricas como:

- ✅ Matriz de distâncias (tempo de viagem e distância geográfica)
- ✅ Estatísticas de acessibilidade por bar (média, mediana, máximo)
- ✅ Ranking dos bares mais e menos acessíveis
- ✅ Score integrado de acessibilidade (ponderação personalizada)
- ✅ Visualizações comparativas (gráficos, heatmap, mapa interativo)

## ⚙️ Funcionalidades

| Módulo | Descrição |
|--------|------------|
| **Matriz de Acessibilidade** | Cálculo de caminhos mais curtos entre todos os pares de bares (~780 pares) |
| **Estatísticas por Bar** | Tempo médio, distância média, cobertura da rede |
| **Score Integrado** | Combinação de tempo (50%), distância (30%) e cobertura (20%) |
| **Heatmap** | Visualização matricial dos tempos de viagem entre bares |
| **Mapa Interativo** | Mapa Folium com marcadores coloridos por nível de acessibilidade |

## 📊 Resultados Principais

### 🏆 Top 5 Bares Mais Acessíveis

| Ranking | Bar | Tempo Médio | Score Final |
|---------|-----|-------------|--------------|
| 1º | BAR BATATA D'MOLA | 4.6 min | 80.0/100 |
| 2º | BAR DO MARQUIM | 4.6 min | 79.6/100 |
| 3º | CAMINHO DA ROCA | 4.8 min | 78.2/100 |
| 4º | BAR DO ABILIO | 5.0 min | 77.4/100 |
| 5º | REZA FORTE | 5.0 min | 77.4/100 |

### 📉 Bottom 3 Bares Menos Acessíveis

| Ranking | Bar | Tempo Médio |
|---------|-----|-------------|
| 38º | COLISEUM BAR | 15.2 min |
| 39º | NOSSO BAR JF | 15.3 min |
| 40º | BAR DO BREJO | 15.5 min |

### 📈 Estatísticas Globais

| Métrica | Valor |
|---------|-------|
| **Tempo médio global** | 7.0 minutos |
| **Distância média global** | 5.94 km |
| **Cobertura da rede** | 100% (todos conectados) |
| **Pares de rotas calculados** | 1.560 |
| **Bares analisados** | 40 |

## 🚀 Como Executar

### Pré-requisitos

- Python 3.8 ou superior
- Conexão com internet (para baixar dados do OpenStreetMap)
- ~2-5 minutos de processamento (dependendo do hardware)

### Instalação

1. **Clone o repositório**
   ```bash
   git clone https://github.com/seu-usuario/acessibilidade-bares.git
   cd acessibilidade-bares
   ```
   
2. **Instale as dependências**

   ```python
   pip install pandas numpy networkx osmnx folium matplotlib seaborn scikit-learn branca
   ```

3. **Prepare o arquivo de dados**
   Certifique-se de ter o arquivo lista_bares.csv com a seguinte estrutura:

   ```python
   Name,latitude,longitude
   BAR BATATA D'MOLA,-21.761234,-43.349876
   BAR DO MARQUIM,-21.759876,-43.351234
   ```

4. **Execute o notebook**
   
   ```bash
   jupyter notebook acessibilidade_cb.ipynb
   ```

   Ou execute célula por célula no seu ambiente preferido (VS Code, Google Colab, etc.)

## 📁 Estrutura do projeto

   ```python
   acessibilidade-bares/
│
├── acessibilidade_cb.ipynb      # Notebook principal com toda a análise
├── lista_bares.csv               # Arquivo de entrada (coordenadas dos bares)
├── README.md                     # Este arquivo
│
├── outputs/                      # Pasta com resultados gerados
│   ├── acessibilidade_bares.csv  # Métricas detalhadas por bar
│   ├── resumo_acessibilidade.csv # Estatísticas gerais
│   └── mapa_acessibilidade_bares.html  # Mapa interativo
│
└── images/                       # Screenshots e visualizações (opcional)
    ├── heatmap.png
    ├── rankings.png
    └── mapa_interativo.png
   ```

## 📄 Arquivos gerados

| Arquivo | Formato | Descrição |
|---------|---------|-----------|
| `acessibilidade_bares.csv` | CSV | Métricas individuais por bar (tempos, distâncias, scores) |
| `resumo_acessibilidade.csv` | CSV | Estatísticas agregadas (média, mínimo, máximo) |
| `mapa_acessibilidade_bares.html` | HTML | Mapa interativo com marcadores coloridos |

## 🗺️ Visualizações

1. Heatmap de Tempos de Viagem
   - Matriz que mostra, para cada par de bares, o tempo de deslocamento (minutos):
   - Células amarelas/claras = menor tempo
   - Células vermelhas/escuras = maior tempo

2. Gráficos Comparativos
   - Tempo médio por bar (ordenado)
   - Distribuição dos tempos entre pares
   - Cobertura da rede por bar
   - Relação distância × tempo

3. Mapa Interativo
   - Marcadores coloridos (verde escuro = mais acessível, vermelho = menos acessível)
   - Popup com score, tempo médio e ranking
   - Legenda integrada

## 🛠️ Tecnologias Utilizadas

   | Biblioteca | Finalidade |
|:-----------|:-----------|
| `osmnx` | Baixar e modelar grafo viário do OpenStreetMap |
| `networkx` | Calcular caminhos mais curtos entre nós |
| `pandas` | Manipulação e análise de dados tabulares |
| `numpy` | Operações matriciais e estatísticas |
| `folium` | Criação de mapas interativos |
| `matplotlib` + `seaborn` | Geração de gráficos e heatmaps |
| `scikit-learn` | Normalização de métricas (MinMaxScaler) |
| `branca` | Colormaps para mapas Folium |

## ⚠️ Observações Técnicas

   🔍 Grafo viário: Construído a partir do centro geográfico dos bares com raio de 25 km (rede de direção para automóveis)
   🚗 Velocidade: Atributos de velocidade padrão do OSMnx (usados para calcular tempo de viagem)
   🌐 Conectividade: Todos os 40 bares ficaram 100% conectados (sem pares isolados)
   ⏱️ Performance: O cálculo dos ~780 pares únicos pode levar de 2 a 5 minutos. Para conjuntos maiores, recomenda-se otimização com paralelização ou    heurísticas.

## 🔮 Limitações e Melhorias Futuras

   ### Limitações Atuais
   - Não considera trânsito em tempo real ou horários de pico
   - Assume velocidade constante em todas as vias
   - Não inclui modos alternativos de transporte (pedestre, bicicleta, transporte público)

   ### Sugestões de Melhoria
   ✅ Adicionar ponderação por horário do dia (pico vs. horário comercial)
   ✅ Incluir múltiplos modos de transporte (walk, bike, transit)
   ✅ Implementar cálculo paralelo para acelerar matrizes grandes
   ✅ Adicionar análise de isócronas para cada bar (áreas alcançáveis em X minutos)
   ✅ Incorporar dados demográficos para planejamento de público-alvo

   ## 📚 Referências
   - OSMnx Documentation
   - NetworkX Shortest Paths
   - Folium Interactive Maps

   ## 📄 Licença
   Este projeto está sob a licença MIT. Sinta-se livre para usar, modificar e distribuir, desde que os devidos créditos sejam atribuídos.
   

   

      
   
