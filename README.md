# 🏏 IPL 2022 Season Analytics

> Exploratory data analysis of all **74 matches** of the 2022 Indian Premier League, covering team performance, toss strategy, player impact and venue behaviour.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4c72b0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Table of Contents
1. [Project Overview](#-project-overview)
2. [Business Questions](#-business-questions)
3. [Dataset](#-dataset)
4. [Methodology](#-methodology)
5. [Key Findings](#-key-findings)
6. [Visual Gallery](#-visual-gallery)
7. [Repository Structure](#-repository-structure)
8. [Getting Started](#-getting-started)
9. [Limitations & Future Work](#-limitations--future-work)
10. [Author](#-author)

---

## 🎯 Project Overview

The IPL is one of the most data-rich T20 leagues in the world. This capstone project takes the match-level records of the 2022 season (the first with 10 teams) and turns them into clear, decision-ready insights.

The workflow covers the full analyst cycle: **data inspection → cleaning → feature engineering → visual analysis → insight reporting**.

**Skills demonstrated:** data cleaning, string parsing, feature engineering, aggregation (`groupby`), statistical summarisation, and publication-quality visualisation.

## ❓ Business Questions

| # | Question |
|---|----------|
| 1 | Which team dominated the 2022 season? |
| 2 | What do captains choose after winning the toss, and does it matter? |
| 3 | Are matches won more by defending (runs) or chasing (wickets)? |
| 4 | Who are the most impactful batters, bowlers and match-winners? |
| 5 | Which venues hosted the most matches, and how do they play? |
| 6 | What were the standout individual and team records? |

## 🗂 Dataset

| Property | Detail |
|----------|--------|
| File | `IPL.csv` |
| Records | 74 matches |
| Columns | 20 (7 numeric, 13 categorical) |
| Missing values | **0** |
| Season | IPL 2022 (26 March to 29 May 2022) |

**Key columns:** `match_id`, `date`, `venue`, `team1`, `team2`, `stage`, `toss_winner`, `toss_decision`, `first_ings_score`, `second_ings_score`, `match_winner`, `won_by`, `margin`, `player_of_the_match`, `top_scorer`, `highscore`, `best_bowling`, `best_bowling_figure`.

## 🛠 Methodology

**1. Data inspection:** shape, dtypes, null counts and duplicate checks confirmed a clean dataset.

**2. Cleaning & feature engineering**
- Split `venue` into separate `venue` and `city` columns (whitespace-stripped).
- Parsed `date` into a proper datetime.
- Standardised team names (e.g. `Banglore` → `Bengaluru`).
- Created `toss_match_win` (did the toss winner win the match?).
- Extracted `wickets_taken` and `runs_conceded` from `best_bowling_figure` (format `3--20`).
- Derived `bat_first_team` and `bat_first_won` to measure chasing success.

**3. Analysis & visualisation:** bar charts, donut chart and KDE plots built with a consistent theme, value labels and descriptive subtitles, exported to `/images`.

**4. Insight extraction:** key findings are generated programmatically at the end of the script so they never go out of sync with the data.

---

## 📊 Key Findings

### 🏆 Team performance
- **Gujarat won the most matches (12)**, followed by **Rajasthan (10)**, and **Bengaluru and Lucknow (9 each)**.
- **Chennai and Mumbai finished with just 4 wins each**, the lowest in the league.

### 🪙 Toss strategy
- Captains overwhelmingly **chose to field first: about 59 of 74 tosses (≈80%)**, against roughly 15 for batting. Chasing was the dominant philosophy of the season.

### ⚖️ Defending vs chasing
- Results were **perfectly balanced: 37 wins by wickets and 37 by runs**. Despite the strong preference for chasing, neither approach had a decisive edge.

### ⭐ Player impact
| Category | Leader |
|----------|--------|
| Most Player-of-the-Match awards | **Kuldeep Yadav (4)**, then **Jos Buttler (3)** |
| Most runs in match-topping innings | **Jos Buttler (≈650)**, then Quinton de Kock (≈375) and KL Rahul (≈350) |
| Most wickets in match-best spells | **Yuzvendra Chahal (17)**, then Kuldeep Yadav, Rashid Khan and Jasprit Bumrah (11 each) |

### 🏟 Venues
- **Wankhede Stadium (≈21)** and **Dr DY Patil Sports Academy (20)** hosted the most matches, followed by Brabourne Stadium (16) and the MCA Stadium, Pune (13). The two playoff venues, Eden Gardens and Narendra Modi Stadium, hosted 2 each.
- The league phase was concentrated in **Mumbai and Pune**, a bio-bubble-style logistical choice.

### 🥇 Records
| Record | Detail |
|--------|--------|
| Biggest win by runs | **91 runs**: Chennai (208/6) vs Delhi, Match 55 at Dr DY Patil Sports Academy; Devon Conway made 87 |
| Highest individual score | **140 by Quinton de Kock**: Lucknow vs Kolkata, Match 66; Lucknow won by just 2 runs |

---

## 🖼 Visual Gallery

| | |
|---|---|
| ![Team wins](images/01_team_wins.png) | ![Toss decision](images/02_toss_decision.png) |
| ![Defending vs chasing](images/04_won_by.png) | ![Player of the match](images/05_player_of_match.png) |
| ![Top batters](images/06_top_scorers.png) | ![Top bowlers](images/07_top_bowlers.png) |
| ![Venues](images/08_venues.png) | ![Venue scoring](images/09_venue_scoring.png) |

## 📁 Repository Structure

```
ipl-2022-season-analytics/
├── data/
│   └── IPL.csv                  # Match-level dataset
├── notebooks/
│   └── IPL_capstone_project.ipynb
├── src/
│   └── ipl_2022_analysis.py     # Clean, reproducible script
├── images/                      # Exported charts
├── requirements.txt
└── README.md
```

## 🚀 Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/ipl-2022-season-analytics.git
cd ipl-2022-season-analytics

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the analysis
python src/ipl_2022_analysis.py
# or open the notebook:
jupyter notebook notebooks/IPL_capstone_project.ipynb
```

**`requirements.txt`**
```
pandas
numpy
matplotlib
seaborn
jupyter
```

## ⚠️ Limitations & Future Work

**Limitations**
- The dataset records only the **top scorer and best bowler per match**, so the batting and bowling leaderboards reflect *match-topping performances*, not full-season run and wicket totals.
- With 74 matches, differences such as toss advantage are statistically small-sample observations.

**Future work**
- Add ball-by-ball data for true season leaderboards (Orange Cap / Purple Cap).
- Test toss advantage with a chi-square test.
- Predict match outcomes (logistic regression / random forest) using toss, venue and first-innings score.
- Build an interactive Streamlit or Power BI dashboard.
- Extend to multi-season analysis (2008 to 2022).

## 👤 Author

**Your Name**
[LinkedIn](https://linkedin.com/in/your-profile) · [GitHub](https://github.com/your-username) · your.email@example.com

⭐ If you found this project useful, consider giving it a star!
