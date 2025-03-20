# WASP ODI Predictor

## Project Overview
This project implements the **Winning and Score Prediction (WASP)** model for One Day Internationals (ODIs), covering both **First Innings** and **Second Innings** predictions. The model provides real-time insights into score projections and winning probabilities based on historical data and match progression.

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
The project calculates key metrics separately for the first and second innings.

### **First Innings Prediction**
1. **R(b, w)**: The expected final score given the current ball number **b** and wickets lost **w**.
   \[ R(b, w) = E[FinalScore | Ball = b, Wickets = w] \]

2. **P(b, w)**: The probability of a wicket falling at a specific ball **b**, given **w** wickets lost.
   \[ P(b, w) = P(Wicket | Ball = b, Wickets = w) \]

Using these, the model estimates the projected total score for the batting team at the end of 50 overs.

### **Second Innings Prediction**
1. **Q(r, b, w)**: The probability of scoring **r** runs at a specific ball **b+1**, given **w** wickets lost.
   \[ Q(r, b, w) = P(Runs = r | Ball = b, Wickets = w) \]

2. **P(i, j, k)**: The probability of successfully chasing a target, where **i** is the remaining runs, **j** is the current ball number, and **k** is the number of wickets lost.
   \[ P(i, j, k) = P(Winning | RemainingRuns = i, Ball = j, Wickets = k) \]

These metrics allow the model to determine the probability of a successful chase given the current state of the match.

## Theory
The WASP model analyzes historical cricket data to determine scoring trends and wicket probabilities based on match progression. The first innings model predicts the final score, while the second innings model evaluates the likelihood of a successful chase. By dynamically computing **R(b, w)**, **P(b, w)**, **Q(r, b, w)**, and **P(i, j, k)**, the model provides real-time predictions for commentators, analysts, and fans.

## Requirements
To run this project, install the following dependencies:
```bash
pip install numpy pandas jupyter
```

## Usage
Run the Jupyter Notebook to process the dataset and generate predictions:
```bash
jupyter notebook WASP_ODI_Predictor.ipynb
```

## Author
Debdip Mukherjee
