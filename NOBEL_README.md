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
<img width="1496" height="1580" alt="image" src="https://github.com/user-attachments/assets/78715641-b4e5-4812-ad76-4ab919de1de4" />


- Bar chart with count labels
<img width="1982" height="1178" alt="image" src="https://github.com/user-attachments/assets/f2ad752e-5410-4b92-a1d6-7d528b8b81f7" />

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
<img width="2780" height="1579" alt="image" src="https://github.com/user-attachments/assets/fbbc193c-2dee-49a3-a2d4-cb48647ddc69" />

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
<img width="2783" height="1379" alt="image" src="https://github.com/user-attachments/assets/db04f784-f17a-46b3-93c7-88dbe9f34ba4" />

- Comparison of USA vs total winners by decade
<img width="2782" height="1379" alt="image" src="https://github.com/user-attachments/assets/a05a43c4-3111-4d82-8ba2-da3741fe8979" />

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
<img width="2783" height="1379" alt="image" src="https://github.com/user-attachments/assets/7b48087b-d565-4241-8ec8-4351554feda7" />

- Female winners by category
<img width="2381" height="1379" alt="image" src="https://github.com/user-attachments/assets/5b35ea4d-b081-4aa0-9b54-63b39e0c845c" />

- Gender comparison across categories
<img width="2782" height="1379" alt="image" src="https://github.com/user-attachments/assets/782de89d-6f61-443c-91e9-95e60c2dc74d" />

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
<img width="2781" height="1380" alt="image" src="https://github.com/user-attachments/assets/88b55f82-f56b-4713-95e1-354d4dfae5d5" />

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
<img width="2375" height="1178" alt="image" src="https://github.com/user-attachments/assets/b8c840bf-513e-4fae-9e80-8b8bc805eb59" />

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




## Contributing

Contributions welcome! Areas for enhancement:
- Additional statistical tests
- Machine learning predictions
- Interactive visualizations
- Geographic mapping
- Network analysis of collaborations




*A data-driven exploration of Nobel Prize winners spanning over a century of scientific, literary, and humanitarian achievement.*
