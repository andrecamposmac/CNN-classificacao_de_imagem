# Classificação de Imagens de Malária com CNN

Este projeto consiste em um notebook Jupyter que implementa uma Rede Neural Convolucional (CNN) para classificar imagens de células em duas categorias: **Infectadas (Parasitized)** e **Não Infectadas (Uninfected)**. O objetivo é criar uma ferramenta capaz de auxiliar na detecção da malária através da análise de imagens microscópicas.

## Descrição

O código realiza todo o pipeline de um projeto de visão computacional:
1.  **Análise Exploratória:** Carregamento e visualização das imagens e suas dimensões.
2.  **Pré-processamento:** Organização dos diretórios e redimensionamento das imagens para `(130, 130, 3)`.
3.  **Data Augmentation:** Uso do `ImageDataGenerator` para aumentar a variabilidade dos dados de treino (rotação, zoom, flip, etc.).
4.  **Construção do Modelo:** Definição de uma arquitetura CNN sequencial.
5.  **Treinamento:** Treino do modelo com *Early Stopping* para evitar overfitting.
6.  **Avaliação:** Geração de métricas de desempenho (Relatório de Classificação e Matriz de Confusão).
7.  **Predição:** Teste do modelo com uma imagem individual.

## Dataset

Os dados utilizados foram obtidos do repositório oficial de datasets de malária do NIH (National Library of Medicine):
*   **Fonte:** https://ceb.nlm.nih.gov/repositories/malaria-datasets
*   **Estrutura:** O notebook espera que os dados estejam organizados em pastas de treino e teste, separadas por classe (`parasitized` e `uninfected`).

## Tecnologias e Bibliotecas

O projeto foi desenvolvido em Python utilizando as seguintes bibliotecas principais:

*   **TensorFlow/Keras:** Para construção e treinamento da rede neural.
*   **NumPy & Pandas:** Manipulação de dados numéricos.
*   **Matplotlib & Seaborn:** Visualização de dados e imagens.
*   **Scikit-learn:** Métricas de avaliação (classification_report, confusion_matrix).

### Pré-requisitos
Para executar este notebook, certifique-se de ter as bibliotecas instaladas:

```bash
pip install tensorflow pandas numpy matplotlib seaborn scikit-learn
```

## Arquitetura do Modelo

A rede neural construída segue uma arquitetura sequencial clássica:

1.  **Camada Convolucional 1:** 32 filtros, kernel (3,3), ativação ReLU + Max Pooling (2,2).
2.  **Camada Convolucional 2:** 64 filtros, kernel (3,3), ativação ReLU + Max Pooling (2,2).
3.  **Camada Convolucional 3:** 64 filtros, kernel (3,3), ativação ReLU + Max Pooling (2,2).
4.  **Flatten:** Achatamento dos mapas de características.
5.  **Camada Densa (Fully Connected):** 128 neurônios, ativação ReLU.
6.  **Dropout:** Taxa de 0.5 (para regularização).
7.  **Camada de Saída:** 1 neurônio, ativação Sigmoid (classificação binária).

**Compilação:**
*   **Otimizador:** Adam
*   **Função de Perda:** Binary Crossentropy
*   **Métrica:** Acurácia

## Como Executar

1.  Baixe o dataset e organize os diretórios conforme esperado pelo script (`train_path` e `test_path`).
2.  Abra o notebook `CNN-Classificacao_de_imagem_malaria.ipynb` no Jupyter Notebook, JupyterLab ou Google Colab.
3.  Ajuste os caminhos dos diretórios de dados na célula correspondente:
    ```python
    my_data_dir = 'caminho/para/seu/diretorio'
    ```
4.  Execute as células sequencialmente para treinar e avaliar o modelo.

## Resultados

O notebook ao final exibe:
*   Gráficos de perda (loss) e acurácia durante o treinamento.
*   Uma matriz de confusão comparando as predições com os valores reais.
*   Um relatório de classificação com precisão, recall e f1-score.

---
