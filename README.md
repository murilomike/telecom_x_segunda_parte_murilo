
# Telecom_X_Murilo_Parte2

### 1. Objetivo

Este projeto tem como objetivo analisar os dados de churn de clientes de uma empresa de telecomunicações, identificando os principais fatores que contribuem para o cancelamento de contratos. A meta final é desenvolver um modelo de machine learning capaz de prever com precisão quais clientes têm maior probabilidade de cancelar, permitindo que a empresa tome medidas proativas para retenção.

### 2. Ferramentas e Tecnologias

-   **Linguagem de Programação:** Python
    
-   **Bibliotecas Utilizadas:**
    
    -   **Pandas:** Manipulação e análise de dados tabulares
        
    -   **NumPy:** Cálculos numéricos
        
    -   **Scikit-learn:** Modelagem de machine learning, divisão de dados, classificação e métricas
        
    -   **Matplotlib e Seaborn:** Visualização de dados
        
    -   **Plotly:** Gráficos interativos
        
    -   **imbalanced-learn (imblearn):** Técnicas para lidar com dados desbalanceados, como SMOTE
        

### 3. Fonte de Dados

Os dados foram obtidos a partir de um arquivo JSON: `Telco-Customer-Churn.json` O conjunto inclui informações sobre clientes, planos, dados demográficos e status de cancelamento.

### 4. Processamento e Limpeza dos Dados

Etapas realizadas:

1.  **Carregamento:** Utilizando Pandas
    
2.  **Desaninhamento:** Uso de `json_normalize` para colunas com dados aninhados (`customer`, `phone`, `internet`, `account`)
    
3.  **Tratamento de Valores Ausentes:** Preenchimento com médias
    
4.  **Remoção de Duplicatas**
    
5.  **Correção de Tipos de Dados:** Ex: `Charges.Total` convertido para `float`
    
6.  **Tratamento de Inconsistências:** Correção de valores categóricos inválidos (ex: strings vazias em `Churn`)
    

### 5. Feature Engineering

Novas variáveis criadas:

-   `Contrato_Internet`: Combinação do tipo de contrato com serviço de internet
    
-   `Total_Servicos`: Contagem de serviços adicionais (segurança online, backup, etc.)
    
-   `Streaming_Internet`: Combinação de uso de streaming de TV e filmes
    
-   `Charge_Tempo_Ratio`: Razão entre cobrança mensal e tempo de contrato
    
-   `Idoso_Com_Dependentes`: Indica se o cliente é idoso e possui dependentes
    

### 6. Modelagem

1.  **Modelo Escolhido:** RandomForest, pela capacidade de lidar com dados não lineares e boa interpretabilidade
    
2.  **Divisão dos Dados:** Treino e teste (80/20)
    
3.  **Balanceamento:** Aplicação de SMOTE para gerar amostras sintéticas da classe minoritária (`Churn = Sim`)
    
4.  **Treinamento:** Modelo treinado com dados balanceados
    
5.  **Avaliação:** Validação cruzada estratificada com métricas:
    
    -   Acurácia
        
    -   Precisão
        
    -   Recall
        
    -   F1-Score
        
    -   AUC
        
    -   Matriz de Confusão
        

### 7. Resultados

O modelo com melhor desempenho priorizou o **recall** para a classe "Cancelou", com os seguintes resultados:

-   **AUC:** 0.826
    
-   **Relatório de Classificação:**
    

Métrica

0.0 (Não Cancelou)

1.0 (Cancelou)

Precisão

0.89

0.53

Recall

0.76

0.74

F1-Score

0.82

0.62

O destaque é o _recall_ de 0.74 para clientes que cancelaram, permitindo ações mais eficazes de retenção.

### 8. Conclusão

O modelo desenvolvido apresenta bom desempenho na previsão de churn, com foco em recall para identificar clientes em risco. Futuras melhorias podem incluir:

-   Testes com outros algoritmos de machine learning
    
-   Inclusão de novas variáveis (ex: tipo de assinatura, valor do produto)
