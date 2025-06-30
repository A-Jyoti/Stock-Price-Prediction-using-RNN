# Stock  Price Prediction using RNN

## Project Workflow: Stock Price Prediction Using Stacked LSTM

1. **Data Collection**
   - Stock data for Apple Inc. (AAPL) is fetched using the `pandas_datareader` library and Tiingo API.
   - The data is saved as a CSV file for further processing.

2. **Data Preparation**
   - The CSV file is loaded into a pandas DataFrame.
   - Only the 'close' price column is used for prediction.
   - The closing price is plotted to visualize trends.

3. **Data Scaling**
   - The closing prices are normalized to the range [0, 1] using `MinMaxScaler` to improve LSTM performance.

4. **Train-Test Split**
   - The dataset is split into training (65%) and testing (35%) sets.

5. **Sequence Creation**
   - A helper function `create_dataset` converts the time series data into sequences suitable for LSTM input (X: previous 100 timesteps, Y: next value).
   - Data is reshaped to `[samples, time steps, features]` as required by LSTM layers.

6. **Model Building**
   - A stacked LSTM model is built using Keras Sequential API:
     - Three LSTM layers (first two return sequences, last one does not)
     - One Dense output layer
   - The model is compiled with Mean Squared Error loss and Root Mean Squared Error (RMSE) as a metric.

7. **Model Training**
   - The model is trained for 100 epochs with a batch size of 64, using the training set and validating on the test set.
   - Training and validation loss and RMSE are recorded.

8. **Performance Visualization**
   - Training and validation loss are plotted over epochs.
   - Training and validation RMSE are also plotted.

9. **Prediction and Evaluation**
   - The trained model predicts on both training and test data.
   - Predictions are transformed back to the original scale.
   - RMSE is calculated for both training and test predictions.

10. **Results Visualization**
    - The actual and predicted values are plotted for both training and test sets.
    - The model is used to predict the next 30 days, and these predictions are visualized alongside the actual data.

---
