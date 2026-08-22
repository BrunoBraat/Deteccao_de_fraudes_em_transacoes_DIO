# 💳 Detecção de Fraudes em Transações Financeiras

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seu-usuario/Deteccao_de_fraudes_em_transacoes_DIO/blob/main/Deteccao_de_fraudes_em_transacoes.ipynb)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F1440A?logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-111111?logo=xgboost)

Projeto desenvolvido para identificação de fraudes bancárias em dados altamente desbalanceados, utilizando técnicas avançadas de Machine Learning, pré-processamento de atributos financeiros e explicabilidade de modelos com SHAP.

---

## 📌 Visão Geral do Problema

Em detecção de fraudes, a ocorrência de casos positivos (fraudes) representa uma fração ínfima do volume total de transações. 
* **O Desafio:** Um modelo ingênuo que classifique todas as transações como legítimas atinge ~99% de acurácia, mas falha totalmente no objetivo de negócio.
* **Métrica Foco:** Otimização prioritária da métrica **Recall (Sensibilidade)** combinada ao **F1-Score**, minimizando o risco financeiro de fraudes não detectadas.

---

## ⚙️ Pipeline e Técnicas Aplicadas

* **Pré-processamento & Feature Engineering:** Transformação logarítmica (`np.log1p`) e padronização (`StandardScaler`) na coluna `Amount`.
* **Tratamento de Desbalanceamento:** Teste e aplicação de **Undersampling**, **Oversampling (SMOTE)** e ajuste de pesos das classes (`class_weight="balanced"` e `scale_pos_weight`).
* **Modelagem:** Implementação e comparação entre **Regressão Logística**, **Random Forest Classifier** e **XGBoost Classifier**.
* **Otimização:** Ajuste de limiares de decisão (*thresholding*) e tuning de hiperparâmetros via **GridSearchCV**.
* **Explicabilidade (XAI):** Interpretação das variáveis mais determinantes para o modelo através de **SHAP (SHapley Additive exPlanations)**.

---

## 📊 Comparativo de Resultados

| Modelo | Precision (Classe 1) | Recall (Classe 1) | F1-Score (Classe 1) |
| :--- | :---: | :---: | :---: |
| **Logistic Regression (Baseline)** | 0.81 | 0.58 | 0.68 |
| **Pipeline + Logistic Regression** | 0.85 | 0.59 | 0.70 |
| **Random Forest (`class_weight="balanced"`)** | 0.88 | 0.82 | 0.85 |
| **XGBoost (`scale_pos_weight=10`)** | **0.96** | **0.83** | **0.89** |

> **Conclusão:** O **XGBoost** apresentou a melhor performance geral, alcançando **83% de Recall** e **96% de Precisão**, garantindo alta taxa de captura de fraudes com baixíssimo índice de alarmes falsos.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Manipulação & Visualização:** Pandas, NumPy, Matplotlib
* **Machine Learning:** Scikit-Learn, Imbalanced-Learn, XGBoost, SHAP
