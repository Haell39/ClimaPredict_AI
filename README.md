# Análise e Previsão de Temperaturas em Los Angeles ☀️📈

Este repositório contém um projeto de análise e modelagem de dados meteorológicos históricos da cidade de Los Angeles, focado na previsão da **temperatura máxima do dia seguinte**. O objetivo é demonstrar um fluxo completo de trabalho em Ciência de Dados, desde a ingestão até a visualização e avaliação do modelo.

## 🎯 Objetivo

Prever a temperatura máxima diária em Los Angeles (em Fahrenheit) com base em dados históricos, utilizando técnicas de aprendizado de máquina.

## 📊 Conjunto de Dados

Os dados utilizados abrangem o período de 1960 a 2025 e contêm diversas métricas climáticas. As principais colunas utilizadas para a previsão incluem precipitação (PRCP), temperatura máxima (TMAX) e temperatura mínima (TMIN).

## ✨ Principais Etapas do Projeto

* **Limpeza e Pré-processamento de Dados:** Tratamento de valores ausentes e padronização das colunas.
* **Engenharia de Features:** Criação de novas variáveis (e.g., médias móveis, proporções) para enriquecer o conjunto de dados e melhorar o poder preditivo do modelo.
* **Análise Exploratória de Dados (EDA):** Visualizações para entender padrões, distribuições e a relação entre as variáveis.
* **Modelagem Preditiva:** Utilização de um modelo de Regressão Ridge para prever a temperatura máxima do dia seguinte.
* **Avaliação do Modelo:** Análise do desempenho do modelo através de métricas de erro (MAE) e visualização de previsões vs. valores reais, incluindo uma análise detalhada dos outliers.

## 🛠️ Tecnologias Utilizadas

* **Python** 🐍
* **Pandas** 🐼: Manipulação e análise de dados.
* **NumPy** 🔢: Operações numéricas.
* **Matplotlib** 📈 & **Seaborn** 📊: Visualização de dados.
* **Scikit-learn** 🧠: Construção e avaliação do modelo de Machine Learning.

## 🚀 Como Executar

1.  Clone este repositório: `git clone https://github.com/Haell39/ClimaPredict_AI.git`
2.  Navegue até o diretório do projeto.
3.  Garanta que o arquivo `Los_Angeles.csv` esteja na pasta `data/`.
4.  Instale as dependências: `pip install -r requirements.txt`
5.  Abra o notebook `weather.ipynb` em um ambiente Jupyter e execute as células.

