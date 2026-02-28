# TechChallenge05
Trabalho Final da Pós Tech - Data Analytics 

Análise de Sentimento e Dores em Reclamações Financeiras
Classificação de Deep Learning e Insights Acionáveis para o Setor FinanceiroEste repositório contém o projeto desenvolvido para o Tech Challenge, focado na aplicação de técnicas de Processamento de Linguagem Natural (NLP) e
Deep Learning para analisar reclamações de consumidores sobre produtos e serviços financeiros.

# Visão Geral e Motivação
Este projeto aborda o desafio de compreender o sentimento e as principais dores expressas em um vasto volume de reclamações de consumidores do setor financeiro. A capacidade de classificar automaticamente o sentimento (positivo/negativo) e identificar temas recorrentes de insatisfação é crucial para instituições financeiras, órgãos reguladores e equipes de atendimento ao cliente.

* Por que é útil?
     - Bancos: Permite identificar rapidamente falhas em produtos/serviços, priorizar melhorias, reduzir o churn de clientes e otimizar a alocação de recursos no atendimento.
     - Atendimento ao Cliente: Facilita a triagem automática de reclamações, direcionando casos críticos para agentes especializados e melhorando o tempo de resposta.
     - Gestão de Risco e Conformidade: Ajuda a detectar padrões de reclamações que podem indicar problemas regulatórios, fraudes ou riscos operacionais.

Objetivos do Projeto:
O projeto foi estruturado em fases, com foco na construção de um pipeline robusto de NLP e Deep Learning:

1. Criação da Variável Alvo (Sentimento)
Desafio: O dataset original não possui rótulos de sentimento explícitos.
Solução: Implementação de uma estratégia de weak supervision (Estratégia A), utilizando o desfecho do atendimento como proxy para o sentimento. Reclamações são classificadas como Positiva ou Negativa com base nas colunas company_response_to_consumer, timely_response_ e consumer_disputed_. Casos ambíguos são descartados para garantir a qualidade dos rótulos

2. Pré-processamento de Texto
Desafio: Narrativas de reclamação em idioma misto (Português/Inglês) e com ruído.
Solução: Aplicação de técnicas de limpeza e normalização, incluindo:
      Regex: Remoção de pontuações, caracteres especiais, URLs, e normalização de espaços.
      Stop Words: Remoção de palavras irrelevantes em ambos os idiomas.
      Normalização: Conversão para minúsculas.
      Lematização/Stemming: Aplicação seletiva para reduzir a dimensionalidade, considerando a natureza mista do texto.

3. Vetorização e Representação de Texto
Desafio: Transformar texto em formato numérico para modelos de Deep Learning.
Solução: Utilização de Tokenização e Embeddings (treináveis ou pré-treinados) para representar as palavras em um espaço vetorial denso. Para a análise de dores, também é explorado o TF-IDF com n-grams.

4. Modelagem de Deep Learning para Classificação de Sentimento
Desafio: Construir um modelo robusto para classificar sentimentos em um dataset desbalanceado.
Solução: Treinamento de um modelo de Deep Learning baseado em arquiteturas LSTM/GRU com camadas de Embedding.
Tratamento de Desbalanceamento: Utilização de class_weight durante o treinamento e ajuste de threshold na fase de predição para otimizar o desempenho na classe minoritária (positiva).
Avaliação: Performance avaliada com métricas adequadas para classes desbalanceadas, como F1-score, Recall da classe positiva, PR-AUC (Area Under the Precision-Recall Curve) e Matriz de Confusão.

5. Análise das Principais Dores dos Clientes por Categoria de Produto
Desafio: Extrair insights acionáveis sobre os problemas mais recorrentes.
Solução: Análise focada nas reclamações classificadas como Negativas, gerando visualizações como:
Nuvem de Palavras: Para identificar os termos mais frequentes.
Gráficos de Frequência: Para os issues e sub_issues mais comuns, detalhados por categoria de produto.
TF-IDF com n-grams: Para identificar temas e expressões-chave (ex: "cobrança indevida").


# Como Reproduzir o Projeto
Para reproduzir este projeto, siga os passos abaixo:
1. Configuração do Ambiente
Certifique-se de ter o Python (versão 3.8+) instalado.
 
# Crie um ambiente virtual (recomendado)
python -m venv venv source venv/bin/activate  # No Windows: .\venv\Scripts\activate

## Instale as dependências
pip install -r requirements.txt

2. Estrutura de Pastas
Crie a estrutura de pastas conforme descrito na seção "Estrutura do Repositório".

3. Download do Dataset
Coloque o arquivo complaints.csv (ou a amostra complaints_sample_XXXXX.csv) na pasta data/raw/.

4. Execução dos Notebooks
Os notebooks na pasta notebooks/ guiam você por todo o pipeline do projeto.

O notebook contém seções dedicadas à geração de:

Nuvem de Palavras: Para reclamações negativas gerais e, opcionalmente, por produto.
Gráficos de Frequência: Para os issues mais recorrentes, com a possibilidade de filtrar por product.

Resultados
O modelo de Deep Learning demonstrou capacidade de aprender padrões nas narrativas, mesmo com o desafio do desbalanceamento extremo e a natureza do rótulo proxy.

ContribuiçãoContribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

