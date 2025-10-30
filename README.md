# Game Style Matcher 🎮✨

A comprehensive machine learning project for **finding and recommending similar games** on Steam based on their characteristics, tags, genres, and user reviews. This project demonstrates advanced data visualization, feature engineering, and recommendation system implementation.

---

## Table of Contents

- [English Version](#english-version)
  - [Project Overview](#project-overview)
  - [Task Description](#task-description)
  - [Dataset](#dataset)
  - [Technologies & Tools](#technologies--tools)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Methodology](#methodology)
  - [Results](#results)
  - [Future Improvements](#future-improvements)
  - [Repository Structure](#repository-structure)
  - [Author](#author)
- [Русская версия](#русская-версия)
  - [Обзор проекта](#обзор-проекта)
  - [Описание задачи](#описание-задачи)
  - [Датасет](#датасет-1)
  - [Технологии и инструменты](#технологии-и-инструменты-1)
  - [Установка](#установка-1)
  - [Использование](#использование-1)
  - [Методология](#методология)
  - [Результаты](#результаты-1)
  - [Дальнейшие улучшения](#дальнейшие-улучшения-1)
  - [Структура репозитория](#структура-репозитория-1)
  - [Автор](#автор-1)

---

## English Version

### Project Overview

Game Style Matcher is an intelligent recommendation system that analyzes Steam games and finds similar games based on their tags, genres, categories, and user behavior. Using machine learning techniques, the project demonstrates:

- **Data visualization** for understanding game market patterns
- **Feature engineering** for creating meaningful game representations
- **Cosine similarity** for finding games with similar characteristics
- **Nearest Neighbors** algorithm for efficient recommendations

This project was developed as part of a creative machine learning assignment, showcasing the ability to:
- Work with real-world datasets (Steam games database)
- Perform comprehensive data analysis and visualization
- Build a fully functional ML-based recommendation system
- Create production-ready documentation

### Task Description

This project was created as part of a creative assignment with the following requirements:

- A classical machine learning problem
- Comprehensive data visualization demonstration
- A complete, working solution suitable for resume/GitHub
- Original solution (not borrowed from GitHub, Kaggle, Habr, etc.)
- Using public datasets
- Addressing real-world business needs

**Problem Statement:** The game industry is one of the largest entertainment sectors globally, with Steam being the leading digital distribution platform. Players often struggle to discover new games that match their preferences. This project creates an intelligent system to recommend games based on similarity, helping users discover titles they might enjoy.

### Dataset

**Source:** Steam Games Dataset (71,716 games)

**Key Features:**
- `AppID` - Unique Steam application identifier
- `Name` - Game title
- `Release date` - Release date
- `Tags` - User-defined game tags (comma-separated)
- `Genres` - Game genres (comma-separated)
- `Categories` - Steam categories (comma-separated)
- `Price` - Game price in USD
- `Positive/Negative` - Number of positive/negative reviews
- `Average playtime` - Average hours played
- `Metacritic score` - Critic rating
- `User score` - User rating
- `Achievements` - Number of achievements
- `Supported languages` - Available languages

**Data Statistics:**
- Initial dataset: 71,716 games
- After filtering: 14,448 quality games
- 109 engineered features
- Top 50 most popular tags
- 9 genres analyzed
- 15 most common categories

**Data Preprocessing:**
- Removed non-game items (editors, tools, DLC, soundtracks)
- Filtered games with minimum 100 reviews (1000 for free games)
- Engineered binary features for tags, genres, categories
- Created derived features (positive ratio, review counts, age indicators)
- Normalized features using L2 normalization

### Technologies & Tools

- **Python 3.11** - Programming language
- **Jupyter Notebook** - Interactive development environment
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computations
- **Scikit-learn** - Machine learning algorithms
  - `NearestNeighbors` - KNN-based recommendation
  - `normalize` - Feature normalization
  - `pairwise_distances` - Similarity calculations
- **Matplotlib** - Data visualization
- **Seaborn** - Statistical visualizations
- **Cosine Similarity** - Distance metric for recommendations

### Installation

#### Prerequisites
- Python 3.8 or higher
- Git
- Jupyter Notebook

#### Step-by-Step Setup

1. **Clone the repository**
```bash
git clone https://github.com/himynameisartem/Game_Style_Matcher.git
cd Game_Style_Matcher
```

2. **Create a virtual environment**
```bash
python -m venv venv
```

3. **Activate the virtual environment**
   - On macOS/Linux:
   ```bash
   source venv/bin/activate
   ```
   - On Windows:
   ```bash
   venv\Scripts\activate
   ```

4. **Install dependencies**
```bash
pip install -r requirements.txt
```

5. **Download the dataset**
   - The dataset `games.csv` should be placed in `data/raw/` directory
   - Due to file size, the dataset is in `.gitignore`
   - You can obtain the Steam games dataset from Kaggle or other public sources
   - Place your `games.csv` file in `data/raw/games.csv`

6. **Launch Jupyter Notebook**
```bash
jupyter notebook
```

7. **Open the notebook**
   - Navigate to `game_style_matcher.ipynb`
   - Run all cells to train the model

### Usage

#### Getting Recommendations

Once you've run the notebook, you can get game recommendations:

```python
# Get recommendations for a specific game
recommend('Far Cry')

# Output example:
# 🎮 Recommendations for 'Far Cry® 5':
#
#    1. Far Cry® 4
#       ⭐ 82.9% | 📊 Similarity: 0.906
#
#    2. Far Cry 3
#       ⭐ 90.1% | 📊 Similarity: 0.858
```

#### Key Functions

- `recommend(game_name, n=10)` - Get top N similar games
- `find_game(game_name)` - Search for a game in the database
- Model automatically filters out duplicate editions and versions

### Methodology

1. **Data Collection & Cleaning**
   - Loaded 71,716 games from Steam database
   - Removed non-game items and low-quality entries
   - Filtered for games with sufficient reviews

2. **Feature Engineering**
   - Extracted top 50 most popular tags (binary features)
   - Encoded all genres (binary features)
   - Encoded top 15 categories (binary features)
   - Created derived features:
     - Total reviews count
     - Positive review ratio
     - Years since release
     - Average playtime in hours
     - Language support count

3. **Data Visualization**
   - Top 20 most popular Steam tags
   - Top 10 most common genres
   - Top 15 categories distribution
   - Cosine distance distribution
   - Feature importance analysis

4. **Model Training**
   - Used `NearestNeighbors` with cosine similarity
   - L2-normalized all features
   - Trained on 14,448 quality games
   - Configured to find 11 nearest neighbors (excluding self)

5. **Recommendation Logic**
   - Finds similar games using cosine similarity
   - Filters out duplicate editions
   - Ranks by similarity score
   - Displays rating and similarity metrics

### Results

**Key Findings:**
- **Indie** is the most popular tag with 18,000+ games
- **Action** and **Casual** are the dominant genres
- Most games have **Single-player** as the primary category
- The recommendation system successfully identifies similar games with 80-95% similarity scores
- Filtered dataset of 14,448 games provides comprehensive coverage

**Visualizations:**
- Bar charts for tag/genre/category distributions
- Heatmaps for feature correlations
- Scatter plots for feature relationships
- Histograms for distance distributions

**Example Results:**
For "Far Cry® 5", the system recommends:
- Far Cry® 4 (90.6% similarity)
- Far Cry 3 (85.8% similarity)
- Homefront®: The Revolution (83.7% similarity)
- Red Dead Redemption 2 (81.8% similarity)

### Future Improvements

- [ ] Add collaborative filtering based on user reviews
- [ ] Implement content-based filtering using game descriptions (NLP)
- [ ] Create a web interface for the recommendation system
- [ ] Add price filtering and budget constraints
- [ ] Include multiplayer mode matching
- [ ] Add developer/publisher similarity
- [ ] Implement real-time game discovery
- [ ] Add seasonal and trending game detection
- [ ] Create game similarity heatmaps
- [ ] Deploy as a REST API service

### Repository Structure

```
Game_Style_Matcher/
│
├── data/
│   └── raw/
│       └── games.csv              # Steam games dataset (in .gitignore)
│
├── game_style_matcher.ipynb       # Main Jupyter notebook
├── requirements.txt               # Python dependencies
├── README.md                      # Project documentation
└── .gitignore                     # Git ignore rules
```

### Author

**Artem** - Machine Learning Enthusiast

This project demonstrates practical machine learning skills including:
- Data analysis and preprocessing
- Feature engineering
- Machine learning model development
- Data visualization
- Production-ready code documentation

---

## Русская версия

### Обзор проекта

Game Style Matcher — это интеллектуальная система рекомендаций, которая анализирует игры в Steam и находит похожие игры на основе их тегов, жанров, категорий и поведения пользователей. Используя методы машинного обучения, проект демонстрирует:

- **Визуализацию данных** для понимания закономерностей игрового рынка
- **Инженерию признаков** для создания осмысленных представлений игр
- **Косинусное сходство** для поиска игр с похожими характеристиками
- **Алгоритм ближайших соседей** для эффективных рекомендаций

Этот проект был разработан в рамках творческого задания по машинному обучению, демонстрируя способность:
- Работать с реальными датасетами (база данных игр Steam)
- Выполнять комплексный анализ и визуализацию данных
- Строить полностью функциональную ML-based систему рекомендаций
- Создавать продакшн-готовую документацию

### Описание задачи

Этот проект был создан в рамках творческого задания со следующими требованиями:

- Классическая задача машинного обучения
- Демонстрация комплексной визуализации данных
- Полное, работоспособное решение, пригодное для резюме/GitHub
- Оригинальное решение (не заимствованное с GitHub, Kaggle, Habr и т.д.)
- Использование публичных датасетов
- Решение реальных бизнес-задач

**Постановка проблемы:** Игровая индустрия — одна из крупнейших отраслей развлечений в мире, а Steam — ведущая платформа цифровой дистрибуции. Игроки часто испытывают трудности с поиском новых игр, соответствующих их предпочтениям. Этот проект создает интеллектуальную систему для рекомендации игр на основе схожести, помогая пользователям открывать для себя новые интересные игры.

### Датасет

**Источник:** Датасет игр Steam (71,716 игр)

**Ключевые признаки:**
- `AppID` - Уникальный идентификатор приложения Steam
- `Name` - Название игры
- `Release date` - Дата релиза
- `Tags` - Пользовательские теги игры (через запятую)
- `Genres` - Жанры игры (через запятую)
- `Categories` - Категории Steam (через запятую)
- `Price` - Цена игры в долларах США
- `Positive/Negative` - Количество положительных/отрицательных отзывов
- `Average playtime` - Среднее время игры в часах
- `Metacritic score` - Рейтинг критиков
- `User score` - Рейтинг пользователей
- `Achievements` - Количество достижений
- `Supported languages` - Доступные языки

**Статистика данных:**
- Исходный датасет: 71,716 игр
- После фильтрации: 14,448 качественных игр
- 109 созданных признаков
- Топ 50 самых популярных тегов
- 9 проанализированных жанров
- 15 наиболее распространенных категорий

**Предобработка данных:**
- Удалены не-игры (редакторы, инструменты, DLC, саундтреки)
- Отфильтрованы игры с минимум 100 отзывами (1000 для бесплатных)
- Созданы бинарные признаки для тегов, жанров, категорий
- Созданы производные признаки (доля положительных отзывов, количество отзывов, возрастные показатели)
- Нормализованы признаки с использованием L2-нормализации

### Технологии и инструменты

- **Python 3.11** - Язык программирования
- **Jupyter Notebook** - Интерактивная среда разработки
- **Pandas** - Манипуляции и анализ данных
- **NumPy** - Численные вычисления
- **Scikit-learn** - Алгоритмы машинного обучения
  - `NearestNeighbors` - Рекомендации на основе KNN
  - `normalize` - Нормализация признаков
  - `pairwise_distances` - Расчеты схожести
- **Matplotlib** - Визуализация данных
- **Seaborn** - Статистические визуализации
- **Косинусное сходство** - Метрика расстояния для рекомендаций

### Установка

#### Требования
- Python 3.8 или выше
- Git
- Jupyter Notebook

#### Пошаговая установка

1. **Клонировать репозиторий**
```bash
git clone https://github.com/himynameisartem/Game_Style_Matcher.git
cd Game_Style_Matcher
```

2. **Создать виртуальное окружение**
```bash
python -m venv venv
```

3. **Активировать виртуальное окружение**
   - На macOS/Linux:
   ```bash
   source venv/bin/activate
   ```
   - На Windows:
   ```bash
   venv\Scripts\activate
   ```

4. **Установить зависимости**
```bash
pip install -r requirements.txt
```

5. **Скачать датасет**
   - Датасет `games.csv` должен быть размещен в директории `data/raw/`
   - Из-за размера файла датасет находится в `.gitignore`
   - Вы можете получить датасет игр Steam с Kaggle или других публичных источников
   - Поместите ваш файл `games.csv` в `data/raw/games.csv`

6. **Запустить Jupyter Notebook**
```bash
jupyter notebook
```

7. **Открыть ноутбук**
   - Перейдите к `game_style_matcher.ipynb`
   - Запустите все ячейки для обучения модели

### Использование

#### Получение рекомендаций

После запуска ноутбука вы можете получить рекомендации по играм:

```python
# Получить рекомендации для конкретной игры
recommend('Far Cry')

# Пример вывода:
# 🎮 Recommendations for 'Far Cry® 5':
#
#    1. Far Cry® 4
#       ⭐ 82.9% | 📊 Similarity: 0.906
#
#    2. Far Cry 3
#       ⭐ 90.1% | 📊 Similarity: 0.858
```

#### Ключевые функции

- `recommend(game_name, n=10)` - Получить топ N похожих игр
- `find_game(game_name)` - Поиск игры в базе данных
- Модель автоматически фильтрует дубликаты изданий и версий

### Методология

1. **Сбор и очистка данных**
   - Загружено 71,716 игр из базы данных Steam
   - Удалены не-игры и низкокачественные записи
   - Отфильтрованы игры с достаточным количеством отзывов

2. **Инженерия признаков**
   - Извлечены топ 50 самых популярных тегов (бинарные признаки)
   - Закодированы все жанры (бинарные признаки)
   - Закодированы топ 15 категорий (бинарные признаки)
   - Созданы производные признаки:
     - Общее количество отзывов
     - Доля положительных отзывов
     - Годы с момента релиза
     - Среднее время игры в часах
     - Количество поддерживаемых языков

3. **Визуализация данных**
   - Топ 20 самых популярных тегов Steam
   - Топ 10 самых распространенных жанров
   - Распределение топ 15 категорий
   - Распределение косинусных расстояний
   - Анализ важности признаков

4. **Обучение модели**
   - Использован `NearestNeighbors` с косинусным сходством
   - Все признаки L2-нормализованы
   - Обучение на 14,448 качественных играх
   - Настроено на поиск 11 ближайших соседей (исключая саму игру)

5. **Логика рекомендаций**
   - Находит похожие игры используя косинусное сходство
   - Фильтрует дубликаты изданий
   - Ранжирует по оценке схожести
   - Отображает рейтинг и метрики схожести

### Результаты

**Ключевые выводы:**
- **Indie** — самый популярный тег с 18,000+ игр
- **Action** и **Casual** — доминирующие жанры
- Большинство игр имеют **Single-player** как основную категорию
- Система рекомендаций успешно идентифицирует похожие игры с оценками схожести 80-95%
- Отфильтрованный датасет из 14,448 игр обеспечивает широкое покрытие

**Визуализации:**
- Столбчатые диаграммы для распределений тегов/жанров/категорий
- Теплокарты для корреляций признаков
- Диаграммы рассеяния для отношений признаков
- Гистограммы для распределений расстояний

**Пример результатов:**
Для "Far Cry® 5" система рекомендует:
- Far Cry® 4 (90.6% схожесть)
- Far Cry 3 (85.8% схожесть)
- Homefront®: The Revolution (83.7% схожесть)
- Red Dead Redemption 2 (81.8% схожесть)

### Дальнейшие улучшения

- [ ] Добавить коллаборативную фильтрацию на основе отзывов пользователей
- [ ] Реализовать контентную фильтрацию используя описания игр (NLP)
- [ ] Создать веб-интерфейс для системы рекомендаций
- [ ] Добавить фильтрацию по цене и бюджетным ограничениям
- [ ] Включить сопоставление многопользовательских режимов
- [ ] Добавить схожесть разработчиков/издателей
- [ ] Реализовать обнаружение игр в реальном времени
- [ ] Добавить определение сезонных и трендовых игр
- [ ] Создать теплокарты схожести игр
- [ ] Развернуть как REST API сервис

### Структура репозитория

```
Game_Style_Matcher/
│
├── data/
│   └── raw/
│       └── games.csv              # Датасет игр Steam (в .gitignore)
│
├── game_style_matcher.ipynb       # Основной Jupyter ноутбук
├── requirements.txt               # Зависимости Python
├── README.md                      # Документация проекта
└── .gitignore                     # Правила игнорирования Git
```

### Автор

**Артем** - Энтузиаст машинного обучения

Этот проект демонстрирует практические навыки машинного обучения, включая:
- Анализ и предобработку данных
- Инженерию признаков
- Разработку моделей машинного обучения
- Визуализацию данных
- Продакшн-готовую документацию кода

---

**⭐ Если вам понравился этот проект, не забудьте поставить звезду!**
