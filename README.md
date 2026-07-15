# Probabilistic NBA Game Prediction

A mathematical and computational framework developed to analyze NBA game outcomes using probability theory, statistical modeling, Monte Carlo simulations, and machine learning.

This project investigates whether data-driven methods can identify predictive patterns in professional basketball performance and improve game outcome forecasting.

The project independently implements a complete NBA prediction pipeline, including custom Monte Carlo simulation models, Elo-based rating systems, statistical classifiers, and a feed-forward neural network designed, trained, and evaluated specifically for NBA game prediction.

---

# Introduction

Predicting professional sports outcomes is a challenging problem due to randomness, injuries, team variability, and changing performance trends.

This project explores the following question:

**Can mathematical modeling and machine learning identify meaningful patterns in NBA game outcomes?**

To investigate this problem, I developed a simulated sports betting environment using a hypothetical $10,000 investment portfolio. Each prediction model was evaluated through money-line and over-under predictions across NBA matchups.

The primary prediction objectives were:

- Money-Line Predictions: Estimating the probability that a team wins a matchup.
- Over-Under Predictions: Forecasting the expected combined score of both teams.

---

# Modeling Framework and Methodology

The prediction system combines four independently developed models. Each model approaches NBA forecasting from a different mathematical perspective, allowing comparison between simulation methods, statistical models, and artificial intelligence approaches.

---

# 1. Monte Carlo Score Simulation Model

I designed and implemented a Monte Carlo simulation framework to model NBA scoring uncertainty and estimate game outcomes.

Team scores are represented as probabilistic variables:

```
Score_team ~ Normal(μ, σ²)
```

where:

- μ represents expected team scoring performance based on historical Points Per Game (PPG).
- σ represents game-to-game scoring variability.
- Team strength adjustments are included to account for differences in performance.

For each matchup, the simulation generates:

```
50,000 - 100,000 simulated games
```

to estimate:

- Win probability
- Expected final scores
- Score distributions
- Over-under probabilities

This simulation framework was independently developed to quantify uncertainty and model the randomness present in individual NBA games.

---

# 2. Elo Rating and Offensive Strength Adjustment Model

I implemented an adjusted Elo rating system to estimate matchup probabilities based on relative team strength.

The traditional Elo probability model:

```
P(Team A wins) =
1 / (1 + 10^((R_B - R_A) / 400))
```

where:

```
R_A = Team A Elo rating
R_B = Team B Elo rating
```

To improve the traditional Elo model, I incorporated offensive strength adjustments:

```
P_win =
Base Elo Probability ×
(Offensive Rating of Team / Offensive Rating of Opponent)
```

This adjustment allows the model to account for teams with similar Elo ratings but different offensive capabilities.

---

# 3. Logistic Regression Prediction Model

I developed a supervised machine learning model using logistic regression to estimate game-winning probabilities.

The probability equation:

```
P(home win) =
1 / (1 + e^-(β0 + β1Δwin_pct + β2Δpts_scored + β3Δpts_allowed + β4ΔPPG))
```

The model uses statistical differences between teams, including:

- Win percentage difference
- Points scored difference
- Points allowed difference
- Scoring efficiency difference

This model provides a statistical baseline for comparison against more complex machine learning approaches.

---

# 4. Feed-Forward Neural Network Model

I independently designed, implemented, trained, and evaluated a feed-forward neural network to capture complex non-linear relationships between NBA statistics and game outcomes.

The neural network architecture was created specifically for this project and includes:

- Multiple fully connected hidden layers
- ReLU activation functions
- Adam optimization
- Adaptive learning rate adjustments
- Regularization techniques
- Sigmoid output layer for probability prediction

The neural network learns relationships between:

- Offensive production
- Defensive performance
- Win percentage
- Scoring margin
- Historical team statistics

The neural network calculations are represented as:

```
h(1) = f(W(1)x + b(1))
```

Additional hidden layers:

```
h(l) = f(W(l)h(l-1) + b(l))
```

Final prediction output:

```
P(team win) =
sigmoid(W(L)h(L-1) + b(L))
```

The neural network architecture, training process, and evaluation pipeline were fully developed as part of this project to compare artificial intelligence methods against traditional statistical models.

---

# Predictive Features

The models use a combination of historical team performance metrics and statistical variables.

## Team Performance Metrics

### Margin of Victory (MOV)

Average point differential between a team and its opponents.

### Win Percentage

Historical success rate used as a measure of team strength.

### Points Per Game (PPG)

Average offensive scoring production.

### Points Allowed

Defensive performance measurement.

---

## Shooting Metrics

The models incorporate:

- Two-point shooting percentage
- Three-point shooting percentage
- Free throw efficiency
- Opponent shooting percentages

---

## Additional Variables

Additional features include:

- Average roster age
- Home attendance
- Draft position information

Teams without draft selections were assigned:

```
61
```

to represent missing draft information.

---

# Data and Technology Stack

## Datasets Used

### Games.csv

Contains historical NBA game information:

- Home team
- Away team
- Final score
- Game result

---

### Team Totals.csv

Contains season-level team statistics:

- Points per game
- Offensive production
- Team averages

---

### TeamStatistics.csv

Contains detailed statistical features used for machine learning training.

---

# Technical Implementation

The project was developed using Python.

Required libraries:

```bash
pip install numpy pandas scikit-learn tensorflow matplotlib
```

Technology stack:

| Library | Purpose |
|---|---|
| NumPy | Numerical computation and simulations |
| Pandas | Data processing and dataset management |
| Scikit-learn | Logistic regression and machine learning models |
| TensorFlow/Keras | Neural network development and training |
| Matplotlib | Visualization and statistical analysis |

---

# Project Contributions

This project involved the complete development of a mathematical and machine learning NBA prediction system.

Major contributions include:

- Designed and implemented Monte Carlo simulations for NBA game outcomes.
- Created probabilistic scoring models to estimate game uncertainty.
- Developed an adjusted Elo rating system incorporating offensive strength.
- Built and trained a custom feed-forward neural network architecture.
- Created data-processing pipelines for NBA statistical datasets.
- Compared statistical models against machine learning approaches.
- Evaluated predictions using simulated betting strategies.

---

# Objective

The objective of this project was to combine mathematics, statistics, and artificial intelligence to study the predictability of NBA outcomes.

This project demonstrates applications of:

- Probability theory
- Statistical modeling
- Monte Carlo simulation
- Neural networks
- Machine learning
- Sports analytics
- Data-driven decision making
