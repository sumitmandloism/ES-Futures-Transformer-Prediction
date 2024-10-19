## 1. Introduction:
This document provides a technical overview of the Transformer-based model for predicting ES futures returns. It includes the design choices, model architecture, training process, and potential improvements.

## 2. Model Architecture:
The model is a Transformer-based time series predictor.

### Input features: 
Open, High, Low, Close, and Volume (OHLCV) on a 15-minute time frame.
### Output: 
Predicted return for the next candle.
### Transformer Architecture:

Embedding Dimension: 64


Number of Attention Heads: 8

Feed-Forward Network Dimension: 128

Transformer Blocks: 4

Sequence Length (window): 50 timesteps (about 12.5 hours of data)

The model architecture was inspired by natural language processing models, adapting the multi-head attention mechanism for time series data to capture temporal dependencies between OHLCV values.

## 3. Data Preprocessing:
### Data Source: 
ES futures OHLCV data (meta-trader_historical-data)

### Feature Engineering: 
A sliding window approach is used to split the time series data into sequences of 50 timesteps.

### Normalization:
 StandardScaler was used to normalize the features to zero mean and unit variance.

### Returns:
 Calculated as the percentage change of the close price shifted back by 2 timesteps to predict the next candle's return.
## 4. Training Process:
Loss Function: Mean Squared Error (MSE), since the task is a regression problem.

Optimizer: Adam optimizer with default parameters.

Callbacks:
Early Stopping: Stops training when validation loss no longer improves for 10 consecutive epochs.

Learning Rate Scheduler: Reduces the learning rate by a factor of 0.2 if the validation loss plateaus.
## 5. Backtesting Approach:
Backtesting Tool: vectorbt

Entry/Exit Signals: Based on the predicted returns (long position if return > 0, exit otherwise).

Performance Metrics: Includes Sharpe ratio, max drawdown, and return distribution.

Equity Curve: Visualizes the strategy’s cumulative returns over time.

## 6. Design Choices & Hyperparameters:
Embedding Dimension: 64, chosen based on a balance between model complexity and the size of the dataset.

Attention Heads: 8 heads allow the model to capture different dependencies in the OHLCV data.

Sequence Length: 50 timesteps chosen to provide enough historical context without overfitting.

Batch Size: 32, chosen empirically for efficient training.

## 7. Potential Areas for Improvement:
Hyperparameter Tuning: Further optimization of attention heads, embedding dimension, and window size could improve model accuracy.

Alternative Architectures: Consider experimenting with CNN-LSTM hybrid models for capturing both local and temporal patterns.

Feature Engineering: Add additional features such as technical indicators (e.g., moving averages) to enhance model input.
