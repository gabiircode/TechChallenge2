
# 📈 Tech Challenge FIAP – Previsão de Tendência do IBOVESPA

Este repositório apresenta a solução desenvolvida por **Gabriela Rodrigues** como parte do desafio técnico da Pós-Tech FIAP, com foco em machine learning aplicado ao mercado financeiro.  
O objetivo é prever se o índice IBOVESPA fechará em alta ou baixa no próximo pregão, utilizando dados históricos e aprendizado supervisionado.

---

## 🎯 Objetivo do Projeto

Desenvolver um modelo preditivo binário (alta ou baixa) para o fechamento diário do índice IBOVESPA, com foco em:

- **Alta confiabilidade preditiva**
- **Aplicabilidade prática para investidores e analistas**
- **Acurácia mínima de 75% nos últimos 30 dias úteis**

---

## 🔢 Fonte dos Dados

- **Origem:** Investing.com
- **Período:** Aproximadamente 8 anos (diário)
- **Colunas originais:** Data, Abertura, Máxima, Mínima, Último, Volume, Variação %

---

## 📊 Análise Exploratória (EDA)

O EDA incluiu:

- Tendência histórica do índice
- Distribuição dos valores de fechamento
- Correlação entre variáveis técnicas
- Identificação de padrões sazonais e ruído

Gráficos de linha e heatmaps foram utilizados para visualizar o comportamento do mercado e auxiliar na criação de variáveis.

---

## ⚙️ Engenharia de Atributos

Foram geradas diversas variáveis técnicas com base no comportamento do preço:

- `lag_1` a `lag_5`: defasagens de 1 a 5 dias do preço de fechamento
- `sma_5`, `sma_10`: médias móveis simples
- `RSI`: índice de força relativa (14 dias)
- `MACD` e `MACD Signal`: indicadores de momentum
- `pct_change`: variação percentual do dia seguinte

### 🎯 Definição do alvo (`target`)

- O valor `1` foi atribuído quando a variação percentual do dia seguinte superava **+0,7%**
- Justificativa: evitar que o modelo interprete oscilações irrelevantes como tendência

---

## 🧠 Modelagem

- **Modelo principal:** `XGBoostClassifier`
- **Técnicas aplicadas:**
  - Normalização com `StandardScaler`
  - Seleção automática de variáveis com `SelectFromModel`
  - Balanceamento com `scale_pos_weight`
  - Otimização com `GridSearchCV`
  - Validação com `TimeSeriesSplit` (5 blocos)

---

## 🧪 Divisão de Dados

- Dados foram ordenados cronologicamente
- **Últimos 30 dias úteis** utilizados exclusivamente para teste (simulação real de uso)
- Sem embaralhamento de dados (essencial para séries temporais)

---

## 📈 Resultados

| Métrica                       | Resultado     |
|-------------------------------|---------------|
| Acurácia no treino            | 75,27%        |
| Acurácia no teste (30 dias)   | ✅ **83,33%** |
| Acurácia validação cruzada    | 71,16%        |
| Desvio padrão CV              | 4,07%         |
| Previsão final                | Tendência de **baixa** |
| Fechamento estimado           | R$ 137.481,00 |

---

## 📌 Interpretação Gerencial

O modelo entrega uma previsão robusta, superando a meta exigida.  
Pode ser utilizado para apoiar decisões de investimento, alertas operacionais ou monitoramento de tendências de mercado.  
Além disso, é interpretável, replicável e pronto para integração com dashboards e APIs financeiras.

---

## 🔮 Possíveis Expansões

- Previsão de ações individuais (PETR4, VALE3, etc.)
- Inclusão de dados macroeconômicos e eventos
- Modelos alternativos (LSTM, Prophet)
- Automação via pipeline em tempo real

---

## 🗂️ Estrutura do Projeto

```
📁 dataset/                  # Dados tratados
📁 notebooks/                # Notebooks de análise e modelagem
📄 tech_challenge_ibovespa.ipynb   # Notebook principal
📄 README.md                 # Descrição do projeto
```

---

## 👩‍💻 Autora

**Gabriela Rodrigues**   
🔗 [LinkedIn](https://www.linkedin.com/in/gabrielarodriguesmkt)

---

## ✅ Status: Projeto finalizado e validado ✅

Este projeto atendeu todos os critérios técnicos, estatísticos e de storytelling exigidos na Fase 2 do Tech Challenge FIAP.
