# Análise de Performance de Campanhas de Facebook Ads

[English](README.md) | [Português](README.pt-BR.md)

Projeto completo de análise de dados examinando a performance de campanhas de marketing digital utilizando dados reais de Facebook Ads. Este estudo foca em estratégias de otimização de custos através da identificação de padrões de gastos ineficientes e segmentos de audiência de alto desempenho, utilizando análise estatística e visualização de dados.

## 🎯 Visão Geral do Projeto

Esta análise examina **1.143 observações** de campanhas de publicidade da empresa XYZ no Facebook para identificar oportunidades de otimização de custos. Sem dados de receita disponíveis, o projeto trata o problema como um **exercício de minimização de custos**, visando cortar campanhas de baixo desempenho enquanto escala padrões vencedores.

### Contexto de Negócio

Idealmente, teríamos dados de retorno de receita para calcular o ROI real. Porém, esta análise aborda o problema sob uma **perspectiva de otimização de custos**:
- Identificar e cortar campanhas com gastos relativamente altos e baixo desempenho
- Descobrir padrões demográficos e de segmentação que funcionam
- Recomendar ajustes para maximizar a eficiência do investimento

## 📊 Principais Descobertas

- 💰 **$10.442 em economia imediata** identificados pausando 87 anúncios "zombie" (anúncios com zero conversões)
- 📈 **Faixa 30-34 anos** mostra performance estatisticamente superior (p < 0,05, correção de Bonferroni)
- ⚠️ **Campanha 1178** tem **CPA 2x pior** que outras campanhas devido à segmentação inadequada
- 🚫 **Faixa 40-49 anos** gera custos altos com taxas mínimas de conversão
- ✅ **Códigos de interesse específicos** (29, 16, 10, 15, 19, 26, 64, 63, 27) performam bem quando segmentados adequadamente
- 👥 **Evidência estatística** de diferenças de CPA entre gêneros que requerem consideração na alocação de orçamento

## 🛠️ Tecnologias Utilizadas

- **R (4.x)** - Linguagem principal de análise
- **tidyverse** - Manipulação e transformação de dados
- **ggplot2** - Visualização de dados e plotagem customizada
- **skimr** - Sumários estatísticos e perfil de dados
- **DataExplorer** - Análise exploratória automatizada
- **gridExtra** - Arranjos de múltiplos gráficos
- **scales** - Formatação de escalas para visualizações

## 📁 Estrutura do Projeto

```
├── data/
│   └── KAG_conversion_data.csv
├── marketing_campaign_analysis.R
├── marketing_campaign_analysis.pt-BR.R
├── README.md
└── README.pt-BR.md
```

## 📈 Componentes da Análise

### 1. Análise Exploratória de Dados
- Análise de distribuição e volume de campanhas
- Padrões demográficos (idade, gênero)
- Avaliação de qualidade dos dados
- Análise de valores faltantes

### 2. Métricas de Performance
- **CTR (Click-Through Rate)**: Taxa de cliques em relação às impressões
- **CPC (Cost Per Click)**: Custo médio por clique
- **CPA (Cost Per Acquisition)**: Custo por venda completada
- Análise de funil de conversão por campanha

### 3. Sistema de Classificação de Anúncios
Framework customizado classificando cada anúncio em:
- **⭐ Estrela (Barato)**: CPA abaixo de $40 (média da base)
- **💀 Zombie (Gasta e não vende)**: Zero conversões, gasto > $50
- **⚠️ Caro (Precisa Otimizar)**: CPA acima de $40
- **🧪 Em Teste**: Gasto relativo baixo

### 4. Validação Estatística
- **Testes de proporções pareadas** com correção de Bonferroni para grupos etários
- **Teste de Kruskal-Wallis** para diferenças de CPA por gênero
- Testes de hipótese com nível de significância α = 0,05

### 5. Relatório Executivo
- Diagnóstico de problemas (dispersão demográfica, anúncios zombie, segmentação inadequada)
- Identificação de perfil de alta performance
- Planos de ação de curto e médio prazo
- Quantificação de impacto esperado

## 📊 Dataset

