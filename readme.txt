📊 Tech Challenge — Sentiment Analysis of Financial Complaints
🧠 Classificação de Reclamações Financeiras com NLP e Deep Learning
Este projeto foi desenvolvido como parte do Tech Challenge, integrando conceitos de Análise Exploratória de Dados (EDA), Processamento de Linguagem Natural (NLP) e Deep Learning.
O foco é a classificação automática do sentimento de reclamações financeiras (positivo ou negativo), bem como a identificação das principais dores dos clientes por categoria de produto financeiro, utilizando dados reais do Consumer Financial Protection Bureau (CFPB).

🎯 Objetivos

Classificar automaticamente o sentimento das reclamações a partir do texto
Aplicar técnicas de NLP para limpeza e preparação textual
Realizar EDA profunda para compreensão do comportamento dos consumidores
Identificar produtos, empresas e problemas mais recorrentes
Implementar baseline clássico (TF‑IDF + Logistic Regression)
Implementar modelo Deep Learning com Keras
Avaliar desempenho com métricas adequadas
Criar pipeline reprodutível e explicável


🗂️ Fonte dos Dados
Os dados utilizados são provenientes do Consumer Complaints Database, mantido pelo Consumer Financial Protection Bureau (CFPB).
São reclamações reais de consumidores sobre produtos e serviços financeiros, publicadas após confirmação de relacionamento comercial.
Principais campos utilizados:

Consumer complaint narrative
Product
Issue
Company
Date received
Submitted via
Company response to consumer


📈 Visão Geral do Dataset
A base foi coletada via API do CFPB e passou por múltiplas etapas de tratamento.
Fluxo de preparação:

Base original com aproximadamente 178 mil registros
Remoção de duplicatas baseada na narrativa da reclamação
Tratamento de dados ausentes
Limpeza textual
Remoção de outliers textuais (comprimento das reclamações)
Base final com aproximadamente 87 mil registros válidos


🧼 Limpeza e Pré‑Processamento
As principais etapas de preparação dos dados foram:

Conversão de colunas de data para formato datetime
Remoção de registros duplicados
Normalização do texto:

Conversão para lowercase
Remoção de anonimizações (XXXX)
Remoção de números e pontuações
Normalização de espaços


Tokenização com NLTK
Remoção de stopwords
Lematização (WordNetLemmatizer)
Criação de colunas auxiliares como clean_text, cleaned_text e word_count


🔎 Tratamento de Outliers Textuais
Foi analisado o comprimento das narrativas (número de palavras).
Textos extremamente curtos ou excessivamente longos foram removidos com base em percentis, reduzindo ruído e melhorando o desempenho dos modelos de NLP.
Essa etapa foi fundamental para evitar viés e otimizar o treinamento do modelo.

📊 Análise Exploratória de Dados (EDA)
Durante a EDA foram analisados:

Distribuição de produtos financeiros
Tipos de reclamação (Issue e Sub‑issue)
Empresas com maior número de reclamações
Canais de envio (Web, telefone, outros)
Evolução temporal das reclamações
Tempo de envio da reclamação para a empresa

Insight relevante:
Mais de 90% das reclamações foram enviadas à empresa no mesmo dia, indicando eficiência operacional do processo de encaminhamento.

🏷️ Rotulagem de Sentimento
A rotulagem do sentimento foi realizada utilizando o VADER Sentiment Analyzer (NLTK) como heurística inicial.
Regra adotada:

compound <= -0.05: sentimento negativo
compound > -0.05: sentimento positivo

Essa abordagem é:

Reprodutível
Explicável
Amplamente aceita como baseline em NLP


🧪 Baseline Clássico
Foi implementado um modelo de referência utilizando:

TF‑IDF com uni‑gramas e bi‑gramas
Logistic Regression
Métrica principal: AUC

Esse baseline serve como ponto de comparação para avaliar os ganhos obtidos com o modelo de Deep Learning.

🧠 Modelo Deep Learning (Keras)
A arquitetura escolhida foi Embedding + Bidirectional LSTM (BiLSTM), adequada para textos longos e com dependência contextual.
Fluxo do modelo:

Texto
Tokenização e Padding
Embedding treinável
Bidirectional LSTM
Camada Dense com ReLU
Dropout
Camada de saída com Sigmoid

Configuração:

Função de perda: Binary Crossentropy
Otimizador: Adam
Métricas: Accuracy e AUC
Early Stopping para evitar overfitting


📈 Treinamento e Avaliação
O treinamento foi conduzido com validação estratificada.
Foram avaliados:

Classification report
Matriz de confusão
Curvas de loss e accuracy (treino vs validação)

O modelo apresentou comportamento estável, sem overfitting significativo.

📦 Estrutura do Projeto
Estrutura esperada do repositório:

KERAS_TECCHALLENGE (2).py
README.md
sentiment_analysis_cfpb.h5
tokenizer.pkl
requirements.txt


🚀 Tecnologias Utilizadas

Python
Pandas e NumPy
Matplotlib e Seaborn
NLTK
Scikit‑learn
TensorFlow / Keras
