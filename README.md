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
   
2. **Instale as dependências**

   ```python
   pip install pandas numpy networkx osmnx folium matplotlib seaborn scikit-learn branca
