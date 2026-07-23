# Competição: Classificação de Documentos Jurídicos

Solução desenvolvida para a classificação automática de documentos jurídicos em uma competição do Kaggle.

## 🛠️ Tecnologias e Bibliotecas Utilizadas

* **Linguagem:** Python 3.12+

* **Manipulação de Dados:** `pandas`, `numpy`

* **Processamento de Linguagem Natural:** `scikit-learn` (`TfidfVectorizer`, `TruncatedSVD`)

* **Machine Learning:** `lightgbm` (`LGBMClassifier`), `scikit-learn` (`StratifiedKFold`, `f1_score`)

---

## Preparação dos dados

### 1. Tratamento de Valores Ausentes

Tratamento de valores ausentes em colunas textuais (`text_clean` e `text_head_30`) para evitar erros durante a vetorização.

---

### 2. Engenharia de Features

Criação de novas features (`score_ARE`, `score_Acordao`, `score_Despacho`, `score_RE` e `score_Sentenca`) baseados nas features com sinal mais forte em cada classe.

---

### 3. Vetorização e Embeddings

Para representar o contexto dos textos, foram gerados embeddings para os campos `text_clean` e `text_head_30` utilizando a combinação de **TF-IDF** e **TruncatedSVD** para redução de dimensionalidade.

---

## ⚙️ Treinamento e Validação

### Modelo

Foi utilizado o **LightGBM Classifier** com hiperparâmetros ajustados.

### Estratégia de Validação

O desempenho do modelo foi medido utilizando **Stratified K-Fold Cross-Validation (5 folds)**, garantindo a mesma proporção de classes em cada fold, avaliado com a métrica **Macro F1-Score**.

## 🚀 Como Executar

1. **Clone o repositório:**
```bash
git clone https://github.com/LuisFSouza/dswa-2026
```

2. **Entre na pasta da competição:**
```bash
cd competicao-3
```

3. **Instale as dependências:**
```bash
pip install pandas numpy lightgbm scikit-learn
```

4. **Adicione os dados:**
Certifique-se de colocar os arquivos `train.csv` e `test.csv` dentro da pasta `dataset/`.

5. **Execute o Jupyter Notebook:**
Abra o notebook da solução e rode todas as células para gerar o arquivo `submission.csv`.