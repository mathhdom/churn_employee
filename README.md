# Identificar colaboradores que podem deixar a empresa

O objetivo deste projeto é desenvolver um modelo de machine learning para prever se um colaborador de uma empresa deixará o emprego.. Com base nessas previsões, a empresa poderá identificar colaboradores em risco e implementar ações preventivas. 

# Dados

Os dados foram obtidos a partir de um dataset do kaggle, através do link abaixo:

- link: [https://www.kaggle.com/datasets/kmldas/hr-employee-data-descriptive-analytics/code]

# Análise Exploratória (EDA)

Balanceamento:
- A variável alvo está desbalanceada no dataset. Cerca de 76% dos colaboradores continuam na empresa, enquanto 24% já saíram.

Correlação:
- A matriz de correlação mostra que não há relações lineares fortes entre as variáveis independentes e a variável dependente ('left'). Portanto, algorítimos baseados em árvore podem captar relação não lineares, como o RandomForest

Nível de satisfação
- Avaliando os níveis de satisfação e comparando-os com a saída ou não dos colaboradores, é possível notar que colaboradores com nível de satisfação maior tendem a continuar na empresa, comprovado pelo teste de hipótese.
- O Teste de Mann-Whitney foi aplicado pois não se pode assumir normalidade na distribuição dos dados, além de considerar que o dataset é uma amostra limitada em um período de tempo. Portanto, não é possível afirmar que todo o dataset representa toda a população.

# Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- SciPy (teste não paramétrico)

# Modelagem

Escolha da métrica de desempenho:
- O objetivo é aumentar a performance do recall, visto que o problema de negócio ressalta a importância de prever corretamente as pessoas que irão sair da empresa para promover ações.
- É preferível mover ações em pessoas que não iriam deixar a empresa do que não promover ações em pessoas que realmente vão deixar a empresa.

Pré-Processamento:
- Variáveis nominais como Department foram codificadas com OneHotEncoder.
- A variável ordinal salary foi codificada respeitando sua hierarquia (“low”, “medium”, “high”).
- O método Nearmiss foi utilizado para balancear as classes reduzindo a classe majoritária
- O algoritmo K-Means foi aplicado para criar uma representação categória da variável satisfaction_level, baseando a escolha de 'k' pelo método do cotovelo

# Resultados

Modelo Inicial:
- Algoritmo: Random Forest.
- Acurácia: 94%
- Precision: 98%
- Recall: 76%
- ROC-AUC: 88%

Modelo Final (após otimizações):
- Algoritmo: Random Forest.
- Acurácia: 97%
- Precision: 91%
- Recall: 96%
- ROC-AUC: 96%

# Conclusão

O projeto alcançou seu objetivo, melhorando significativamente o recall do modelo final em comparação ao modelo inicial, permitindo classificar de forma eficiente potenciais colaboradores a deixarem a empresa para promover ações de mitigação.

Nota-se que o modelo entende que o departamento do colaborador não é relevante para uma pessoa deixar ou não a empresa.

A implementação de validações com dados reais é necessária para validar o impacto das ações preventivas sugeridas pelo modelo.

Talvez a aplicação de outros modelos podem trazer possíveis ganhos no desempenho, por exemplo o XGBoost, além da busca de novas variáveis.
