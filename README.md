# Facebook Ads Campaign Performance Analysis

[English](README.md) | [Português](README.pt-BR.md)

A comprehensive data analysis project examining digital marketing campaign performance using real Facebook Ads data. This study focuses on cost optimization strategies by identifying inefficient ad spending patterns and high-performing audience segments through statistical analysis and data visualization.

## 🎯 Project Overview

This analysis examines **1,143 observations** from XYZ company's Facebook advertising campaigns to identify cost optimization opportunities. Without revenue data available, the project treats the problem as a **cost minimization exercise**, aiming to cut underperforming campaigns while scaling winning patterns.

### Business Context

Ideally, we would have revenue return data to calculate actual ROI. However, this analysis approaches the problem from a **cost optimization perspective**:
- Identify and cut campaigns with high relative spending and low performance
- Discover demographic and segmentation patterns that work
- Recommend adjustments to maximize investment efficiency

## 📊 Key Findings

- 💰 **$10,442 in immediate savings** identified by pausing 87 "zombie" ads (ads with zero conversions)
- 📈 **30-34 age range** shows statistically significant superior performance (p < 0.05, Bonferroni corrected)
- ⚠️ **Campaign 1178** has **2x worse CPA** than other campaigns due to poor audience segmentation
- 🚫 **40-49 age group** generates high costs with minimal conversion rates
- ✅ Specific **interest codes** (29, 16, 10, 15, 19, 26, 64, 63, 27) perform well when properly segmented
- 👥 **Statistical evidence** of gender CPA differences requiring consideration in budget allocation

## 🛠️ Technologies Used

- **R (4.x)** - Main analysis language
- **tidyverse** - Data manipulation and transformation
- **ggplot2** - Data visualization and custom plotting
- **skimr** - Statistical summaries and data profiling
- **DataExplorer** - Automated exploratory data analysis
- **gridExtra** - Multi-plot arrangements
- **scales** - Scale formatting for visualizations

## 📁 Project Structure

```
├── data/
│   └── KAG_conversion_data.csv
├── marketing_campaign_analysis.R
├── marketing_campaign_analysis.pt-BR.R
├── README.md
└── README.pt-BR.md
```

## 📈 Analysis Components

### 1. Exploratory Data Analysis
- Campaign distribution and volume analysis
- Demographic patterns (age, gender)
- Data quality assessment
- Missing value analysis

### 2. Performance Metrics
- **CTR (Click-Through Rate)**: Click rate relative to impressions
- **CPC (Cost Per Click)**: Average cost per click
- **CPA (Cost Per Acquisition)**: Cost per completed sale
- Conversion funnel analysis by campaign

### 3. Ad Classification System
Custom framework classifying each ad into:
- **⭐ Star (Cheap)**: CPA below $40 (base average)
- **💀 Zombie (Spends and doesn't sell)**: Zero conversions, spent > $50
- **⚠️ Expensive (Needs Optimization)**: CPA above $40
- **🧪 In Test**: Low relative spending

### 4. Statistical Validation
- **Pairwise proportion tests** with Bonferroni correction for age groups
- **Kruskal-Wallis test** for CPA differences by gender
- Hypothesis testing at α = 0.05 significance level

### 5. Executive Report
- Problem diagnosis (demographic dispersion, zombie ads, poor segmentation)
- High-performance profile identification
- Short and medium-term action plans
- Expected impact quantification

## 📊 Dataset

**Source**: [Kaggle - Sales Conversion Optimization](https://www.kaggle.com/datasets/loveall/clicks-conversion-tracking/data)

**Size**: 1,143 observations × 11 variables

**Variables**:
- `ad_id`: Unique identifier for each ad
- `xyz_campaign_id`: XYZ company campaign ID
- `fb_campaign_id`: Facebook campaign tracking ID
- `age`: Target audience age range
- `gender`: Target audience gender (M/F)
- `interest`: Interest category code
- `Impressions`: Number of times ad was displayed
- `Clicks`: Number of clicks received
- `Spent`: Amount invested ($)
- `Total_Conversion`: Total leads generated
- `Approved_Conversion`: Total sales completed

## 🚀 Quick Start

### Prerequisites

```r
# Install required packages
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

### Running the Analysis

```r
# Clone the repository
git clone https://github.com/yourusername/facebook-ads-analysis.git
cd facebook-ads-analysis

# Open R or RStudio and run
source("marketing_campaign_analysis.R")
```

### Expected Output

The script will generate:
- Statistical summaries and data quality reports
- Multiple visualization plots (funnels, heatmaps, scatter plots)
- Performance metrics by campaign
- Ad classification results
- Statistical test outputs

## 📋 Key Recommendations

### Immediate Actions (Week 1)
- ✅ **Pause 87 zombie ads** → $10,442 immediate savings
- ✅ Top 10 zombies alone represent 30% of total waste

### Short-Term Actions (Week 2)
- 🎯 **Exclude 40-49 age range** from Campaign 1178
- 🎯 This demographic shows high cost with minimal conversion

### Strategic Actions (Weeks 3-4)
- 📊 **Reallocate budget to 30-34 age range** with proven performance
- 📊 **Create new ad sets** using high-performing interests (29, 16, 10, 15, 19, 26, 64, 63, 27)
- 📊 Restrict to 30-34 age range exclusively

### Long-Term Implementation (Month 2+)
- 🔄 Weekly monitoring of "Expensive" classified ads
- 🔄 $50 test spending limit before zombie classification
- 🔄 Quarterly review cycles for new interest identification

## 📊 Sample Visualizations

The analysis includes professional visualizations such as:

- **Conversion Funnel Charts**: Visual representation of campaign performance from impressions to sales
- **Gender Distribution Heatmaps**: Demographic patterns across campaigns and age ranges
- **Interest Performance Matrices**: Bubble charts showing CPA vs sales volume
- **Star vs Zombie Comparison**: Demographic profile differences between high and low performers
- **Common Interest Analysis**: Quadrant plots identifying segmentation optimization opportunities

## 🔍 Detailed Findings

### Campaign Performance Comparison

| Campaign | Ads Run | Investment | CPA | Lead→Sale Rate |
|----------|---------|------------|-----|----------------|
| 916      | Low     | Low        | **Lowest** | **Best** |
| 936      | Medium  | Medium     | Medium | Medium |
| 1178     | **Highest** | **Highest** | **2x worse** | **Worst** |

### Demographic Insights

**High Performers (Stars)**:
- Age: 30-34 years (statistically significant, p < 0.05)
- Gender: Balanced with slight male focus
- Interests: Codes 29, 16, 10, 15, 19, 26, 64, 63, 27

**Low Performers (Zombies)**:
- Age: 40-49 years (poor conversion rate)
- Same interest codes but different demographic
- Problem is **segmentation**, not interest quality

### Statistical Evidence

```
Age Range Conversion Rates (Pairwise Proportion Test)
- 30-34 vs 35-39: p < 0.05 ✓
- 30-34 vs 40-44: p < 0.01 ✓✓
- 30-34 vs 45-49: p < 0.001 ✓✓✓
```

## 💡 Insights & Learnings

1. **Same interests, different results**: Interest codes 29, 16, 10, 15 appear in both top-performing and worst-performing ads. The difference? **Age segmentation**.

2. **Zombie concentration**: Campaign 1178's poor performance is driven by a large number of non-converting ads that should have been paused earlier.

3. **Statistical validation matters**: Initial observations were confirmed through rigorous hypothesis testing, providing confidence in recommendations.

4. **Cost vs Revenue**: Without revenue data, we focus on cost minimization. Future analyses should incorporate revenue tracking for complete ROI assessment.
