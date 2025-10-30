# Game Style Matcher 🎮✨

A tool for **finding similar games** based on their characteristics.

---

## Table of Contents

- [English Version](#english-version)
  - [Goal](#goal)
  - [Dataset](#dataset)
  - [Technologies & Tools](#technologies--tools)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Results](#results)
  - [Future Improvements](#future-improvements)
  - [Repository Structure](#repository-structure)
  - [Author](#author)
- [Русская версия](#русская-версия)
  - [Цель](#цель)
  - [Датасет](#датасет)
  - [Технологии и инструменты](#технологии-и-инструменты)
  - [Установка](#установка)
  - [Использование](#использование)
  - [Результаты](#результаты)
  - [Дальнейшие улучшения](#дальнейшие-улучшения)
  - [Структура репозитория](#структура-репозитория)
  - [Автор](#автор)

---

## English Version

### Goal
- Build a tool that **finds and recommends games similar** to a given game based on features like genre, platform, scores, and sales.  
- Understand patterns and clusters of games via visualization.

### Dataset
- Source: [VG Games dataset on Kaggle](https://www.kaggle.com/datasets) (or your own dataset)
- Key features:
  - `Name` — game title
  - `Platform` — platform
  - `Year_of_Release` — release year
  - `Genre` — genre
  - `Publisher` — publisher
  - `NA_Sales`, `EU_Sales`, `JP_Sales`, `Other_Sales`, `Global_Sales` — sales
  - `Critic_Score`, `User_Score` — scores
- Data preprocessing:
  - Handling missing values
  - Encoding categorical features (one-hot)
  - Scaling numeric features

### Technologies & Tools
- Python 3.11
- Jupyter Notebook
- Pandas, NumPy — data handling
- Scikit-learn — ML, preprocessing
- Matplotlib, Seaborn — visualization
- Cosine similarity — finding similar games
- TSNE — 2D visualization for clusters

### Installation
```bash
git clone https://github.com/himynameisartem/Game_Style_Matcher.git
cd Game_Style_Matcher

python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

pip install -r requirements.txt