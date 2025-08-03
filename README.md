# 📈 Tech Challenge FIAP – Previsão de Tendência do IBOVESPA

Este repositório apresenta o projeto desenvolvido por **Gabriela Rodrigues** como parte do Tech Challenge da Pós-Tech FIAP, com foco em **Machine Learning aplicado ao mercado financeiro**. O objetivo principal é prever a tendência de fechamento do índice IBOVESPA no próximo pregão — se será de **alta ou baixa** — com **alta acurácia e confiabilidade**.

---

## 🎯 Objetivo do Projeto

- Criar um modelo preditivo binário (alta ou baixa) para o fechamento diário do IBOVESPA  
- Utilizar dados históricos dos últimos 8 anos  
- Aplicar boas práticas de modelagem para séries temporais  
- Atingir no mínimo **75% de acurácia nos últimos 30 dias úteis**  

---

## 🗂️ Fonte dos Dados

- **Origem:** Investing.com  
- **Período:** ~8 anos de histórico diário  
- **Variáveis brutas:** Data, Abertura, Máxima, Mínima, Último (Fechamento), Volume e Variação %

---

## 📊 Análise Exploratória (EDA)

- Visualização da tendência histórica do índice  
- Distribuição dos fechamentos  
- Cálculo da correlação entre indicadores técnicos  
- Eliminação de ruídos antes da modelagem  

Foram utilizados gráficos de linha, histogramas e heatmaps para guiar a construção das variáveis mais relevantes.

---

## 🛠️ Engenharia de Atributos

- `lag_1` a `lag_5`: preços de fechamento defasados  
- `sma_5` e `sma_10`: médias móveis simples  
- `RSI`: Índice de Força Relativa (14 períodos)  
- `MACD` e `MACD Signal`: indicador de momentum  
- `pct_change`: variação percentual do dia seguinte  

### 🎯 Alvo (`target`)
- 1 → quando a variação do dia seguinte for **superior a 0,7%**  
- 0 → caso contrário  
**Justificativa:** pequenas oscilações não representam tendências reais e podem gerar ruído no modelo.

---

## 🤖 Modelagem

- **Algoritmo utilizado:** `XGBoostClassifier`  
- **Por que XGBoost?**
  - Alta performance em dados tabulares  
  - Explicabilidade das variáveis  
  - Resistente a overfitting  
  - Ideal para classificações binárias desbalanceadas  

### 🧪 Técnicas Aplicadas

- Padronização com `StandardScaler`  
- Seleção automática de atributos com `SelectFromModel`  
- Balanceamento de classes com `scale_pos_weight`  
- Otimização com `GridSearchCV`  
- Validação cruzada com `TimeSeriesSplit` (5 blocos)

---

## 🧪 Divisão de Dados

- Separação temporal (sem shuffle)  
- **Últimos 30 dias úteis** foram reservados exclusivamente para teste  
- Simulação realista: o modelo foi testado com dados que ele nunca viu

---

## 📈 Resultados

| Métrica                        | Valor          |
|-------------------------------|----------------|
| Acurácia no treino            | 75,27%         |
| Acurácia no teste (últimos 30 dias) | ✅ **83,33%** |
| Acurácia validação cruzada    | 71,16%         |
| Desvio padrão da CV           | 4,07%          |
| Previsão final                | Tendência de **baixa** |
| Fechamento estimado           | R$ 137.481,00   |

---

## 🧠 Interpretação Gerencial

O modelo entrega previsões com **alta confiabilidade**, superando a meta proposta.  
Pode ser utilizado por:

- Investidores para identificar oportunidades de compra ou venda  
- Times de risco e tesouraria como alerta tático  
- Dashboards de BI como uma camada preditiva  

O código é modular, explicável e facilmente adaptável para outros ativos ou contextos.

---

## 🚀 Possíveis Extensões

- Previsão de ações específicas (PETR4, VALE3, etc.)  
- Inclusão de dados macroeconômicos (IPCA, Selic, etc.)  
- Teste com LSTM, Prophet ou ensemble de modelos  
- Automação do pipeline via agendamento (e.g. Airflow)



