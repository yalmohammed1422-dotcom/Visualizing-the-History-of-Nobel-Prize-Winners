# Nobel Prize Winners Analysis

A comprehensive data analysis project exploring Nobel Prize winner demographics, trends, and patterns across decades, countries, categories, and gender distributions.

## Overview

This project analyzes historical Nobel Prize data to uncover insights about:
1. Gender distribution among Nobel Prize winners
2. Countries producing the most laureates
3. USA-born winners' proportion by decade
4. Female representation trends and category dominance
5. First woman Nobel Prize winner
6. Individuals who won multiple Nobel Prizes

## Features

- **Gender Analysis**: Distribution and trends of male vs female laureates
- **Geographic Insights**: Identification of top countries by Nobel Prize winners
- **Temporal Trends**: Decade-by-decade analysis of winner demographics
- **USA Dominance**: Tracking proportion of USA-born winners over time
- **Female Representation**: Historical progression and category breakdown
- **Repeat Winners**: Identification of individuals with multiple Nobel Prizes
- **Comprehensive Visualizations**: 11 matplotlib charts for deep insights

## Requirements

```python
pandas
matplotlib
numpy
```

Install dependencies:
```bash
pip install pandas matplotlib numpy
```

## Dataset

The analysis expects a DataFrame named `df` with the following columns:
- `full_name`: Full name of the Nobel Prize winner
- `sex`: Gender (Male/Female)
- `birth_country`: Country of birth
- `year`: Year the prize was awarded
- `category`: Nobel Prize category (Physics, Chemistry, Medicine, Literature, Peace, Economics)

## Analysis Breakdown

### Analysis 1: Gender Distribution

**Objective**: Determine the most common gender among Nobel Prize winners

```python
# Count gender frequency and find the most common
top_gender = df['sex'].value_counts().idxmax()
```

**Visualizations**:
- Pie chart showing gender distribution with percentages
- Bar chart with count labels

**Key Insight**: Reveals historical gender imbalance in Nobel Prize awards

---

### Analysis 2: Top Country

**Objective**: Identify which country has produced the most Nobel laureates

```python
# Count country frequency and find the most common
top_country = df['birth_country'].value_counts().idxmax()
```

**Visualizations**:
- Horizontal bar chart of top 10 countries (highlighted winner)

**Key Insight**: Shows geographic concentration of Nobel Prize winners

---

### Analysis 3: USA Born Winners by Decade

**Objective**: Find the decade with the highest proportion of USA-born winners

```python
# Create decade column
df['decade'] = df['year'] // 10 * 10

# Filter USA-born winners
usa_born = df[df['birth_country'] == 'United States of America']

# Calculate ratio by decade
total_decade_counts = df['decade'].value_counts()
usa_decade_counts = usa_born['decade'].value_counts()
ratio = usa_decade_counts / total_decade_counts

# Find maximum
max_decade_usa = ratio.idxmax()
```

**Visualizations**:
- Bar chart showing USA proportion by decade (highlighted max)
- Comparison of USA vs total winners by decade

**Key Insight**: Tracks the rise of USA scientific dominance

---

### Analysis 4: Female Winners Analysis

**Objective**: Identify decade and category with highest female representation

```python
# Filter female winners
female_filter = df[df['sex'] == 'Female']

# Calculate proportions by decade
female_decade_counts = female_filter['decade'].value_counts()
proportion = female_decade_counts / total_decade_counts
decade_max_proportion = proportion.idxmax()

# Find category with highest female proportion in that decade
female_max_proportion = female_filter[female_filter['decade'] == decade_max_proportion]
nobel_prize_cat = female_max_proportion['category'].value_counts()
cat_max_proportion = cat_proportion.idxmax()

max_female_dict = {decade_max_proportion: cat_max_proportion}
```

**Visualizations**:
- Female proportion by decade (highlighted max)
- Female winners by category
- Gender comparison across categories

**Key Insight**: Shows progress (or lack thereof) in gender equality over time

---

### Analysis 5: First Woman Winner

**Objective**: Identify the first woman to win a Nobel Prize

```python
# Sort female winners by year
ordered_women_winner = female_filter.sort_values('year', ascending=False)

# Get the earliest (last in descending order)
first_woman_name = ordered_women_winner['full_name'].iloc[-1]
first_woman_category = ordered_women_winner['category'].iloc[-1]
```

**Visualizations**:
- Timeline of female winners with first woman marked

**Key Insight**: Historical milestone in Nobel Prize history

---

### Analysis 6: Repeat Winners

**Objective**: Find individuals who won multiple Nobel Prizes

