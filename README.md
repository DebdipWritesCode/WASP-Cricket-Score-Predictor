# WASP ODI First Innings Predictor

## Project Overview
This project implements the **Winning and Score Prediction (WASP)** model for One Day Internationals (ODIs), specifically focusing on the first innings. The model predicts the final score of the batting team based on historical data and match progression.

## Dataset
The analysis is performed using a cricket dataset that includes:
- **MatchNo**: Unique match identifier
- **Innings**: Indicates 1st or 2nd innings
- **Over**: Current over and ball
- **Runs_Total**: Runs scored on the ball
- **Score**: Cumulative score
- **Wickets**: Wickets lost
- **Wicket_ball**: Binary (1 if a wicket fell, 0 otherwise)
- **Ball_b**: Sequential ball number

## WASP Formulae
The project calculates the following key metrics:

1. **R(b, w)**: The average runs scored at a specific ball number **b** and given wickets lost **w**.
   \[ R(b, w) = E[FinalScore | Ball = b, Wickets = w] \]

2. **P(b, w)**: The probability of a wicket falling at a specific ball **b** given **w** wickets lost.
   \[ P(b, w) = P(Wicket | Ball = b, Wickets = w) \]

These metrics help estimate the final score prediction for the first innings.

## Theory
The WASP model works by analyzing historical cricket data to determine scoring trends and wicket probabilities based on match progression. By computing **R(b, w)** and **P(b, w)** dynamically, the model estimates the expected final score. The approach assumes that batting conditions remain similar across matches, making it a useful predictor for first-innings scores. The WASP algorithm is particularly useful in providing real-time insights during live matches, aiding commentators and analysts in score projections.

## Requirements
To run this project, install the following dependencies:
```bash
pip install numpy pandas jupyter
```

## Usage
Run the Jupyter Notebook to process the dataset and generate predictions:
```bash
jupyter notebook WASP_ODI_First_Innings.ipynb
```

## Author
Debdip Mukherjee

