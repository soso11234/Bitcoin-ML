Bit-coin data analysis.
Period: From 2024.03.31 to 2025.03.31 (12months) by Kraken
Using OHLCV


 
It is the heatmap of 4-hours bar chart of Bitcoin dataset. The correlation index among Open, High, Low, and Close is 1.00, indicating a perfect linear relationship. This is because the points are derived from the same price movement. As the market price shifts, each metric adjusts accordingly within the same interval. However, Volume and Trades do not have any linear relationship with the price sectors. It indicates that, the important factor of shifting price is not a volume or trades. Thus, we can check only what factors are affected by shifting market price in the factors of dataset.


 
Here is modified dataset, which is included Up, when the price was increased compared to previous datetime. Down, when the price was decreased compared to previous datetime.
Price_change is the percentage of shifting close price. 
Close_diff indicates the the difference between current close price and previous close price.
Volume_diff indicates the difference between current current volume and previous volume
Close_accel indicates the acceleration of shifting market close price compared to previous close price.
Volume_accel indicates the acceleration of shifting volume compared to previous volume.
Price_ave indicates 20-period simple moving average of the closing prices.
Volume_ave indicates 20-period simple moving average of the volume.
The volume_ave has weak linear relationship among Open, High, Low, Close, and Price_ave. However, it does not have any relationship with Up or Down, which is the direction of the market price. Therefore, the average volume can affect to strength of shifting market price. 

Then we can assume that the volume affects to strength of shifting market price. However, it does not have any linear relationship with the direction of market price. So that, it is one of the parts to maximize profit of trading Bitcoin. Therefore, the trading strategy should be focused on detecting the power of shifting market price with direction at the low market price. Because it is the direction of shifting market price is walking randomly. 
However, the problem of this strategy is that the shifting market price acceleration does not indicate change of direction of the market price. Because, if the price acceleration replaces from positive to minus, it does not mean, the market price is dropping. It still could increase, but slower than previous acceleration. Therefore, the price acceleration must be subpart to predict the market price direction. 

To validate this hypothesis, I implemented a Machine Learning-based trading model that integrates these indicators. By combining price acceleration, the model achieved significant performance improvements. The winning rate is 65.38%, average return rate is 0.24%, risk management is -1.38%, the maximum return rate is 2.30% for 3 months. The simulation starts with $100, and the result amount is $102.43. 

 

 
According to the new heatmap, 20-period simple moving average of the volume performs like trade, which means the average of individual person trade. Also, it relates to log transformation to the low prices. The purpose of log transformation to the low prices is to reduce heteroscedasticity. 





<seaborn.axisgrid.FacetGrid at 0x7af3429fec60>
 
According to the graph between the relationship between close_accel and price_change, when the close_accel is negative, the price_change, which is direction of the market price between current and previous close price, is also negative. Therefore, if we can detect the close_accel is positive, then we can make trade to make profit.

Therefore, the strategy of trading Bitcoin is that, using close_accel. If close_accel is negative, it means the market price is decreasing, otherwise, we can make the profit through trading Bitcoin.




