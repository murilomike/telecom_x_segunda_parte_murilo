# Telecom_X_prevendo_churn_partII

## Projeto de Análise de Churn de Clientes

### 1. Objetivo

Este projeto tem como objetivo analisar os dados de churn de clientes de uma empresa de telecomunicações para identificar os principais fatores que contribuem para o cancelamento de contratos. O objetivo final é desenvolver um modelo de machine learning que possa prever com precisão quais clientes têm maior probabilidade de cancelar, permitindo que a empresa tome medidas proativas para reter esses clientes.

### 2. Ferramentas e Tecnologias

*   **Linguagem de Programação:** Python
*   **Bibliotecas:**
    *   **Pandas:** Para manipulação e análise de dados tabulares.
    *   **NumPy:** Para cálculos numéricos.
    *   **Scikit-learn:** Para modelagem de machine learning, incluindo divisão de dados, modelos de classificação e métricas de avaliação.
    *   **Matplotlib e Seaborn:** Para visualização de dados.
    *   **Plotly:** Para criação de gráficos interativos.
    *   **imbalanced-learn (imblearn):** Para lidar com dados desbalanceados usando técnicas como SMOTE.

### 3. Fontes de Dados

Os dados utilizados neste projeto foram obtidos a partir de um arquivo JSON (`https://raw.githubusercontent.com/sthemonica/alura-voz/refs/heads/main/Dados/Telco-Customer-Churn.json`) contendo informações sobre clientes, seus planos, seus dados demográficos e seu status de cancelamento.

### 4. Processamento e Limpeza dos Dados

O processo de preparação dos dados envolveu as seguintes etapas:

1.  **Carregamento dos Dados:** Os dados foram carregados a partir do arquivo JSON usando a biblioteca Pandas.
2.  **Desaninhamento:** As colunas que continham dados JSON aninhados (como `customer`, `phone`, `internet` e `account`) foram desaninhadas usando a função `json_normalize`.
3.  **Tratamento de Valores Ausentes:** Os valores ausentes foram preenchidos com a média das respectivas colunas.
5.  **Remoção de Duplicatas:** Linhas duplicadas foram removidas do conjunto de dados.
6.  **Correção de Tipos de Dados:** Os tipos de dados de algumas colunas foram corrigidos (por exemplo, a coluna `Charges.Total` foi convertida para o tipo `float`).
7.  **Tratamento de Inconsistências:** Inconsistências nos dados categóricos foram corrigidas (por exemplo, strings vazias na coluna `Churn`).

### 5. Feature Engineering

Novas features foram criadas para capturar informações mais relevantes sobre os clientes:

*   `Contrato_Internet`: Combinou as informações sobre o tipo de contrato e o serviço de internet.
*   `Total_Servicos`: Contou o número de serviços adicionais que o cliente possui (segurança online, backup online, etc.).
*   `Streaming_Internet`: Combinou as informações sobre o uso de serviços de streaming de TV e filmes.
*   `Charge_Tempo_Ratio`: Calculou a razão entre as cobranças mensais e o tempo de contrato.
*   `Idoso_Com_Dependentes`: Indicou se o cliente é idoso e tem dependentes.

### 6. Modelagem

1.  **Seleção do Modelo:** Um modelo RandomForest foi escolhido para prever o churn devido à sua capacidade de lidar com dados não lineares e sua interpretabilidade.
2.  **Divisão dos Dados:** Os dados foram divididos em conjuntos de treino e teste (80/20).
3.  **Tratamento de Desbalanceamento:** A técnica SMOTE (Synthetic Minority Oversampling Technique) foi utilizada para lidar com o desbalanceamento dos dados, gerando amostras sintéticas da classe minoritária (Churn = Sim).
4.  **Treinamento do Modelo:** O modelo RandomForest foi treinado com os dados de treino balanceados.
5.  **Avaliação do Modelo:** O modelo foi avaliado usando validação cruzada estratificada e as seguintes métricas:
    *   Acurácia
    *   Precisão
    *   Recall
    *   F1-Score
    *   AUC (Area Under the Curve)
    *   Matriz de Confusão

### 7. Resultados

Após experimentar diferentes configurações e ajustar o limiar de decisão, o modelo com o melhor desempenho foi aquele que priorizou o **recall** para a classe "Cancelou". Este modelo apresentou os seguintes resultados:

*   **AUC: 0.826**
*   **Relatório de Classificação:**

    | Métrica      | 0.0 (Não Cancelou) | 1.0 (Cancelou) |
    | :----------- | :------------------- | :-------------- |
    | Precisão     | 0.89                 | 0.53            |
    | Recall       | 0.76                 | 0.74            |
    | F1-Score     | 0.82                 | 0.62            |

O ponto crucial aqui é o *recall* de 0.74 para a classe "Cancelou". Isso significa que o modelo é capaz de identificar 74% dos clientes que realmente cancelam, o que é valioso para implementar estratégias de retenção eficazes.

### 8. Conclusão

O modelo desenvolvido neste projeto é capaz de prever o churn de clientes com uma precisão razoável e um bom recall. Ao priorizar o recall, podemos identificar a maioria dos clientes que têm probabilidade de cancelar e tomar medidas proativas para retê-los.

Embora o modelo já apresente um bom desempenho, há espaço para melhorias. Futuras pesquisas podem se concentrar em:

*   Explorar outros modelos de machine learning.
*   Incorporar mais dados (e.g., tipo de assinatura, valor do produto).
*   Ajustar os pesos das classes para equilibrar ainda mais a precisão e o recall.


```

