# Crop Feature Prediction – Mini Project

Este repositório contém um mini projeto de experimentação em Machine Learning aplicado ao domínio agrícola.  
O objetivo principal é **avaliar o poder preditivo de diferentes features** para prever o tipo de cultura (`crop`) presente em um conjunto de dados.

A estrutura do projeto foi definida de forma modular para facilitar testes, reprodutibilidade e expansão futura.

---

## 1. Objetivo do Projeto

O projeto tem como finalidade:

- Investigar a relevância de diferentes atributos na predição de culturas agrícolas.
- Implementar uma pipeline simples e clara para experimentação.
- Avaliar cada feature individualmente utilizando validação cruzada.
- Criar uma base para futuros modelos supervisonados mais robustos.

---

## 2. Principais Componentes

### **Pipeline**
A função `pipeline()` executa:

1. Seleção do dataset e variável-alvo (`label_name`).
2. Extração sequencial de features usando `get_feature_and_label()`.
3. Avaliação preditiva de cada feature por meio de `evaluate_feature_prediction()`.

### **Extração de Features**

- `get_feature_and_label(dataset, feature_name, label_name)`  
  Responsável por isolar cada feature individualmente para criação dos pares `(X, y)`.

### **Avaliação do Modelo**

- `evaluate_feature_prediction(X, y, n_splits=6, shuffle=True, random_state=42)`  
  Aplica:
  - `KFold` com embaralhamento,
  - `LogisticRegression` como estimador,
  - `cross_val_score` como métrica base.

Correção importante: parâmetros do `KFold` devem ser passados como argumentos nomeados.

---

## 3. Tecnologias e Bibliotecas

- Python 3.x  
- scikit-learn  
  - `LogisticRegression`
  - `KFold`
  - `cross_val_score`
- pandas  
- numpy  
- Jupyter Notebook (para experimentação)

---

## 4. Como Executar

### **1. Clonar o repositório**
```bash
git clone https://github.com/<seu-usuario>/crop-feature-prediction.git
cd crop-feature-prediction