**Fonte**: [Kaggle - Sales Conversion Optimization](https://www.kaggle.com/datasets/loveall/clicks-conversion-tracking/data)

**Tamanho**: 1.143 observações × 11 variáveis

**Variáveis**:
- `ad_id`: Identificador único de cada anúncio
- `xyz_campaign_id`: ID da campanha da empresa XYZ
- `fb_campaign_id`: ID de rastreamento da campanha no Facebook
- `age`: Faixa etária do público-alvo
- `gender`: Gênero do público-alvo (M/F)
- `interest`: Código da categoria de interesse
- `Impressions`: Número de vezes que o anúncio foi exibido
- `Clicks`: Número de cliques recebidos
- `Spent`: Valor investido ($)
- `Total_Conversion`: Total de leads gerados
- `Approved_Conversion`: Total de vendas completadas

## 🚀 Como Executar

### Pré-requisitos

```r
# Instalar pacotes necessários
install.packages(c(
  "readr",
  "tidyverse",
  "ggplot2",
  "skimr",
  "DataExplorer",
  "gridExtra",
  "scales"
))
```

### Executando a Análise

```r
# Clonar o repositório
git clone https://github.com/seuusuario/facebook-ads-analysis.git
cd facebook-ads-analysis

# Abrir R ou RStudio e executar
source("marketing_campaign_analysis.R")
```

### Output Esperado

O script irá gerar:
- Sumários estatísticos e relatórios de qualidade de dados
- Múltiplos gráficos de visualização (funis, heatmaps, scatter plots)
- Métricas de performance por campanha
- Resultados de classificação de anúncios
- Outputs de testes estatísticos

## 📋 Recomendações Principais

### Ações Imediatas (Semana 1)
- ✅ **Pausar 87 anúncios zombie** → $10.442 de economia imediata
- ✅ Top 10 zombies sozinhos representam 30% do desperdício total

### Ações de Curto Prazo (Semana 2)
- 🎯 **Excluir faixa 40-49 anos** da Campanha 1178
- 🎯 Esta demografia mostra alto custo com conversão mínima

### Ações Estratégicas (Semanas 3-4)
- 📊 **Realocar orçamento para faixa 30-34 anos** com performance comprovada
- 📊 **Criar novos conjuntos de anúncios** usando interesses de alta performance (29, 16, 10, 15, 19, 26, 64, 63, 27)
- 📊 Restringir exclusivamente à faixa 30-34 anos

### Implementação de Longo Prazo (Mês 2+)
- 🔄 Monitoramento semanal de anúncios classificados como "Caros"
- 🔄 Limite de $50 de gasto de teste antes de classificação zombie
- 🔄 Ciclos de revisão trimestral para identificação de novos interesses

## 📊 Exemplos de Visualizações

A análise inclui visualizações profissionais como:

- **Gráficos de Funil de Conversão**: Representação visual da performance de campanhas desde impressões até vendas
- **Heatmaps de Distribuição de Gênero**: Padrões demográficos através de campanhas e faixas etárias
- **Matrizes de Performance de Interesse**: Gráficos de bolha mostrando CPA vs volume de vendas
- **Comparação Estrela vs Zombie**: Diferenças de perfil demográfico entre alto e baixo desempenho
- **Análise de Interesses Comuns**: Gráficos de quadrante identificando oportunidades de otimização de segmentação

## 🔍 Descobertas Detalhadas

### Comparação de Performance de Campanhas

| Campanha | Ads Rodados | Investimento | CPA | Taxa Lead→Venda |
|----------|-------------|--------------|-----|-----------------|
| 916      | Baixo       | Baixo        | **Menor** | **Melhor** |
| 936      | Médio       | Médio        | Médio | Médio |
| 1178     | **Maior**   | **Maior**    | **2x pior** | **Pior** |

### Insights Demográficos

**Alto Desempenho (Estrelas)**:
- Idade: 30-34 anos (estatisticamente significativo, p < 0,05)
- Gênero: Balanceado com leve foco masculino
- Interesses: Códigos 29, 16, 10, 15, 19, 26, 64, 63, 27

**Baixo Desempenho (Zombies)**:
- Idade: 40-49 anos (taxa de conversão pobre)
- Mesmos códigos de interesse mas demografia diferente
- Problema é **segmentação**, não qualidade do interesse

### Evidência Estatística

```
Taxas de Conversão por Faixa Etária (Teste de Proporções Pareadas)
- 30-34 vs 35-39: p < 0,05 ✓
- 30-34 vs 40-44: p < 0,01 ✓✓
- 30-34 vs 45-49: p < 0,001 ✓✓✓
```

## 💡 Insights & Aprendizados

1. **Mesmos interesses, resultados diferentes**: Códigos de interesse 29, 16, 10, 15 aparecem tanto em anúncios de melhor quanto de pior desempenho. A diferença? **Segmentação etária**.

2. **Concentração de zombies**: O baixo desempenho da Campanha 1178 é impulsionado por um grande número de anúncios não-conversores que deveriam ter sido pausados anteriormente.

3. **Validação estatística importa**: Observações iniciais foram confirmadas através de testes de hipótese rigorosos, fornecendo confiança nas recomendações.

4. **Custo vs Receita**: Sem dados de receita, focamos em minimização de custos. Análises futuras devem incorporar rastreamento de receita para avaliação completa de ROI.
