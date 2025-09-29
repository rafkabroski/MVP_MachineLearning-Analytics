🏥 MVP - Previsão de Readmissão Hospitalar em 30 Dias

📋 Sobre o Projeto
Este projeto desenvolve um modelo de Machine Learning para prever readmissões hospitalares em até 30 dias após a alta, utilizando dados clínicos e demográficos de pacientes. Desenvolvido como parte da disciplina Sprint: Machine Learning & Analytics da PUC-Rio Online.

🎯 Status do Projeto: Concluído ✅

📊 Contexto do Problema

Problema de Saúde Pública
•	Readmissões em 30 dias: Indicador crítico de qualidade em saúde
•	Custos: Estimados em US$ 17 bilhões anualmente apenas nos EUA
•	Impacto: 20% dos pacientes são readmitidos dentro de 30 dias
•	Oportunidade: Identificação precoce permite intervenções proativas

Valor para o Negócio
•	Redução de custos: Potencial economia de 15-20% em readmissões evitáveis
•	Melhoria da qualidade: Cuidado mais eficiente e personalizado
•	Otimização de recursos: Alocação direcionada para pacientes de alto risco

🗂️ Dataset
Fonte
•	Repositório: UCI Machine Learning Repository
•	Período: 1999-2008
•	Abrangência: 130 hospitais dos Estados Unidos
•	Pacientes: +100,000 registros de pacientes diabéticos
Características Principais

🛠️ Metodologia
Tipo de Problema
•	Classificação: Binária (readmitido vs não readmitido em ≤30 dias)
•	Supervisionado: Com labels históricos
•	Área: Saúde/Sistemas de Informação Hospitalar

Abordagem Técnica
python
FLUXO_DE_TRABALHO = {
    "1. Pré-processamento": [
        "Limpeza de dados missing",
        "Codificação one-hot variáveis categóricas", 
        "Padronização variáveis numéricas",
        "Balanceamento com SMOTE"
    ],
    "2. Modelagem": [
        "Baseline (Dummy Classifier)",
        "Regressão Logística",
        "Random Forest (modelo principal)"
    ],
    "3. Otimização": [
        "RandomizedSearchCV com validação cruzada",
        "Otimização de hiperparâmetros",
        "Validação em dataset de teste"
    ]
}


📈 Resultados

Performance do Modelo Final
Métrica	Valor	Interpretação
AUC-ROC	0.782	Boa capacidade discriminativa
Acurácia	0.751	Precisão geral satisfatória
Sensibilidade	0.721	Detecta 72% dos casos de alto risco
F1-Score	0.723	Balanceamento entre precisão e recall

Comparação de Modelos
Modelo	AUC-ROC	Tempo Treino (s)
Random Forest (Otimizado)	0.782	186.4
Logistic Regression	0.698	45.2
Baseline (Dummy)	0.500	12.1

Features Mais Importantes
1.	time_in_hospital (18.2%) - Tempo de internação
2.	num_lab_procedures (15.8%) - Número de procedimentos
3.	num_medications (12.4%) - Quantidade de medicamentos
4.	number_inpatient (11.2%) - Internações anteriores
5.	number_diagnoses (9.7%) - Número de diagnósticos


🚀 Como Executar

Pré-requisitos
bash
# Bibliotecas principais (instaladas automaticamente no Colab)
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=1.0.0
matplotlib>=3.5.0
seaborn>=0.11.0
imbalanced-learn>=0.8.0
scikit-plot>=0.3.0

Execução no Google Colab
1.	Acesse o Notebook:
python
# O notebook está disponível no Google Colab
# Todos os dados são baixados automaticamente via URL

2.	Execute sequencialmente:
bash
# 1. Configuração do ambiente (2.1)
# 2. Carga e análise dos dados (3.1) 
# 3. Pré-processamento (5.1)
# 4. Modelagem e otimização (6.1, 7.1)
# 5. Avaliação final (8.1)

3.	Resultados: Gráficos e métricas são gerados automaticamente
Estrutura do Código
python
# Pipeline principal
pipeline = ImbPipeline([
    ("preprocessamento", preprocess),      # Limpeza e transformação
    ("balanceamento", SMOTE()),           # Tratamento desbalanceamento
    ("modelo", RandomForestClassifier())  # Algoritmo preditivo
])

📁 Estrutura do Projeto
text
mvp-readmissao-hospitalar/
│
├── 📓 MVP_Previsao_Readmissao_Hospitalar.ipynb  # Notebook principal
├── 📊 data/
│   └── dataset_diabetes/                        # Dados (baixado via URL)
├── 🔧 models/
│   ├── best_readmission_model.pkl              # Modelo treinado
│   └── preprocessor.pkl                        # Pré-processador
├── 📈 results/
│   ├── feature_importance.png                  # Importância das variáveis
│   ├── confusion_matrix.png                    # Matriz de confusão
│   └── roc_curve.png                          # Curva ROC
└── 📋 requirements.txt                         # Dependências

🧪 Experimentação e Reprodutibilidade
Configuração de Ambiente
python
# Seeds para reprodutibilidade total
SEED = 42
np.random.seed(SEED)
random.seed(SEED)

# Configurações específicas
train_test_split(random_state=SEED)
RandomForestClassifier(random_state=SEED)
SMOTE(random_state=SEED)
Validação
•	Validação Cruzada: 5-folds estratificados
•	Métricas: AUC-ROC, F1-Score, Sensibilidade, Especificidade
•	Split: 80% treino, 20% teste (estratificado)

📊 Análises e Insights
Principais Descobertas
1.	Fatores de Risco: Tempo de internação e polifarmácia são preditores fortes
2.	Perfil de Alto Risco: Pacientes idosos com múltiplas comorbidades
3.	Desbalanceamento: Apenas 11.4% são readmitidos (classe minoritária)

Visualizações Incluídas
•	📉 Distribuição da variável target
•	📊 Matriz de correlação entre features
•	🎯 Curva ROC e AUC
•	📋 Matriz de confusão
•	🔥 Importância das features

⚠️ Limitações e Considerações
Limitações Técnicas
1.	Dados Temporais: Dataset de 1999-2008 (práticas podem ter mudado)
2.	Desbalanceamento: Classe minoritária pequena (11.4%)
3.	Variáveis Limitadas: Faltam dados vitais e socioeconômicos
4.	Especificidade: Apenas pacientes diabéticos
Considerações Éticas
•	Privacidade: Dados anonimizados do repositório público
•	Viés: Potencial viés em variáveis demográficas
•	Uso Clínico: Modelo para apoio à decisão, não substitui julgamento médico

🚀 Próximos Passos
Melhorias Técnicas
1.	Novos Algoritmos: Testar XGBoost, LightGBM, Redes Neurais
2.	Engenharia de Features: Criar variáveis derivadas e interações
3.	Técnicas Avançadas: SHAP para explicabilidade, AutoML
Expansão do Projeto
1.	Dados em Tempo Real: Integração com prontuário eletrônico
2.	Dashboard: Interface para equipes médicas
3.	Validação Externa: Teste em dataset independente
4.	Sistema de Scoring: Calculadora de risco clínico

📄 Licença e Referências
Licença
Este projeto é para fins educacionais. O dataset é de uso público para pesquisa.
Referências Principais
1.	UCI Machine Learning Repository - Diabetes Dataset
2.	Scikit-learn Documentation
3.	Imbalanced-learn Documentation
4.	Artigos sobre readmissão hospitalar e machine learning

