Bitcoin data analysis.
Period: From 2024.03.31 to 2025.03.31 (12months) by Kraken
Using OHLCV

<img width="975" height="901" alt="image" src="https://github.com/user-attachments/assets/d50ea159-e728-4fe0-98d8-9279378bad12" />

 
It is the heatmap of a 4-hour bar chart of the Bitcoin dataset. The correlation index among Open, High, Low, and Close is 1.00, indicating a perfect linear relationship. This is because the points are derived from the same price movement. As the market price shifts, each metric adjusts accordingly within the same interval. However, Volume and Trades do not have any linear relationship with the price sectors. It indicates that the important factor of shifting price is not volume or trades. Thus, we can check only what factors are affected by the shifting market price in the factors of dataset.


 <img width="975" height="889" alt="image" src="https://github.com/user-attachments/assets/41148b0f-52d8-4898-9d54-38a3f0140152" />

Here is the modified dataset, which is included Up, when the price was increased compared to the previous datetime. Down, when the price was decreased compared to the previous date.
Price_change is the percentage of shifting close price. 
Close_diff indicates the difference between the current close price and the previous close price.
Volume_diff indicates the difference between current current volume and the previous volume.
Close_accel indicates the acceleration of the shifting market close price compared to the previous close price.
Volume_accel indicates the acceleration of shifting volume compared to the previous volume.
Price_ave indicates a 20-period simple moving average of the closing prices.
Volume_ave indicates a 20-period simple moving average of the volume.
The volume_ave has a weak linear relationship with Open, High, Low, Close, and Price_ave. However, it does not have any relationship with Up or Down, which is the direction of the market price. Therefore, the average volume can affect to strength of shifting market price. 

Then we can assume that the volume affects to strength of shifting market price. However, it does not have any linear relationship with the direction of the market price. So, it is one of the parts to maximize profit from trading Bitcoin. Therefore, the trading strategy should be focused on detecting the power of shifting market price with direction at the low market price. Because it is the direction of the shifting market price is walking randomly. 
However, the problem with this strategy is that the shifting market price acceleration does not indicate a change in the direction of the market price. Because if the price acceleration replaces from positive to minus, it does not mean the market price is dropping. It still could increase, but slower than the previous acceleration. Therefore, the price acceleration must be a part of predicting the market price direction. 

To validate this hypothesis, I implemented a Machine Learning-based trading model that integrates these indicators. By combining price acceleration, the model achieved significant performance improvements. The winning rate is 65.38%, the average return rate is 0.24%, the risk management is -1.38%, and the maximum return rate is 2.30% for 3 months. The simulation starts with $100, and the result amount is $102.43. 

<img width="975" height="889" alt="image" src="https://github.com/user-attachments/assets/39da5ba0-5fe5-4312-a720-6dea1a02e853" />


 
According to the new heatmap, a 20-period simple moving average of the volume performs like a trade, which means the average of a person's trade. Also, it relates to the log transformation of the low prices. The purpose of the log transformation of the low prices is to reduce heteroscedasticity. 




<img width="735" height="734" alt="image" src="https://github.com/user-attachments/assets/22fc2bca-dcdb-40c4-b2d4-5d429d6f2d78" />

 
According to the graph between the relationship between close_accel and price_change, when the close_accel is negative, the price_change, which is the direction of the market price between the current and previous close price, is also negative. Therefore, if we can detect that the close_accel is positive, then we can make a trade to make a profit.

Therefore, the strategy of trading Bitcoin is to use close_accel. If close_accel is negative, it means the market price is decreasing; otherwise, we can make a profit through trading Bitcoin.




