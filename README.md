# Week-10-Project-API-and-Web-Data-Scraping-Part-2-

To analyze the data collected through the API and web scraping in Part 1 last week (week 9). 
This analysis will help gain insights from the data through exploratory data analysis (EDA), correlation analysis, and handling data quality issues such as missing values and outliers.
Results will be presented with a dashboard on Tableau or Streamlit.

---

## Business Questions & Hypotheses (English Premier League Focus)

### 1.A. **Goals For & Against vs League Winners**

- **Question:** *Does having a higher Goals For vs Goals Against ratio (GF/GA ratio) predict finishing top 3 in the league?*
- **Null Hypothesis (H₀):** There is no correlation between the teams with the highest GF/GA ratio and finishing top 3.
- **Data:**
    - Kaggle API: goals for/against per match/season depending on the dataframe.
    - Wikipedia Scrape: [wikipedia](https://en.wikipedia.org/wiki/2024%E2%80%9325_Premier_League#League_table) (league tables, GF, GA, Pos per season).

---

### 1.B. **Formation vs GF/GA ratio vs League Winners**

- **Question:** *Are formations with more in attack (e.g. 4-3-3 or 3-4-3) linked to a higher GF/GA ratio and is there a correlation with winning the league?*
- **Null Hypothesis (H₀):** There is no correlation between teams with more attacking formations *(4-3-3 or 3-4-3)* and higher GF/GA ratio.
- **Data:**
    - Kaggle API: GF/GA ratio per match/season. Group by formation, and take the average goals for and goals against to compare.
    - Wikipedia Scrape: [wikipedia](https://en.wikipedia.org/wiki/2024%E2%80%9325_Premier_League#League_table) (league tables, form), not needed for this question.
  

---

### 2.A. **Possession vs League Winners**

- **Question:** *Is possession percentage correlated with Premier League points?*
- **Null Hypothesis (H₀):** There is no or weak correlation with possession rate and higher points.
- **Data:**
    - Kaggle API: Group by team, take the average possession per team per match/season depending on the dataframe.
    - Wikipedia Scrape: [wikipedia](https://en.wikipedia.org/wiki/2024%E2%80%9325_Premier_League#League_table) (league tables, form), not needed for this question.

---

### 2.B. **Possession Home vs Away**

- **Question:** *Is possession percentage higher at home or away games?*
- **Null Hypothesis (H₀):** There is no correlation between possession rate and playing games at home.
- **Data:**
    - Kaggle API: Average possession per team per match/season sorted by venue (home vs away)
    - Wikipedia Scrape: [wikipedia](https://en.wikipedia.org/wiki/2024%E2%80%9325_Premier_League#League_table) (league tables, form), not needed for this question.

---

### 3. **Shots & Shots on Target**

- **Question:** *Do shots on target predict match outcomes better than total shots?*
- **Null Hypothesis (H₀):** Shots on target are not more strongly correlated with points per game than total shots.
- **Data:**
    - Kaggle API: Total shots (sh) / Shots on target (sot). Group by shots on target and total shots, take the average sot and sh, map Win, Lose, Draw points and compare to the W L D outcome.
    - Wikipedia Scrape: [wikipedia](https://en.wikipedia.org/wiki/2024%E2%80%9325_Premier_League#League_table) (league tables, form), not needed for this question.

---

**Wikipedia Web Scraping: [Wikipedia Premier League Table 2018-2025](https://en.wikipedia.org/wiki/List_of_Premier_League_seasons)**
- Wikipedia: 160 rows × 13 columns

**Kaggle API: dataframes 2018-2024**
- [2018-2020](https://www.kaggle.com/datasets/aditya2803/premier-league-team-data?select=Match+Info.csv): 2280 rows × 20 columns
- [2020-2023](https://www.kaggle.com/datasets/toluabbass/premier-league-team-stats-2023-2020?select=matches.csv): 2280 rows × 28 columns
- [2023-2024](https://www.kaggle.com/datasets/whisperingkahuna/premier-league-2324-team-and-player-insights): 20 rows × 10 columns

---

**Which Dataframes can I use to answer each Business Question?**

**Wikipedia Web Scraping**
- all_dfs = [df_18_cleaned, df_19_cleaned, df_20_cleaned, df_21_cleaned, df_22_cleaned, df_23_cleaned, df_24_cleaned, df_25_cleaned] concatenated = gf, ga, gf_ga_ratio, position (top_3 or non_top_3)

**Kaggle API**
- df_18_20 + df_20_23 = possession, formation, result, venue, gf, ga, xg, xga
- df_20_23 = possession, formation, result, venue, gf, ga, xg, xga, sh, sot
- df_2024_cleaned = possession
