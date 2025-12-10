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
- seaborn
- Jupyter Notebook (para experimentação)

---

## 4. Como Executar

### **1. Clonar o repositório**
```bash
git clone https://github.com/VYuske/crop-feature-prediction.git
cd crop-feature-prediction
```

### 5. Conclusão

A análise conduzida permitiu identificar de maneira objetiva quais atributos possuem maior capacidade de discriminar as classes de cultura no dataset avaliado. Entre todas as variáveis testadas individualmente, a feature K (Potássio) apresentou o melhor desempenho nos experimentos de validação cruzada, indicando que ela contém o sinal mais relevante para a previsão do tipo de cultura quando utilizada isoladamente.

Esse resultado sugere que a concentração de K no solo exerce um papel determinante no comportamento das culturas representadas, refletindo um padrão consistente que o modelo conseguiu capturar mesmo com o uso de um classificador linear simples. Em contraste, outras features demonstraram menor capacidade isolada de generalizar, reforçando a importância de priorizar K em análises iniciais, modelos baseline ou estratégias de seleção de atributos.

Além de cumprir seu objetivo de avaliar o poder preditivo individual das variáveis, o projeto estabeleceu uma base metodológica clara e reprodutível — útil tanto para aprofundar as investigações quanto para evoluir a pipeline com modelos mais complexos, engenharia de features e avaliação multivariada. A partir dos achados, o próximo passo natural é explorar combinações entre K e demais atributos, bem como testar algoritmos não lineares para compreender melhor as interações entre as variáveis.
