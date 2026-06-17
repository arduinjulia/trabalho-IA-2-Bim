Disciplina de Inteligência Artificial - Professor Munif - Unicesumar 2026

## Integrantes
- Júlia Batistella Arduin - RA: 23059881-2
- Beatriz Lemes Vasconcelos de Souza - RA: 23113429-2

## Contextualização e Problema
Atualmente existem milhares de avaliações de filmes publicadas diariamente. Ler todas manualmente é inviável. O objetivo do projeto é desenvolver uma Inteligência Artificial capaz de identificar automaticamente se uma avaliação de filme é positiva ou negativa.

A nossa hipótese é que a arquitetura de Redes Neurais (MLP) apresentará um desempenho superior ao algoritmo estatístico (Naive Bayes) na classificação de sentimentos das avaliações de filmes.

## Descrição do Dataset
* **Origem:** IMDb Dataset (Kaggle)
* **Acesso:** [Link para o Dataset](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)
* **Tamanho:** 50.000 avaliações de filmes (sem valores nulos).
* **Distribuição:** Dados perfeitamente balanceados (25.000 avaliações positivas e 25.000 negativas).
* **Variável Alvo:** Coluna `sentiment` (positivo = 1 / negativo = 0).

## Pré-processamento
Convertemos os sentimentos para valores numéricos. Vetorizamos os textos utilizando a técnica TF-IDF (Term Frequency – Inverse Document Frequency), extraindo os 5.000 atributos (palavras) mais relevantes. Por fim, dividimos os dados em 80% para treino (40.000 amostras) e 20% para teste (10.000 amostras).

## Métodos de IA Utilizados e Avaliação

### MODELO 1: Naive Bayes (Parte 1 da disciplina)
Foi utilizado o algoritmo Multinomial Naive Bayes.
* **Acurácia:** 0.85 (85%)
* **Precisão (Negativo / Positivo):** 0.85 / 0.85
* **Recall (Negativo / Positivo):** 0.85 / 0.85
* **F1-Score:** 0.85

![Matriz de Confusão Naive Bayes](matriz_confusao_Naive.png)

### MODELO 2: Redes Neurais MLP (Parte 2 da disciplina)
Foi utilizada uma arquitetura Multilayer Perceptron (MLP) com uma camada oculta de 50 neurônios, treinada por 20 épocas.
* **Acurácia:** 0.87 (87,02%)
* **Precisão (Negativo / Positivo):** 0.88 / 0.87
* **Recall (Negativo / Positivo):** 0.86 / 0.88
* **F1-Score:** 0.87

![Matriz de Confusão MLP](matriz_confusao_MLP.png)
![Curva de Perda MLP](curva_perda_MLP.png)

## Comparação dos Resultados
Ambos os modelos apresentaram excelentes resultados para processamento de texto. O Naive Bayes atingiu 85% de acurácia com um tempo de treinamento quase instantâneo, provando ser um ótimo modelo base (baseline). 

A Rede Neural MLP atingiu **87,02% de acurácia**, superando o modelo estatístico. Embora o MLP seja mais complexo e exija maior poder computacional e tempo de treinamento (como evidenciado pela curva de perda decrescente), ele conseguiu capturar padrões mais sutis nas palavras, resultando em uma precisão de 88% para prever avaliações negativas e um recall de 88% para avaliações positivas.

## Conclusão
O projeto demonstrou que a conversão de textos em atributos numéricos via TF-IDF, aliada a algoritmos de classificação, resolve eficientemente o problema de análise de sentimentos em massa. A nossa hipótese inicial foi **confirmada**: a Rede Neural superou o Naive Bayes. Para um cenário de produção onde a precisão máxima é exigida, o MLP é a melhor escolha, mas se o sistema exigir respostas rápidas com baixo custo de processamento, o Naive Bayes ainda seria uma opção altamente recomendável.

## Como executar e baixar os modelos
1. Clone este repositório.
2. Baixe o dataset no link indicado acima e coloque na pasta `dataset/`.
3. Os modelos treinados (`modelo_nb.pkl` e `modelo_mlp.pkl`) estão disponíveis na raiz deste repositório (ou basta rodar os notebooks para gerá-los novamente). 
4. Execute os notebooks na pasta respectiva para reproduzir todos os resultados e gráficos.