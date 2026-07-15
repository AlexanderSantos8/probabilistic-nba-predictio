# Probabilistic NBA Game Prediction

A mathematical and computational framework developed to analyze NBA game outcomes using probability theory, statistical modeling, Monte Carlo simulations, and machine learning. This project investigates whether data-driven methods can identify predictive patterns in professional basketball performance and improve game outcome forecasting.

The project independently implements a complete NBA prediction pipeline, including custom Monte Carlo simulation models, Elo-based rating systems, statistical classifiers, and a feed-forward neural network designed and trained specifically for predicting NBA game outcomes.

---

# Introduction

Predicting professional sports outcomes is a challenging problem due to uncertainty, team variability, injuries, and performance fluctuations. This project explores the following question:

**Can mathematical modeling and machine learning identify meaningful patterns in NBA game outcomes?**

To investigate this problem, I developed a simulated sports betting environment using a hypothetical $10,000 investment portfolio. The prediction models were evaluated through money-line and over-under predictions across NBA matchups.

The primary prediction objectives were:

- **Money-Line Predictions:** Estimating the probability that a team wins a matchup.
- **Over-Under Predictions:** Forecasting the expected combined score of both teams.

---

# Modeling Framework and Methodology

The prediction system combines four independently developed models. Each model approaches NBA forecasting from a different mathematical perspective, allowing comparison between probabilistic simulation, traditional statistics, and machine learning methods.

---

# 1. Monte Carlo Score Simulation Model

I designed and implemented a Monte Carlo simulation framework to model the randomness of NBA scoring and estimate game outcomes.

Team scores are represented as probabilistic variables:

$$
Score_{team} \sim N(\mu,\sigma^2)
$$

where:

- $\mu$ represents expected team scoring performance based on historical Points Per Game (PPG).
- $\sigma$ represents game-to-game scoring variability.
- Team strength adjustments are incorporated to account for differences in overall performance.

For each matchup, the simulation generates between:

**50,000 and 100,000 simulated games**

to estimate:

- Win probability
- Expected final scores
- Score distributions
- Over-under probabilities

This simulation framework was fully developed to quantify uncertainty and model the randomness present in individual NBA games.

---

# 2. Elo Rating and Offensive Strength Adjustment Model

I implemented an adjusted Elo rating system to estimate matchup probabilities based on relative team strength.

The traditional Elo probability model is:

$$
P(\text{Team A wins})
=
\frac{1}{1+10^{(R_B-R_A)/400}}
$$

where:

- $R_A$ represents Team A's Elo rating.
- $R_B$ represents Team B's Elo rating.

To improve the traditional Elo model, I incorporated offensive strength adjustments:

$$
P_{win}
=
\text{Base Elo Probability}
\times
\frac{\text{Offensive Rating}_{team}}
{\text{Offensive Rating}_{opponent}}
$$

This adjustment allows the model to account for situations where teams have similar Elo ratings but significantly different offensive capabilities.

---

# 3. Logistic Regression Prediction Model

A supervised learning model was developed using logistic regression to estimate game-winning probabilities based on differences between team statistics.

The model predicts:

$$
P(\text{home win})
=
\frac{1}
{1+e^{-(\beta_0+
\beta_1\Delta win\_pct+
\beta_2\Delta pts\_scored+
\beta_3\Delta pts\_allowed+
\beta_4\Delta PPG)}}
$$

Input features include:

- Difference in win percentage
- Difference in points scored
- Difference in points allowed
- Difference in scoring efficiency

This model provides a statistical baseline for comparison against more complex machine learning approaches.

---

# 4. Feed-Forward Neural Network Model

I independently designed, implemented, trained, and evaluated a feed-forward neural network to capture complex non-linear relationships between NBA team statistics and game outcomes.

The neural network architecture was created specifically for this project and includes:

- Multiple fully connected hidden layers
- ReLU activation functions
- Adam optimization
- Adaptive learning rate adjustments
- Regularization techniques to reduce overfitting
- Sigmoid output layer for probability prediction

The neural network learns relationships between:

- Offensive production
- Defensive performance
- Win percentage
- Scoring margins
- Historical team statistics

The hidden-layer calculations are:

$$
h^{(1)} = f(W^{(1)}x+b^{(1)})
$$

Additional hidden layers are computed as:

$$
h^{(l)}
=
f(W^{(l)}h^{(l-1)}+b^{(l)})
$$

The final output layer produces the probability of victory:

$$
P(\text{team win})
=
\sigma(W^{(L)}h^{(L-1)}+b^{(L)})
$$

The neural network was developed and optimized as part of this project to compare artificial intelligence methods against traditional statistical models.

---

# Predictive Features

The models utilize a combination of historical team performance metrics and statistical variables.

## Team Performance Metrics

### Margin of Victory (MOV)

Average point differential between a team and its opponents.

### Win Percentage

Historical success rate used as an indicator of team strength.

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

Teams without draft selections were assigned a value of:

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
| NumPy | Numerical calculations and simulations |
| Pandas | Data processing and dataset management |
| Scikit-learn | Logistic regression and machine learning tools |
| TensorFlow/Keras | Neural network creation and training |
| Matplotlib | Visualization and analysis |

---

# Project Contributions

This project involved the complete development of a mathematical and machine learning NBA prediction system.

Major contributions include:

- Designed and implemented Monte Carlo simulations for NBA game outcomes.
- Created probability models to estimate win and scoring distributions.
- Developed an adjusted Elo rating system incorporating offensive strength.
- Built and trained a custom neural network architecture.
- Created data-processing pipelines for NBA statistical datasets.
- Compared traditional statistical approaches with machine learning models.
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
