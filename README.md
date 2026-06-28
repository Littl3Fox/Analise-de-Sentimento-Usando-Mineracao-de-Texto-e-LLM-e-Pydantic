# Mineração de Textos com Embeddings, HDBSCAN e LLM

Projeto desenvolvido para a disciplina de **Mineração de Textos** da Especialização em **Data Science e Inteligência Artificial** da **Faculdade Senac DF**.  

Alunos:
*   Denilson Alves Oliveira
*   Anderson Ferreira
*   Ítalo Timbó Santos
*   Artur Romão Soares Barbosa
   
**OBS: Recomendo baixar o PDF do notebook executado e dar zoom**

O objetivo do projeto é analisar comentários do YouTube sobre um debate presidencial utilizando técnicas de Processamento de Linguagem Natural (PLN), aprendizado de máquina não supervisionado e Inteligência Artificial Generativa.

---

# Objetivos

- Coletar comentários do YouTube utilizando a API oficial.
- Realizar Análise Exploratória dos Dados (EDA).
- Aplicar pré-processamento textual.
- Gerar embeddings semânticos utilizando Sentence-BERT.
- Reduzir a dimensionalidade dos embeddings com UMAP.
- Agrupar comentários semanticamente semelhantes utilizando HDBSCAN.
- Avaliar a qualidade dos agrupamentos.
- Rotular automaticamente os clusters utilizando o Gemini.
- Validar as respostas do LLM utilizando Pydantic.
- Gerar insights sobre os principais temas discutidos.

---

# Fluxo do Projeto

```text
Coleta dos comentários
        │
        ▼
Análise Exploratória (EDA)
        │
        ▼
Pré-processamento
        │
        ▼
Sentence-BERT
        │
        ▼
UMAP
        │
        ▼
HDBSCAN
        │
        ▼
Avaliação dos Clusters
        │
        ▼
Gemini + Pydantic
        │
        ▼
Insights
```

---

# Tecnologias utilizadas

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- WordCloud
- Sentence Transformers
- UMAP
- HDBSCAN
- Scikit-Learn
- Google Generative AI (Gemini)
- Pydantic

---

# Estrutura do Projeto

```text
📦 Projeto
│
├── 📁 embeddings
│   ├── embeddings.npy
│   ├── embeddings_umap_5.npy
│   ├── embeddings_umap_10.npy
│   └── embeddings_umap_15.npy
│
├── 📁 json
│   └── respostas geradas pelo Gemini
│
├── 📁 notebook
│   └── mineracao_Texto_analise_sentimentos.ipynb
│
├── 📁 tabelas
│   └──  datasets

├── 📄 PDF do notebook executado
│
└── 📄 README.md
```

---

# Metodologia

## 1. Coleta dos dados

Os comentários foram obtidos por meio da **YouTube Data API v3**, utilizando um vídeo de um debate presidencial de 2022 da Band primerio turno.

---

## 2. Análise Exploratória (EDA)

Foram analisadas características como:

- distribuição temporal dos comentários;
- distribuição de curtidas;
- quantidade de palavras;
- quantidade de caracteres;
- comentários duplicados;
- frequência de palavras;
- nuvem de palavras.

---

## 3. Pré-processamento

As seguintes etapas foram aplicadas:

- remoção de URLs;
- remoção de menções;
- remoção de hashtags;
- remoção de espaços extras;
- remoção de quebras de linha;
- conversão para letras minúsculas;
- normalização da pontuação;
- remoção de comentários muito pequenos.

As stopwords foram mantidas, pois o projeto utiliza **embeddings contextuais**, que consideram o contexto completo da sentença.

---

## 4. Embeddings

Foi utilizado o modelo:

**Sentence-BERT (paraphrase-multilingual-MiniLM-L12-v2)**

O modelo gera representações vetoriais semânticas dos comentários em português.

---

## 5. Redução de dimensionalidade

Foi utilizado o algoritmo **UMAP** para reduzir a dimensionalidade dos embeddings.

Foram avaliadas representações em:

- 5 dimensões;
- 10 dimensões;
- 15 dimensões.

---

## 6. Clusterização

Foi utilizado o algoritmo **HDBSCAN**.

As configurações foram avaliadas utilizando:

- Silhouette Score;
- percentual de ruído;
- inspeção qualitativa dos clusters.

As configurações com **7 e 9 clusters** apresentaram o melhor equilíbrio entre qualidade dos agrupamentos e interpretabilidade.

---

## 7. LLM + Pydantic

Cada cluster foi enviado ao **Gemini**, que retornou informações estruturadas contendo:

- tema principal;
- categoria;
- sentimento predominante;
- intensidade;
- alinhamento político expresso;
- nível de confiança.

Todas as respostas foram validadas utilizando **Pydantic**, garantindo conformidade com o esquema definido.

---

# Como executar

1. Clone o repositório.

```bash
git clone <url-do-repositorio>
```
2. Abra o notebook localizado na pasta **notebook**.  
3. Execute todas as células do notebook.   
4. Informe sua chave da API do YouTube quando solicitado.  
5. Informe sua chave da API Gemini quando solicitado.  



---

# Segurança

As chaves das APIs **não são armazenadas no repositório**.

Durante a execução, as chaves são solicitadas utilizando `getpass()` e armazenadas apenas temporariamente em variáveis de ambiente.

---

# Autor

Projeto desenvolvido como trabalho da disciplina de **Mineração de Textos** da Especialização em **Data Science e Inteligência Artificial** da **Faculdade Senac DF**.
