
1)Problema: Detectar transações fraudulentas em um cenário de extremo desbalanceamento, onde as fraudes representam apenas **0.17%** das transações. O objetivo é maximizar a detecção de fraudes (Recall) minimizando os falsos alarmes (Precision).

2)Dados: Utilizou-se o dataset clássico de *Credit Card Fraud Detection* (Kaggle), contendo transações de cartões europeus. As features passaram por PCA (V1-V28) para anonimização.

3)Metodologia

  3.1)Pré-processamento: Normalização da feature `Amount` com `StandardScaler`.
  
  3.2)Estratégia: Divisão de treino/teste estratificada (80/20) para manter a proporção de fraudes.
  
  3.3)Modelagem: Comparação entre uma *Baseline* (Regressão Logística) e um modelo *Ensemble* (Random Forest), ambos com ajuste de pesos de classe (`class_weight='balanced'`).

4) Resultados
   
!! **A métrica escolhida para decisão foi a **AUPRC (Area Under Precision-Recall Curve)**, visto que a ROC AUC se mostrou enganosa devido ao desbalanceamento das classes.**

| Modelo | ROC AUC (Enganosa) | **PR AUC (Métrica Real)** |
| :--- | :--- | :--- |
| Regressão Logística | 0.9714 | 0.7156 |
| **Random Forest** | 0.9580 | **0.8485** |

5) Conclusão
O **Random Forest** mostrou-se superior, mantendo a precisão elevada mesmo ao aumentar a taxa de captura de fraudes.
