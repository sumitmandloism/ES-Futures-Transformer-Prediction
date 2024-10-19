# ES Futures Transformer-based Prediction Model

This project involves creating a Transformer-based model using TensorFlow 2.14.0 to predict the return of the next 15-minute candle for S&P 500 E-mini Futures (ES). The model is trained using OHLCV data and is backtested using vectorbt to evaluate performance.

## Installation
### Prerequisites:
Python 3.8+

Required Libraries:
```bash
tensorflow==2.14.0
vectorbt
pandas_ta
matplotlib
pandas
numpy

```
Install dependencies using:

```bash
pip install -r requirements.txt
```
### Project Structure
```bash
.
├── data/                          # Directory containing the input data
│   └── US500M15.csv               # ES futures 15-minute OHLCV data
├── model/                         # Directory to save the trained model
│   └── es_transformer_model/      # Saved Keras model in SavedModel format
├── backtest/                      # Backtesting results
│   └── backtest_results.html      # HTML file with performance metrics and equity curve
├── scripts/
│   ├── data_preparation.py        # Script for data loading and preprocessing
│   ├── transformer_model.py       # Script for creating and training the Transformer model
│   ├── backtesting.py             # Script for backtesting using vectorbt
├── requirements.txt               # Dependencies for the project
├── README.md                      # This file
└── technical_document.md          # Technical document with detailed model information

```

## How to run:
### Data Preparation:
   Ensure the US500M15.csv file (containing OHLCV data) is in the data/ folder.

   Run the data preparation script to load and preprocess data:

    python scripts/data_preparation.py

### Training the Model:
Run the model training script:

     python scripts/transformer_model.py
The trained model will be saved in the model/ directory.

### Backtesting:
Run the backtesting script to evaluate the model performance using vectorbt: 
 
    python scripts/backtesting.py
The backtesting results will be saved in backtest/backtest_results.html.
## How to Use the Model:

```python
from tensorflow.keras.models import load_model
model = load_model('model/es_transformer_model')

```
Use the model for predictions by passing OHLCV data with a similar format as during training.
## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

