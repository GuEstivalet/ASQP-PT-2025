# ASQP-PT Data Augmentation and Fine-Tuning

Este repositório reúne os notebooks utilizados no desenvolvimento e avaliação de técnicas de aumento de dados para a tarefa de **Aspect Sentiment Quad Prediction (ASQP)** em português.

O pipeline contempla:

- Pré-processamento
- Geração de conjuntos de treino aumentados;
- Busca de hiperparâmetros com validação cruzada;
- Ajuste fino e avaliação de modelos PTT5-base/mT5-base.


# Requisitos

Os notebooks foram desenvolvidos para execução no **Google Colab**, com Python 3.10+.

Principais bibliotecas utilizadas:

- PyTorch
- Transformers (Hugging Face)
- Datasets
- Evaluate
- Optuna
- Pandas
- NumPy
- Scikit-learn
- Matplotlib

# Observações

- Os notebooks utilizam arquivos armazenados no Google Drive local.
- Os caminhos para os conjuntos de dados podem precisar ser ajustados conforme o ambiente de execução.
- Os experimentos utilizam sementes fixas para favorecer a reprodutibilidade.

# Estrutura do projeto

MODELS = { PTT5-base, mT5-base}

DATASETS = { train_processed.csv, aug_sr.csv, aug_oversampling.csv}

# Pré-processamento

Manipulação dos conjuntos de treino e teste da competição.


# Data Augmentation

Cada notebook implementa o respectivo método de seu título sobre os conjuntos pré-processados.

# Hyperparameters Search (HPS)

Otimizar: learning rate, warmup ratio, weight decay.

Para cada combinação MODELS x DATASETS:
6 trials para explorar o intervalo de busca
	3-fold cross validation
	
A configuração da trail com melhor Medida-F média dentre as cross-validations é a escolhida para a próxima etapa.

# Baseline

Para cada combinação MODELS x DATASETS:
Utiliza os Hiperparâmetros da etapa anterior para o ajuste fino, com o respectivo conjunto de treino;
Inferência e extração de métricas: precisão, revocação, medida-f.
