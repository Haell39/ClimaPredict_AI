## Relatório de Análise e Previsão de Temperaturas em Los Angeles

**1. Visão Geral do Projeto**

Este projeto teve como objetivo principal prever a temperatura máxima do dia seguinte em Los Angeles, utilizando dados meteorológicos históricos que abrangem o período de 1960 a 2025. As temperaturas são medidas em Fahrenheit.

**2. Etapas Chave Realizadas**

* **Coleta e Carregamento de Dados:** Os dados foram carregados a partir de um arquivo CSV ('Los\_Angeles.csv').
* **Seleção e Renomeação de Colunas:** As colunas mais relevantes para a análise (Precipitação, Neve, Profundidade da Neve, Temperatura Máxima e Temperatura Mínima) foram selecionadas e renomeadas para maior clareza.
* **Tratamento de Valores Ausentes (NaN):**
    * As colunas 'neve' e 'prof\_neve' foram removidas devido à alta proporção de valores ausentes e à predominância de valores zero, indicando pouca ou nenhuma ocorrência significativa de neve em Los Angeles.
    * Valores ausentes na coluna 'precip' (precipitação) foram preenchidos com zero, considerando a alta frequência de dias sem precipitação.
    * Valores ausentes na coluna 'temp\_min' (temperatura mínima) foram preenchidos usando o método `ffill` (forward fill), propagando o último valor válido.
* **Conversão de Tipo de Dados:** O índice do DataFrame, que representava as datas, foi convertido para o tipo `datetime` para facilitar a manipulação temporal.
* **Engenharia de Features:** Novas características foram criadas para melhorar o desempenho do modelo:
    * `month_max`: Média móvel da temperatura máxima nos últimos 30 dias.
    * `month_day_max`: Razão entre a média móvel mensal (`month_max`) e a temperatura máxima do dia (`temp_max`).
    * `max_min`: Razão entre a temperatura máxima e a temperatura mínima.
    * `monthly_avg`: Média expansiva da temperatura máxima por mês.
    * `day_of_year_avg`: Média expansiva da temperatura máxima para cada dia do ano.
* **Definição do Alvo (Target):** A temperatura máxima do dia seguinte (`temp_max` shifted em -1) foi definida como a variável a ser prevista.
* **Divisão de Dados:** Os dados foram divididos em conjuntos de treinamento (até 31 de dezembro de 2023) e teste (a partir de 1º de janeiro de 2024).

**3. Modelo de Previsão**

* **Algoritmo:** Foi utilizado um modelo de Regressão Linear Ridge (com `alpha=0.1`).
* **Preditoras Iniciais:** 'precip', 'temp\_min', 'temp\_max'.
* **Preditoras Otimizadas:** 'precip', 'temp\_min', 'temp\_max', 'month\_max', 'month\_day\_max', 'max\_min', 'monthly\_avg', 'day\_of\_year\_avg'.

**4. Resultados e Métricas**

* **Erro Médio Absoluto (MAE):**
    * Com preditoras iniciais: 3.5859 Fahrenheit.
    * Com preditoras otimizadas (após engenharia de features): **3.4253 Fahrenheit**.
* **Análise de Coeficientes do Modelo (após otimização):**
    * `precip`: -0.2567 (impacto negativo, esperado)
    * `temp_min`: 0.1716
    * `temp_max`: 0.7450 (forte impacto positivo, esperado)
    * `month_max`: -0.1249
    * `month_day_max`: 11.6040
    * `max_min`: 9.1634
    * `monthly_avg`: 0.1736
    * `day_of_year_avg`: 0.0837
* **Correlação com o Alvo:** `temp_max` e `temp_min` são as variáveis mais correlacionadas com a temperatura máxima do dia seguinte.

**5. Diagnóstico e Análise de Erros**

* **Maiores Erros:** Os maiores erros de previsão foram observados em dias específicos, como 29 de maio de 2025 (erro de 22.01 Fahrenheit), 5 de setembro de 2024 (erro de 14.28 Fahrenheit) e 23 de março de 2025 (erro de 14.04 Fahrenheit). Esses outliers podem indicar eventos climáticos atípicos não capturados pelo modelo ou a necessidade de mais features.
* **Erro Médio por Mês:** A análise do erro médio absoluto por mês pode ajudar a identificar padrões sazonais nos erros de previsão.
* **Visualização:** Gráficos foram gerados para comparar as temperaturas reais e previstas, especialmente para o ano de 2025, e para visualizar a distribuição dos erros.

**6. Conclusão**

O projeto demonstrou a capacidade de prever a temperatura máxima em Los Angeles com um erro médio absoluto de aproximadamente 3.43 Fahrenheit. A engenharia de novas features baseadas em médias móveis e médias sazonais foi crucial para reduzir o erro do modelo, indicando que a inclusão de informações temporais e contextuais aprimora significativamente a precisão das previsões.