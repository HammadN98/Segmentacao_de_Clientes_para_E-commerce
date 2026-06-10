# 🛍️ Customer Segmentation — E-commerce Behavior

> Segmentação não supervisionada de clientes de e-commerce usando K-Means, PCA e análise estatística multivariada, com foco em geração de personas acionáveis para estratégias de CRM.

<br>

## 📌 Visão Geral

Este projeto aplica técnicas de **Machine Learning não supervisionado** sobre dados reais de comportamento de clientes em e-commerce, com o objetivo de identificar perfis distintos de consumidores e traduzir esses perfis em **estratégias de marketing personalizadas**.

O pipeline cobre desde a análise exploratória até a validação estatística dos clusters, passando pela comparação de três algoritmos de clustering e justificativa técnica da escolha do modelo final.

<br>

## 📊 Visualizações em Destaque

### Radar de Perfis dos Clusters
> Cada eixo representa uma dimensão do comportamento do cliente (normalizada). A área do polígono revela o "tipo" de cliente de cada cluster.

*(inserir print do gráfico radar aqui)*

---

### Distribuição dos Clusters via PCA
> Redução para 2 dimensões com variância explicada exibida nos eixos. Clusters visualmente separados validam a qualidade da segmentação.

*(inserir print do scatter PCA aqui)*

---

### Heatmap de Correlação
> Análise de relacionamento entre variáveis antes da modelagem — etapa essencial para entender o que diferencia os clientes.

*(inserir print do heatmap aqui)*

<br>

## 🧱 Estrutura do Projeto

```
📁 projeto
├── 📓 notebook.ipynb       # Pipeline completo comentado
├── 📄 README.md            # Este arquivo
└── 📁 dados/
    └── E-commerce_CustomerBehavior.csv
```

<br>

## 🔄 Pipeline

```
Carregamento dos Dados
        ↓
Análise Exploratória (EDA)
  • Histogramas com boxplot marginal
  • Boxplots por variável categórica
  • Heatmap de correlação
        ↓
Limpeza & Pré-processamento
  • Remoção de nulos e duplicatas
  • Análise de outliers
  • StandardScaler nas variáveis numéricas
        ↓
K-Means — Variáveis Numéricas
  • Método do Cotovelo (K=4)
  • Silhouette Score: 0.55
        ↓
Comparação de Algoritmos
  • K-Means  → Silhouette: 0.547
  • DBSCAN   → Silhouette: 0.696*
  • Agglomerative → Silhouette: 0.713
  • ✅ K-Means escolhido por interpretabilidade e cobertura total
        ↓
Validação de Estabilidade
  • Perturbação gaussiana (100 iterações)
  • ARI médio: 0.616 ± 0.000
        ↓
K-Means — Todas as Variáveis (K=7)
  • Encoding ordinal: Membership Type, Satisfaction Level
  • Encoding booleano: Discount Applied
  • One-Hot: Gender, City
  • Silhouette Score: > 0.70
        ↓
Análise dos Clusters
  • Boxplots por variável numérica
  • Sunburst por variável categórica
  • Médias e medianas por cluster
        ↓
Validação Estatística
  • ANOVA (variáveis numéricas): todas p < 0.05
  • Qui-Quadrado (variáveis categóricas): todas p < 0.05
        ↓
Perfis & Estratégias de CRM
  • 7 personas definidas
  • Campanhas personalizadas por cluster
  • Gráfico Radar de perfis
```

<br>

## 🤖 Comparação de Algoritmos

| Algoritmo | Clusters | Silhouette | Cobertura | Escolhido |
|-----------|----------|------------|-----------|-----------|
| **K-Means** | 7 | 0.547 | 100% | ✅ |
| DBSCAN | 9 + ruído | 0.696* | 98.4% | ❌ |
| Agglomerative (Ward) | 7 | 0.713 | 100% | ❌ |

> *Silhouette do DBSCAN calculado excluindo os 4 pontos classificados como ruído, o que pode superestimar a métrica.