```python
# Count name frequency
freq_names = df['full_name'].value_counts()

# Filter those with more than one prize
more_than_one = freq_names[freq_names > 1]
repeat_list = list(more_than_one.index)
```

**Visualizations**:
- Horizontal bar chart of repeat winners

**Key Insight**: Extremely rare achievement highlighting exceptional contributions

---

## Visualizations Summary

The project includes **11 matplotlib visualizations**:

1. **Gender Distribution Pie Chart** - Overall gender breakdown with percentages
2. **Gender Distribution Bar Chart** - Count comparison with labels
3. **Top 10 Countries** - Horizontal bar chart (top country highlighted)
4. **USA Winners Proportion by Decade** - Tracks USA dominance over time
5. **USA vs Total Winners Comparison** - Side-by-side decade comparison
6. **Female Proportion by Decade** - Shows progress in gender equality
7. **Female Winners by Category** - Category breakdown of female laureates
8. **Gender Comparison by Category** - Male vs Female in each category
9. **Female Winners Timeline** - Historical progression with first woman marked
10. **Repeat Winners** - Rare individuals with multiple prizes
11. **Comprehensive Dashboard** - 4-panel overview (decade, category, country, gender)

## Usage

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Load your data
df = pd.read_csv('nobel_prize_data.csv')

# Run the analysis script
# [Execute the analysis code]
```

## Sample Output

```
Most common gender among Nobel Prize winners: Male
Gender distribution:
Male      XXX
Female     XX

Country with most Nobel Prize winners: United States of America

Decade with highest proportion of USA-born winners: 2000s
Proportion: XX.XX%

Decade with highest female proportion: 2010s
Category with highest female proportion in that decade: Literature
Result dictionary: {2010: 'Literature'}

First woman to win Nobel Prize: Marie Curie
Category: Physics

Number of repeat winners: X
Repeat winners: ['Marie Curie', 'John Bardeen', ...]

==================================================
Analysis Complete!
==================================================
```

## Key Findings Template

Based on the analysis, you can report:
- **Gender Gap**: X% male vs Y% female laureates
- **Geographic Concentration**: Top country is [Country] with X winners
- **USA Peak**: Highest USA proportion in the [decade]s at X%
- **Female Progress**: Highest female representation in [decade]s
- **Pioneer**: First woman winner was [Name] in [Year] for [Category]
- **Elite Club**: X individuals have won multiple Nobel Prizes

## Insights & Interpretations

- **Historical Gender Imbalance**: The data reveals significant underrepresentation of women
- **Geographic Patterns**: Certain countries dominate due to research infrastructure
- **Temporal Trends**: Winner demographics shift with global power dynamics
- **Category Variations**: Gender distribution varies significantly by field
- **Recent Progress**: Modern decades show improvement in diversity

## Code Improvements Implemented

- ✅ **11 professional visualizations** using matplotlib only
- ✅ **Color-coded highlights** for maximum values and key insights
- ✅ **Comprehensive labels** on all charts with values
- ✅ **Trend analysis** with line plots and filled areas
- ✅ **Comparative visualizations** for context
- ✅ **Dashboard view** for holistic understanding
- ✅ **Print statements** for all key findings

## Potential Further Analysis

- Analyze age at time of award
- Study collaboration patterns (shared prizes)
- Examine time lag between discovery and recognition
- Investigate institutional affiliations
- Analyze prize motivation text for patterns
- Study longevity of laureates
- Compare founding vs recent categories

## Alternative Implementation

For more efficient decade analysis:
```python
# Vectorized decade creation
df['decade'] = (df['year'] // 10) * 10

# Direct groupby for proportions
proportions = df.groupby(['decade', 'sex']).size().unstack(fill_value=0)
proportions = proportions.div(proportions.sum(axis=1), axis=0)
```

## File Structure

```
project/
│
├── nobel_prize_analysis_matplotlib.py    # Main analysis script
├── README.md                             # This file
└── nobel_prize_data.csv                  # Your dataset (not included)
```

## Data Sources

Nobel Prize data can be obtained from:
- Official Nobel Prize API: https://api.nobelprize.org/
- Kaggle datasets
- Nobel Prize official website

## Contributing

Contributions welcome! Areas for enhancement:
- Additional statistical tests
- Machine learning predictions
- Interactive visualizations
- Geographic mapping
- Network analysis of collaborations

## License

This project is open source and available under the MIT License.

## Author

Nobel Prize Analysis Project

---

*A data-driven exploration of Nobel Prize winners spanning over a century of scientific, literary, and humanitarian achievement.*

## Acknowledgments

Data courtesy of the Nobel Prize organization and public datasets. This analysis is for educational purposes.
