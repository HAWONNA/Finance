## ** Project Title: Forecasting Price Trends Using Hourly Data through Conv1D + LSTM Architectures**

**Project Description:**  
Numerous studies have demonstrated the efficacy of Conv1D and LSTM architectures in time series forecasting. Motivated by these findings, this project seeks to investigate the performance of these models when applied to real-world financial market indices. Specifically, the hourly data of five major global indices—S&P 500, NASDAQ, KOSPI 200, Nikkei, and DAX—were collected as input data to forecast their future trends. Among these, the DAX index provided the most comprehensive hourly sample data, thus becoming the primary focus of this study’s time series forecasting using the Conv1D + LSTM model.

To preprocess the data for deep neural network training, a rolling window approach was employed. Each segment comprised 9-hour intervals, with the model trained on these 9-hour windows to predict the subsequent t+9 hours. As a result, the input data was reshaped into 3D tensors with the following dimensions: **X_train**: (1696, 9, 1), **Y_train**: (1696, 9, 1), **X_test**: (28, 9, 1), and **Y_test**: (28, 9, 1). 

The Conv1D layers were then utilized to transform the input channels from 9 to 1024, 512, 256, and eventually to 128. This transformed output was passed through a single LSTM layer, where the feature size remained constant. The Conv1D layers served to extract critical features from the time series data, gradually reducing the input’s sequence length while increasing the channel count to 128. The LSTM layer then learned the temporal dependencies within the transformed data, allowing the model to predict future values.

Additionally, Teacher Forcing was employed to dynamically select between the true values and the model’s predictions as input to the decoder, ensuring robust prediction over the specified **output_window**. To enhance the model’s generalization ability, K-Fold Cross-Validation (with 8 folds) was utilized during training. The Adam optimizer was employed for its adaptive learning rate and efficient optimization capabilities.

**References:**  
Elsworth, S., & Güttel, S. (2020). Time series forecasting using LSTM networks: A symbolic approach. *arXiv preprint arXiv:2003.05672*.
