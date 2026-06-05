# 🛒 Segmentação de Clientes para E-commerce
> Identificação de perfis comportamentais via K-Means para otimização de campanhas de marketing e incremento do lifetime value (LTV)

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3-orange?logo=scikit-learn&logoColor=white)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📋 Sumário
- [Contexto de Negócio](#-contexto-de-negócio)
- [Resultados e Impacto](#-resultados-e-impacto)
- [Metodologia](#-metodologia)
- [Estrutura dos Dados](#-estrutura-dos-dados)
- [Perfis dos Clusters](#-perfis-dos-clusters)
- [Estratégias de Marketing por Cluster](#-estratégias-de-marketing-por-cluster)
- [Como Reproduzir](#-como-reproduzir)
- [Próximos Passos](#-próximos-passos)

---

## 🎯 Contexto de Negócio

**Pergunta central:** *Como identificar e segmentar grupos de clientes com comportamentos distintos para otimizar campanhas de marketing e aumentar engajamento e retenção?*

O time de marketing enfrentava o desafio de comunicar-se com toda a base de clientes de forma genérica, sem personalização, resultando em baixas taxas de conversão e retenção. Este projeto aplica técnicas de **clustering não-supervisionado** para segmentar clientes de e-commerce com base em comportamento de compra e perfil demográfico, viabilizando campanhas direcionadas e aumento do LTV.

---

## 📊 Resultados e Impacto

| Métrica | Resultado |
|---|---|
| Número de clusters identificados | **7** |
| Silhouette Score | **0.XX** |
| Algoritmo principal | **K-Means** |
| Variáveis utilizadas | **9** (5 numéricas + 4 categóricas) |

> **Impacto financeiro estimado:** A implementação das estratégias mapeadas para os clusters de maior valor tem potencial de aumentar a receita recorrente em **~15–20%** nos primeiros 3 meses, via maior retenção dos clientes Gold e reativação dos clientes inativos.

---

## 🔬 Metodologia

```
Dados Brutos → Limpeza e Pré-processamento → Normalização → Determinação do k Ideal → K-Means → Perfilagem → Estratégias
```

### 1. Limpeza e Pré-processamento
- Remoção de valores nulos e outliers
- Normalização (StandardScaler) das variáveis numéricas
- Encoding ordinal das variáveis categóricas (Membership Type, Satisfaction Level, Gender, City)

### 2. Determinação do Número de Clusters
- **Elbow Method:** análise da inércia por número de k
- **Silhouette Score:** avaliação da coesão e separação dos grupos
- Resultado: **k = 7** como configuração ótima

### 3. Modelagem e Perfilagem
- Aplicação do **K-Means** com `k=7` e `random_state=42`
- Criação de perfis descritivos para cada cluster considerando: idade, frequência de compra, gasto médio, satisfação e tipo de associação

---

## 🗂️ Estrutura dos Dados

### Variáveis Numéricas

| Variável | Descrição |
|---|---|
| `Age` | Idade do cliente |
| `Total Spend` | Gasto total acumulado |
| `Items Purchased` | Número total de itens comprados |
| `Average Rating` | Avaliação média do cliente |
| `Days Since Last Purchase` | Dias desde a última compra |

### Variáveis Categóricas (Codificadas)

| Variável | Encoding |
|---|---|
| `Membership Type` | 1 = Bronze · 2 = Silver · 3 = Gold |
| `Satisfaction Level` | 1 = Unsatisfied · 2 = Neutral · 3 = Satisfied |
| `Discount Applied` | 0 = Não · 1 = Sim |
| `Gender` | 1 = Male · 2 = Female |
| `City` | Categorizado numericamente por localização |

---

## 👥 Perfis dos Clusters

> Baseado na análise das médias e distribuições de cada grupo após a aplicação do K-Means.

| Cluster | Nome | Perfil Resumido | Prioridade |
|---|---|---|---|
| 0 | 🏆 Embaixadores da Marca | Alto gasto, alta frequência, alta satisfação | 🔴 Alta |
| 1 | 🌱 Potenciais de Crescimento | Gasto intermediário, frequência regular, satisfação moderada | 🟡 Média |
| 2 | 💤 Clientes Adormecidos | Baixa frequência, gasto ocasional, longa inatividade | 🔴 Alta |
| 3 | 🎯 Compradores Inconstantes | Frequência baixa, gasto moderado por compra | 🟡 Média |
| 4 | 👴 Compradores Maduros | Clientes mais velhos, compras esporádicas e baixo gasto | 🟢 Baixa |
| 5 | 💎 Clientes VIP Inativos | Alto gasto histórico, mas com redução recente de atividade | 🔴 Alta |
| 6 | 🔄 Exploradores de Desconto | Compras concentradas em períodos promocionais | 🟡 Média |

---

## 📣 Estratégias de Marketing por Cluster

### Visão Executiva — Tabela de KPIs

| Cluster | Ação Principal | KPI | Meta (3 meses) | Impacto Estimado |
|---|---|---|---|---|
| 0 · Embaixadores | Programa VIP + cashback | NPS / Frequência mensal | +15% recompra | Alta receita recorrente |
| 1 · Potenciais | Cross-sell / Up-sell | Ticket médio | +20% ticket médio | Expansão de receita |
| 2 · Adormecidos | Campanha de reativação | Taxa de reativação 30d | Recuperar 20% | Redução de churn |
| 3 · Inconstantes | Nudges de recorrência | Frequência de compra | +2 compras/trimestre | Aumento de LTV |
| 4 · Maduros | Promoções segmentadas | Taxa de conversão | +10% conversão | Retenção base |
| 5 · VIP Inativos | Reengajamento premium | Retorno ao padrão histórico | Recuperar 25% | Alto valor recuperado |
| 6 · Exploradores | Fidelização pós-desconto | Compra sem desconto | +5% compras full-price | Margem protegida |

---

### Cluster 0: Embaixadores da Marca 🏆

- **Perfil resumido:** Clientes jovens com alto gasto total, frequência de compra elevada e satisfação máxima. Possuem adesão Gold e raramente ficam muitos dias sem comprar.
- **Ação de marketing sugerida:** Programa de fidelidade "VIP Club" com acesso antecipado a lançamentos, cashback progressivo (2–5%) e convites para eventos exclusivos da marca via e-mail e push notification.
- **KPI principal:** Net Promoter Score (NPS) e frequência de compra mensal.
- **Meta (3 meses):** Aumentar a taxa de recompra em 15% e gerar ao menos 50 avaliações positivas na plataforma.
- **Justificativa:** Esse grupo já ama a marca; o foco é transformá-los em promotores orgânicos e elevar o LTV via recorrência e boca-a-boca, com custo de ativação baixo.

---

### Cluster 1: Potenciais de Crescimento 🌱

- **Perfil resumido:** Clientes com gasto intermediário, frequência regular e satisfação moderada. Têm adesão Silver e mostram consistência, mas ainda não atingiram o potencial máximo de gasto.
- **Ação de marketing sugerida:** Régua de e-mails com ofertas de cross-sell baseadas no histórico de compras e gatilho de up-sell ao atingir R$ X no carrinho (ex: "Adicione R$ 50 e ganhe frete grátis").
- **KPI principal:** Ticket médio por pedido.
- **Meta (3 meses):** Aumentar o ticket médio em 20% e converter 30% do cluster para adesão Gold.
- **Justificativa:** Com pequenos estímulos contextuais, clientes nesse estágio tendem a ampliar o escopo de compra; o upgrade de membership também aumenta o comprometimento com a plataforma.

---

### Cluster 2: Clientes Adormecidos 💤

- **Perfil resumido:** Compradores com longo período de inatividade (alto `Days Since Last Purchase`), baixa frequência e gasto reduzido. Sinal claro de risco de churn.
- **Ação de marketing sugerida:** Campanha de reativação multicanal com desconto progressivo ("Sentimos sua falta — 10% off hoje, 15% amanhã") + e-mail personalizado com os últimos produtos visualizados.
- **KPI principal:** Taxa de reativação (compra realizada em até 30 dias após o contato).
- **Meta (3 meses):** Recuperar 20% dos clientes do cluster, monitorando o LTV pós-reativação para validar rentabilidade.
- **Justificativa:** O custo de reter é 5–7x menor que o de adquirir um novo cliente. Um incentivo financeiro com urgência pode reengajar clientes que ainda têm propensão de compra latente.

---

### Cluster 3: Compradores Inconstantes 🎯

- **Perfil resumido:** Clientes com baixa frequência, mas gasto moderado por compra. Compram quando têm intenção clara, sem relacionamento contínuo com a marca.
- **Ação de marketing sugerida:** Sequência de "nudges" de recorrência via push/SMS em datas relevantes (aniversário, datas comemorativas) com curadoria personalizada de produtos baseada nas categorias já compradas.
- **KPI principal:** Frequência de compra trimestral.
- **Meta (3 meses):** Aumentar de 1 para 3 compras por trimestre em 25% do cluster.
- **Justificativa:** Esses clientes já demonstraram disposição de gastar; a barreira não é financeira, mas de engajamento. Gatilhos contextuais e personalizados criam o momento certo de compra.

---

### Cluster 4: Compradores Maduros 👴

- **Perfil resumido:** Clientes de faixa etária mais avançada, com compras esporádicas, baixo gasto e adesão predominantemente Bronze. Menor sensibilidade digital, mas fidelidade potencial alta.
- **Ação de marketing sugerida:** Promoções simplificadas via e-mail com linguagem clara e CTAs diretos. Campanhas sazonais (Dia das Mães, Natal) com produtos de fácil navegação e opção de atendimento humano.
- **KPI principal:** Taxa de conversão em campanhas sazonais.
- **Meta (3 meses):** Aumentar a taxa de conversão em 10% durante as próximas 2 datas comemorativas.
- **Justificativa:** Comunicação adaptada ao perfil reduz fricção e aumenta conversão nesse segmento, que costuma ter alto ticket nas compras que efetua quando bem segmentado.

---

### Cluster 5: VIPs em Risco 💎

- **Perfil resumido:** Clientes com histórico de alto gasto e adesão Gold, mas que reduziram significativamente a atividade recente. Representam a maior perda potencial de receita do portfólio.
- **Ação de marketing sugerida:** Contato proativo e personalizado (preferencialmente via Account Manager ou e-mail assinado pelo CEO da plataforma) com oferta exclusiva de reengajamento: crédito, frete grátis por 3 meses ou acesso a coleção exclusiva.
- **KPI principal:** Retorno ao padrão histórico de compras (frequência e gasto pré-queda).
- **Meta (3 meses):** Recuperar 25% dos clientes desse cluster ao nível histórico de atividade.
- **Justificativa:** São clientes que já demonstraram alto valor; a queda sugere insatisfação ou mudança de contexto — não abandono definitivo. Atenção personalizada tem alto ROI nesse grupo.

---

### Cluster 6: Exploradores de Desconto 🔄

- **Perfil resumido:** Clientes que concentram compras em períodos com `Discount Applied = 1`, com frequência e gasto correlacionados a promoções. Baixa conversão em períodos sem oferta.
- **Ação de marketing sugerida:** Programa de fidelização pós-compra com pontos acumuláveis — incentivando a recompra sem desconto — e testes A/B de ofertas de valor não-monetário (frete grátis, brinde, acesso antecipado).
- **KPI principal:** Percentual de compras realizadas sem desconto aplicado.
- **Meta (3 meses):** Aumentar em 5 p.p. a participação de compras full-price nesse cluster.
- **Justificativa:** Reduzir a dependência de desconto protege a margem. Alternativas de valor percebido criam vínculo emocional sem comprometer a rentabilidade.

---

## 🚀 Como Reproduzir

```bash
# Clone o repositório
git clone https://github.com/HammadN98/Segmentacao_de_Clientes_para_E-commerce.git
cd Segmentacao_de_Clientes_para_E-commerce

# Instale as dependências
pip install -r requirements.txt

# Execute o notebook principal
jupyter notebook notebooks/segmentacao_clientes.ipynb
```

**Dependências principais:**
- `pandas`, `numpy` — manipulação de dados
- `scikit-learn` — K-Means, StandardScaler, Silhouette Score
- `matplotlib`, `seaborn` — visualizações
- `yellowbrick` — Elbow Method visual

---

## 🔭 Próximos Passos

- [ ] Testar algoritmos alternativos: **DBSCAN** e **Hierarchical Clustering** para comparação
- [ ] Aplicar **PCA** para redução dimensional e melhor visualização dos clusters em 2D
- [ ] Criar **pipeline de re-segmentação automática** mensal à medida que novos dados chegam
- [ ] Calcular **LTV real por cluster** com dados históricos para validar projeções de impacto
- [ ] Integrar segmentos a uma ferramenta de CRM/CDP para automação das campanhas

---

## 👤 Autor

Desenvolvido por **[Hammad N.](https://github.com/HammadN98)**  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/HammadN98)
