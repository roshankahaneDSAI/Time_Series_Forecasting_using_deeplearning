
# 📈 Time Series Demand Forecasting

This repository explores multiple deep-learning and statistical approaches for **time-series demand forecasting**, including:

* **LSTM (Stacked LSTM)**
* **GRU (Stacked GRU)**
* **Seq2Seq LSTM (Encoder–Decoder)**
* **Prophet**

The project uses **Keras** for deep-learning model development and **Prophet** for additive-trend forecasting.
The dataset used is the monthly international airline passengers dataset from Jason Brownlee’s collection.

Dataset:
[https://raw.githubusercontent.com/jbrownlee/Datasets/master/airline-passengers.csv](https://raw.githubusercontent.com/jbrownlee/Datasets/master/airline-passengers.csv)
Tutorial reference:
[https://machinelearningmastery.com/time-series-prediction-lstm-recurrent-neural-networks-python-keras/](https://machinelearningmastery.com/time-series-prediction-lstm-recurrent-neural-networks-python-keras/)

---

## 🚀 Models Implemented

### 1️⃣ Two-Layer Stacked LSTM Regression

Notebook: `stacked_lstm_regression.ipynb`

**Training setup:**

* Input window: past **12 months**
* Output: **next 1 month**

**Performance:**

* RMSE: **22.66**
* MAE: **18.28**

The model effectively captures seasonality and rising trends.

<img src="https://user-images.githubusercontent.com/30923675/78865607-dc5d7d00-7a78-11ea-95ea-13a8f25a57c0.png" width="600"/>

---

### 2️⃣ Two-Layer Stacked GRU Regression

Notebook: `stacked_gru_regression.ipynb`

**Training setup:**

* Same as LSTM (12 → 1 prediction)

**Performance:**

* RMSE: **22.47**
* MAE: **18.16**

GRU performs slightly better than LSTM.

<img src="https://user-images.githubusercontent.com/30923675/78866401-41fe3900-7a7a-11ea-985f-75fdb9ddcd7b.png" width="600"/>

---

### 3️⃣ Seq2Seq LSTM (Encoder–Decoder Architecture)

Notebook: `seq2seq_lstm.ipynb`

Inspired by Uber’s paper
**"Deep and Confident Prediction for Time Series Forecasting"**
Blog: [https://eng.uber.com/neural-networks-uncertainty-estimation/](https://eng.uber.com/neural-networks-uncertainty-estimation/)
Paper: [https://arxiv.org/pdf/1709.01907.pdf](https://arxiv.org/pdf/1709.01907.pdf)

**Training setup:**

* Encoder input: `t → t+12`
* Decoder input: `t+6 → t+12`
* Output: next **6 months (t+13 → t+18)**

Evaluated on **one-step** and **six-step** predictions.

#### 🔹 Next 1-Month Forecast

* RMSE: **19.38**
* MAE: **15.97**

<img src="https://user-images.githubusercontent.com/30923675/78984666-caa3d480-7b61-11ea-9f9e-78534a44cf8b.png" width="600"/>

#### 🔹 Next 6-Month Forecast

* RMSE: **21.51**
* MAE: **18.21**

<img src="https://user-images.githubusercontent.com/30923675/78984671-cd9ec500-7b61-11ea-94dd-23def3eb7735.png" width="600"/>

---

### 4️⃣ Prophet Model

Notebook: `prophet_model.ipynb`

Prophet is robust for trend + seasonality modeling but struggles with strong nonlinear increasing amplitude.

**Performance:**

* RMSE: **40.36**
* MAE: **31.17**

<img src="https://user-images.githubusercontent.com/30923675/78988604-5f133480-7b6c-11ea-8285-d5e24401a5c7.png" width="600"/>

---

## 📊 Summary of Findings

| Model                | RMSE  | MAE   | Notes                         |
| -------------------- | ----- | ----- | ----------------------------- |
| **Stacked LSTM**     | 22.66 | 18.28 | Good baseline DL model        |
| **Stacked GRU**      | 22.47 | 18.16 | Slightly better than LSTM     |
| **Seq2Seq (1-step)** | 19.38 | 15.97 | Best short-horizon predictor  |
| **Seq2Seq (6-step)** | 21.51 | 18.21 | Strong multi-step forecasting |
| **Prophet**          | 40.36 | 31.17 | Underfits growing trend       |

Seq2Seq LSTM provides the best performance, especially for multi-step forecasting.

---

## 🧠 Technologies Used

* Python
* Keras (TensorFlow backend)
* Prophet
* NumPy, Pandas, Matplotlib
* Jupyter Notebook

---

## 📁 Repository Structure

```
.
┣━━ stacked_lstm_regression.ipynb
┣━━ stacked_gru_regression.ipynb
┣━━ seq2seq_lstm.ipynb
┣━━ prophet_model.ipynb
┣━━ README.md
```

---

## 👨‍💻 Author

Roshan kahane Data scientist | AI/ML Engineer | Time Series Specialist