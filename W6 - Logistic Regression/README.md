# # W6 - Assignments

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QRBnZAm2XXmpBqHD-nOKvrXs9GZxWUSA#scrollTo=2Amlbf8BvIe5)


**🧡ทบทวน Logistic Regression ด้วย application**

- Initial code : https://github.com/ekaratnida/Applied-machine-learning/blob/master/Week05-Logistic/Stock_forecast.ipynb
- Implement use case : https://blog.quantinsti.com/machine-learning-logistic-regression-python/


**🧡Code Overview**

![Alt text](https://github.com/KK-PU/KK-PU-DADS6004_ML-4/blob/main/W6%20-%20Logistic%20Regression/Code-Overview.png)


## Create Trading Strategy Using The Model

We will predict the signal to buy (1) or sell (-1) and calculate the cumulative Nifty 50 returns for the test dataset. Next, we will calculate the cumulative strategy return based on the signal predicted by the model in the test dataset. We will also plot the cumulative returns.


    df['Predicted_Signal'] = model.predict(X)
    df['Nifty_returns'] = np.log(df['Close']/df['Close'].shift(1))
    Cumulative_Nifty_returns = np.cumsum(df[split:]['Nifty_returns'])
    
    df['Startegy_returns'] = df['Nifty_returns']* df['Predicted_Signal'].shift(1)
    Cumulative_Strategy_returns = np.cumsum(df[split:]['Startegy_returns'])
    
    plt.figure(figsize=(10,5))
    plt.plot(Cumulative_Nifty_returns, color='r',label = 'Nifty Returns')
    plt.plot(Cumulative_Strategy_returns, color='g', label = 'Strategy Returns')
    plt.legend()
    plt.show()

![Alt text](https://github.com/KK-PU/KK-PU-DADS6004_ML-4/blob/main/W6%20-%20Logistic%20Regression/download.png)
