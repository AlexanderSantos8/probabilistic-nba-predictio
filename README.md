# Probabilistic NBA Game Prediction

A mathematical and computational framework developed to analyze NBA game outcomes through probability theory, statistical modeling, Monte Carlo simulation, and machine learning. This project investigates whether data-driven methods can identify predictive patterns in professional basketball performance and improve game outcome forecasting.

The project was independently developed with a focus on designing and implementing custom predictive models, including Monte Carlo simulation systems, Elo-based rating models, logistic regression classifiers, and a feed-forward neural network architecture for NBA game prediction.

---

# Introduction

Sports prediction presents a challenging modeling problem due to the combination of team variability, randomness, injuries, and changing performance trends. This project explores the question:

**Can mathematical modeling and machine learning techniques identify reliable patterns in NBA game outcomes?**

To investigate this problem, I developed a simulated betting environment using a hypothetical $10,000 investment portfolio. Each predictive model was evaluated through money-line and over-under predictions across NBA matchups.

The primary prediction targets were:

- **Money-Line Predictions:** Predicting the probability of a team winning a matchup.
- **Over-Under Predictions:** Estimating total combined points scored by both teams.

---

# Modeling Framework and Methodology

The prediction system combines four independently developed models. Each model approaches the forecasting problem from a different mathematical perspective, allowing comparisons between statistical methods, simulations, and machine learning approaches.

---

# 1. Monte Carlo Score Simulation Model

I designed and implemented a Monte Carlo simulation framework to model NBA game outcomes by treating team scoring as probabilistic variables.

Team scores are modeled as:

\[
Score_{team} \sim N(\mu,\sigma^2)
\]

where:

- \( \mu \) represents expected team scoring performance based on historical scoring averages.
- \( \sigma \) represents game-to-game scoring variability.
- Team strength adjustments are incorporated to account for differences in overall performance.

For each matchup, the simulation generates between **50,000 and 100,000 simulated games** to estimate:

- Win probability
- Expected final scores
- Predicted scoring distributions
- Over-under probabilities

This simulation framework was fully implemented to analyze uncertainty and quantify the randomness inherent in individual NBA games.

---

# 2. Elo Rating and Offensive Strength Model

I implemented an adjusted Elo rating system to estimate matchup probabilities based on relative team strength.

The traditional Elo probability model is:

\[
P(\text{Team A wins}) =
\frac{1}{1+10^{(R_B-R_A)/400}}
\]

where:

- \(R_A\) represents Team A's rating.
- \(R_B\) represents Team B's rating.

To improve the baseline Elo system, I incorporated offensive efficiency adjustments:

\[
P_{win}
=
\text{Base Elo Probability}
\times
\frac{\text{Offensive Rating}_{team}}
{\text{Offensive Rating}_{opponent}}
\]

This allowed the model to account for differences between teams with similar Elo ratings but significantly different offensive capabilities.

---

# 3. Logistic Regression Prediction Model

I developed a supervised learning model using logistic regression to estimate win probabilities from statistical differences between teams.

The model predicts:

\[
P(\text{home win})
=
\frac{1}{1+e^{-(\beta_0+
\beta_1\Delta win\_pct+
\beta_2\Delta pts\_scored+
\beta_3\Delta pts\_allowed+
\beta_4\Delta PPG)}}
\]

Features include:

- Win percentage difference
- Average points scored difference
- Average points allowed difference
- Team scoring efficiency

The model provides a statistical baseline for comparison against more complex machine learning approaches.

---

# 4. Neural Network Prediction Model

I independently designed and implemented a feed-forward neural network to capture complex non-linear relationships between team statistics and game outcomes.

The neural network architecture was developed specifically for this project and includes:

- Multiple fully connected hidden layers
- ReLU activation functions
- Adaptive optimization using Adam
- Regularization techniques to reduce overfitting
- Sigmoid output layer for probability prediction

The network learns relationships between:

- Team offensive production
- Defensive performance
- Win percentage
- Scoring margins
- Historical matchup statistics

The neural network architecture was created, trained, and evaluated as part of this project to compare machine learning performance against traditional statistical models.

The neural network computes:

\[
h^{(1)} = f(W^{(1)}x+b^{(1)})
\]

\[
h^{(l)}
=
f(W^{(l)}h^{(l-1)}+b^{(l)})
\]

Final probability output:

\[
P(\text{team win})
=
\sigma(W^{(L)}h^{(L-1)}+b^{(L)})
\]

---

# Predictive Features

The models utilize a combination of team performance, statistical, and historical variables.

## Team Performance Metrics

- Margin of Victory (MOV)
  - Average point differential against opponents.

- Win Percentage
  - Historical success rate.

- Points Per Game
  - Offensive scoring capability.

- Points Allowed
  - Defensive performance.

## Shooting Metrics

Included variables:

- Two-point shooting percentage
- Three-point shooting percentage
- Free throw efficiency
- Opponent shooting percentages

## Additional Variables

- Average roster age
- Home attendance
- Draft position information

Teams without draft selections were assigned a value of 61 to represent missing draft data.

---

# Data and Technology Stack

## Datasets Used

### Games.csv

Contains historical NBA matchup information:

- Home and away teams
- Final scores
- Game outcomes

### Team Totals.csv

Contains season-level team statistics:

- Points per game
- Offensive averages
- Team performance indicators

### TeamStatistics.csv

Contains detailed statistical features used for machine learning training.

---

# Technical Implementation

The project was developed using Python with the following libraries:

```bash
pip install numpy pandas scikit-learn tensorflow matplotlib
```

Libraries used:

- NumPy — Numerical computation and simulations
- Pandas — Data processing and dataset management
- Scikit-learn — Logistic regression and machine learning tools
- TensorFlow/Keras — Neural network development and training
- Matplotlib — Visualization and statistical analysis

---

# Project Contributions

This project involved the complete development of a statistical and machine learning NBA prediction pipeline.

Major contributions include:

- Designed and implemented Monte Carlo simulation models for NBA outcomes.
- Developed an adjusted Elo rating system incorporating offensive strength.
- Built and trained a custom neural network architecture for game prediction.
- Created data-processing pipelines for NBA statistical datasets.
- Compared traditional statistical models against machine learning approaches.
- Evaluated prediction accuracy through simulated betting strategies.

---

# Objective

The goal of this project was to combine mathematical modeling, probability theory, and artificial intelligence to investigate the predictability of NBA outcomes.

The project demonstrates applications of:

- Probability and statistics
- Machine learning
- Neural networks
- Simulation methods
- Sports analytics
- Data-driven decision making
