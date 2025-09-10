# MVP Machine Learning & Analytics - Predição de Rotatividade de Funcionários

## Descrição Geral

Este projeto desenvolve um modelo preditivo para análise de rotatividade de funcionários (employee attrition) utilizando técnicas de machine learning. O objetivo é identificar funcionários com maior probabilidade de deixar a empresa, permitindo que a organização tome medidas proativas de retenção de talentos.

O projeto utiliza o dataset **HR Analytics** que contém informações demográficas, profissionais e comportamentais de funcionários, incluindo variáveis como idade, salário, satisfação no trabalho, distância de casa, horas extras, entre outras características relevantes para a análise de rotatividade.

## Contexto Acadêmico

Este projeto faz parte do MVP (Minimum Viable Product) da **Pós-graduação em Ciência de Dados da PUC-RIO**, representando a aplicação prática de conhecimentos em machine learning e analytics para resolução de problemas reais de negócio.

## Objetivos

### Objetivo Principal
Desenvolver um modelo de classificação supervisionada capaz de prever se um funcionário irá deixar a empresa com base em suas características pessoais e profissionais.

### Objetivos Específicos
- Comparar diferentes algoritmos de machine learning para o problema
- Otimizar hiperparâmetros dos modelos mais promissores
- Implementar técnicas de balanceamento de dados para lidar com classes desbalanceadas
- Avaliar a eficácia de modelos ensemble vs. modelos individuais

## Fluxo do Notebook

### 1. **Descrição do Problema**
- Apresentação do dataset HR Analytics
- Definição de hipóteses sobre comportamentos que levam ao desligamento
- Caracterização como problema de classificação supervisionada

### 2. **Setup e Preparação**
- Importação de bibliotecas necessárias
- Definição de funções auxiliares para análise
- Carregamento e configuração inicial dos dados

### 3. **Replicação do MVP Anterior**
- Aplicação de processamentos baseados em análise exploratória prévia
- Saneamento dos dados (remoção de duplicatas, tratamento de valores nulos)
- Seleção de variáveis relevantes baseada em insights do EDA

### 4. **Pré-processamento**
- Filtragem de colunas relevantes: idade, nível do cargo, função, renda mensal, horas extras, opções de ações, anos com gerente atual
- Criação de variáveis dummy para categóricas
- Divisão em conjuntos de treino e teste (80/20)

### 5. **Comparativo de Modelos**
Teste sistemático de **63 combinações** entre:
- **7 Modelos:** Logistic Regression, Decision Tree, Random Forest, XGBoost, Naive Bayes, KNN, SVM
- **3 Técnicas de Escalonamento:** Sem escalonamento, MinMaxScaler, StandardScaler  
- **3 Estratégias de Balanceamento:** Sem balanceamento, SMOTE, Random Undersampling

### 6. **Otimização de Hiperparâmetros**
Otimização detalhada dos 3 melhores modelos usando GridSearchCV:
- **Naive Bayes** (sem balanceamento/escalonamento)
- **Random Forest** (com SMOTE e StandardScaler)
- **Logistic Regression** (sem balanceamento, com StandardScaler)

### 7. **Treinamento Completo e Avaliação**
- Treinamento dos modelos otimizados com dados completos
- Avaliação detalhada no conjunto de teste
- Análise de métricas e detecção de overfitting

### 8. **Modelo Ensemble**
- Implementação de VotingClassifier com majority voting
- Comparação entre ensemble e modelos individuais

### 9. **Conclusões e Recomendações**
- Seleção do melhor modelo baseado em métricas de performance
- Análise dos resultados e limitações encontradas

## Tecnologias Utilizadas

### Bibliotecas de Manipulação e Análise
- **pandas**: Manipulação e análise de dados estruturados
- **numpy**: Operações numéricas e arrays multidimensionais

### Visualização
- **matplotlib**: Criação de gráficos e visualizações básicas
- **seaborn**: Visualizações estatísticas avançadas

### Machine Learning
- **scikit-learn**: Algoritmos de ML, pré-processamento, métricas e validação
- **xgboost**: Algoritmo de gradient boosting otimizado
- **imbalanced-learn**: Técnicas de balanceamento de dados (SMOTE, undersampling)

### Ambiente de Desenvolvimento
- **ipykernel**: Suporte para Jupyter notebooks
- **scipy**: Funções científicas e estatísticas

## Resultados Alcançados

### Modelo Vencedor: Naive Bayes
O modelo **Naive Bayes** foi selecionado como a melhor solução, apresentando:

- **F1-Score:** 0.704 (melhor entre todos os modelos testados)
- **Acurácia:** 84.4%
- **Recall:** 69.7% (segundo melhor)
- **Precisão:** 70.4%
- **Overfitting:** Baixo ou desprezível

### Comparativo de Performance
| Modelo | F1-Score | Acurácia | Recall | Precisão |
|--------|----------|----------|---------|----------|
| **Naive Bayes** | **0.704** | **0.844** | 0.697 | 0.704 |
| Ensemble | 0.696 | 0.858 | 0.674 | 0.696 |
| Random Forest | 0.688 | 0.801 | **0.724** | 0.688 |
| Logistic Regression | 0.661 | 0.862 | 0.633 | 0.661 |

### Principais Insights
- **Desbalanceamento:** Todos os modelos apresentaram melhor performance para prever funcionários que permanecem na empresa
- **Recall Elevado:** O modelo consegue identificar ~70% dos funcionários que realmente deixarão a empresa
- **Estabilidade:** Ausência de overfitting, indicando boa capacidade de generalização
- **Simplicidade:** O modelo mais simples (Naive Bayes) superou modelos mais complexos

## Instruções de Uso

### Pré-requisitos
```bash
# Clone o repositório
git clone <url-do-repositorio>
cd pucrio-mvp-machine-learning
```

### Instalação de Dependências
```bash
# Instalar as dependências listadas em requirements.txt
pip install -r requirements.txt
```

### Execução
1. **Google Colab (Recomendado):**
   - Clique no badge "Open in Colab" no início do notebook
   - Execute as células sequencialmente

2. **Jupyter Local:**
   ```bash
   # Iniciar Jupyter
   jupyter notebook MVP_MACHINE_LEARNING.ipynb
   ```

3. **Ambiente Virtual (Opcional):**
   ```bash
   # Criar ambiente virtual
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   # ou
   venv\Scripts\activate     # Windows
   
   # Instalar dependências
   pip install -r requirements.txt
   ```

### Dataset
O dataset é carregado automaticamente via URL no notebook. Não é necessário download manual.

### Estrutura de Arquivos
```
pucrio-mvp-machine-learning/
├── MVP_MACHINE_LEARNING.ipynb    # Notebook principal com toda a análise
├── requirements.txt              # Dependências do projeto
└── README.md                    # Documentação (este arquivo)
```

---