**Por que K-Means?** Apesar do menor Silhouette Score, foi escolhido pela combinação de: interpretabilidade dos centroides, cobertura total da base, estabilidade em produção e facilidade de re-segmentação mensal automatizada.

<br>

## 👥 Os 7 Perfis de Clientes

| Cluster | Nome | Gasto Médio | Frequência | Satisfação | Membership |
|---------|------|-------------|------------|------------|------------|
| 6 | 🏆 VIP Premium | R$ 1.492 | Alta | ⭐ 4.9 | Gold |
| 3 | 💎 Engajado Leal | R$ 1.340 | Alta | ⭐ 4.7 | Gold |
| 2 | 🌟 Alto Valor | R$ 1.151 | Média | ⭐ 4.5 | Gold |
| 1 | 📈 Frequente Médio | R$ 805 | Alta | ⭐ 4.2 | Silver |
| 4 | ⏳ Inconstante Jovem | R$ 704 | Baixa | ⭐ 4.0 | Silver |
| 5 | 🔄 Moderado Sênior | R$ 550 | Baixa | ⭐ 3.6 | Bronze/Silver |
| 0 | 💤 Ocasional | R$ 448 | Média | ⭐ 3.2 | Bronze |

<br>

## 🎯 Estratégias de CRM por Cluster

| Cluster | Objetivo | Ação Principal |
|---------|----------|----------------|
| 6 — VIP Premium | Manter satisfação | Experiências exclusivas + acesso antecipado |
| 3 — Engajado Leal | Aumentar lifetime value | Clube de assinatura + eventos VIP |
| 2 — Alto Valor | Reforçar fidelidade | Ofertas premium personalizadas |
| 1 — Frequente Médio | Elevar ticket médio | Cross-selling + programa de cashback |
| 4 — Inconstante Jovem | Aumentar frequência | E-mails de reativação + frete grátis |
| 5 — Moderado Sênior | Estimular volume | Promoções de quantidade + benefícios VIP acessíveis |
| 0 — Ocasional | Aumentar recorrência | Desconto por tempo limitado + lembretes personalizados |

<br>

## 🛠️ Tecnologias

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)

| Biblioteca | Uso |
|------------|-----|
| `pandas` | Manipulação e análise dos dados |
| `scikit-learn` | K-Means, PCA, DBSCAN, Agglomerative, Silhouette |
| `plotly` | Visualizações interativas (histogramas, radar, scatter PCA) |
| `scipy` | Testes estatísticos ANOVA e Qui-Quadrado |
| `seaborn / matplotlib` | Gráfico de Silhouette e análises complementares |
| `numpy` | Operações numéricas e perturbação gaussiana |

<br>

## 📂 Como Executar

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/customer-segmentation.git
cd customer-segmentation

# 2. Instale as dependências
pip install pandas numpy scikit-learn plotly seaborn matplotlib scipy

# 3. Abra o notebook
jupyter notebook notebook.ipynb
```

> Os dados são carregados diretamente via URL pública — nenhum download manual necessário.

<br>

## 📈 Principais Resultados

- **7 perfis** de clientes identificados com separação estatisticamente significativa (ANOVA e Qui-Quadrado, p < 0.05 em todas as variáveis)
- **Silhouette Score > 0.70** após inclusão de variáveis categóricas codificadas
- **Estabilidade comprovada**: ARI de 0.616 sob perturbação gaussiana de 5% em 100 iterações
- **Cobertura total** da base de clientes — nenhum cliente sem segmento
- Personas **diretamente acionáveis** para campanhas de CRM segmentadas

<br>

## 👤 Autor

**Seu Nome**
Analista de Dados | 1 ano de experiência

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/seu-perfil)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/seu-usuario)

<br>

---

<p align="center">
  <i>Este projeto faz parte do meu portfólio de Ciência e Análise de Dados.<br>
  Feedbacks são bem-vindos — sinta-se à vontade para abrir uma issue ou me chamar no LinkedIn.</i>
</p>
