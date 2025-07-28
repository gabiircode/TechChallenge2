
# 📊 Tech Challenge FIAP – Previsão de Tendência do IBOVESPA

Este repositório contém o projeto desenvolvido por **Gabriela Rodrigues** como parte do Tech Challenge da Pós-Tech FIAP, com foco em Machine Learning aplicado ao mercado financeiro.

---

## 🎯 Objetivo

Construir um modelo de machine learning capaz de prever a **tendência diária do IBOVESPA** se o índice fechará em alta ou baixa no dia seguinte com uma acurácia mínima de 75% nos últimos 30 dias úteis.

---

## 🧠 Abordagem Técnica

- **Fonte de dados:** Investing.com  
- **Período utilizado:** ~8 anos de dados diários  
- **Variáveis:** Abertura, Máxima, Mínima, Fechamento, Volume, Variação %

### 📌 Engenharia de Atributos

- Lags: `lag_1` a `lag_5`  
- Médias móveis: `sma_5`, `sma_10`  
- Indicadores técnicos: `RSI`, `MACD`, `MACD Signal`

### 🎯 Definição do Target

- O alvo (`target`) é 1 quando `pct_change > 0.007` (alta > 0,7%)
- Justificativa: evita ruído e foca em oscilações com impacto real

---

## ⚙️ Modelagem

- **Algoritmo:** `XGBoostClassifier`
- **Validação temporal:** `TimeSeriesSplit` (5 blocos)
- **Otimização:** `GridSearchCV`
- **Seleção de atributos:** `SelectFromModel`
- **Normalização:** `StandardScaler`

---

## 📈 Resultados

| Métrica                   | Resultado    |
|---------------------------|--------------|
| Acurácia - Treinamento    | 75,27%       |
| Acurácia - Teste (30 dias)| 83,33% ✅     |
| Validação cruzada média   | 71,16%       |
| Desvio padrão CV          | 4,07%        |
| Previsão final            | Tendência de **baixa** |
| Fechamento estimado       | R$ 137.481,00 |

---

## 📌 Interpretação Gerencial

O modelo apresentou desempenho estável e confiável, superando a meta de acurácia com margem.  
Pode ser utilizado como ferramenta de apoio à decisão para investidores e analistas de risco.

---

## 🔮 Aplicações Futuras

- Previsão de ações específicas
- Extensão para índices internacionais
- Integração com dashboards de BI

---

## 👩‍💻 Autora

**Gabriela Rodrigues**  
