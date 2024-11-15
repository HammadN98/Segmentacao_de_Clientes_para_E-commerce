# Segmentação de Clientes para E-commerce

## Pergunta de Negócio
**Como podemos identificar e segmentar grupos de clientes com comportamentos distintos para otimizar campanhas de marketing e aumentar o engajamento e a retenção?**

Este projeto utiliza técnicas de clustering para dividir clientes de e-commerce em grupos de acordo com seu comportamento e perfil de compra. Os insights obtidos ajudam o time de marketing a personalizar ofertas e direcionar campanhas para melhorar a experiência do cliente e aumentar o valor ao longo do tempo (lifetime value). A análise inclui variáveis como gasto total, frequência de compra, nível de satisfação e tipo de adesão.

---

## Principais Ações Realizadas

- **Limpeza e Pré-processamento de Dados**:
  - Remoção de valores nulos e normalização de variáveis numéricas.
  - Codificação das variáveis categóricas.

- **Análise de Agrupamento (Clustering)**:
  - Avaliação do número ideal de clusters usando o método do cotovelo e o Silhouette Score.
  - Aplicação do K-Means para formar grupos baseados em padrões de comportamento.

- **Criação de Perfis de Clientes**:
  - Definimos perfis claros para cada cluster considerando idade, frequência de compra, gasto médio, nível de satisfação e tipo de associação.

- **Estratégias de Marketing Baseadas em Clusters**:
  - Desenvolvemos campanhas específicas, como programas de fidelidade para clientes de alto valor e promoções de retorno para clientes de menor engajamento.

---

## Estrutura dos Dados

### Variáveis Numéricas:
- **Age**: Idade do cliente.
- **Total Spend**: Gasto total acumulado.
- **Items Purchased**: Número total de itens comprados.
- **Average Rating**: Avaliação média do cliente.
- **Days Since Last Purchase**: Dias desde a última compra.

### Variáveis Categóricas Codificadas:
- **Membership Type**: Tipo de adesão (1 = Bronze, 2 = Silver, 3 = Gold).
- **Satisfaction Level**: Nível de satisfação (1 = "Unsatisfied, 2 = Neutral, 3 = Neutral). 
- **Discount Applied**: Indica se foi aplicado desconto (0 = Não, 1 = Sim).
- **Gender**: Gênero do cliente (1 = Male, 2 = Female).
- **City**: Localização do cliente, categorizada numericamente.
  
---

## Sumário Executivo
O projeto segmentou clientes em sete clusters distintos com base em comportamentos de compra e características demográficas. Através da aplicação de K-Means e métricas como o Silhouette Score, foram criados perfis que identificam desde clientes de alto valor e frequência até clientes de menor gasto e engajamento. Esse modelo de segmentação permite a criação de campanhas de marketing personalizadas para aumentar o valor e a retenção dos clientes.

A segmentação fornece insights estratégicos que ajudam a empresa a entender seu público, permitindo ações específicas para fidelização e incremento do lifetime value dos clientes.

---
## Perfis dos Clusters e Principais Insights

- **Cluster de Alto Valor**: Clientes jovens, altamente satisfeitos, com alto gasto e frequência de compras. Esse grupo responde bem a campanhas exclusivas.
- **Cluster de Engajamento Médio**: Clientes com gasto intermediário e frequência regular. Potencial para aumentar o ticket médio com cross-selling e up-selling.
- **Cluster de Baixo Gasto e Frequência**: Clientes de idade mais avançada, com compras ocasionais e baixo gasto. Podem ser incentivados com promoções.
- **Clientes Inconstantes**: Compram com baixa frequência, mas possuem gasto moderado. Estratégias de reativação podem ser eficazes para esse grupo.

---

## Recomendações

1. **Campanhas de Exclusividade para Clusters de Alto Valor**:
   - Ofereça acesso antecipado a produtos, eventos VIP e programas de fidelidade exclusivos para incentivar a lealdade desses clientes.

2. **Promoções de Up-Selling e Cross-Selling para Clusters de Engajamento Médio**:
   - Aumente o ticket médio com ofertas de produtos complementares e recompensas para compras maiores.

3. **Campanhas de Retenção e Reativação para Clusters de Menor Engajamento**:
   - Incentive a atividade desses clientes com promoções e descontos específicos, aumentando a frequência de compras.

4. **Monitoramento Contínuo dos Clusters**:
   - Estabeleça um pipeline de atualização regular para manter os clusters relevantes e avaliar a eficácia das campanhas ao longo do tempo.
