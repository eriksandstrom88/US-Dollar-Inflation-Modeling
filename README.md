# US-Dollar-Inflation-Modeling

## Summary
- 4 Models created so far with one in progress; several more planned
- Created models include 3 relatively basic neural networks and 1 Deep Neural Network
- Deep Neural Network predicted inflation (as measured by CPI) EXACTLY for Q1 2021
- Model in progress is a custom model based on my dissection of the Quantity Theory of Money
- Planned models include: SVM, MARS, various linear regression models, ensemble model by economic sector

## Model 4: Deep Neural Network using Keras

### Grade: A-

This model performs the best yet, having predicted CPI for the most recent quarter for which all data has been released (4/1/2021) with perfect accuracy--predicted value: 266.83; actual value: 266.83.  The reason it gets an A- is that it predicted a much higher CPI for 4/1/2020 than the actual value, which I attribute to the bizarre conditions surrounding the start of the COVID-19 pandemic. I suspect the inputs for personal savings and commercial bank loans are responsible given their high volatility relative to the other inputs (see line chart below) in April of 2020.  The model was trained on 11 variables: M2 Money Supply, Federal Debt, Government Expenditures, Federal Funds Rate, Commercial Bank Loans (combined commercial/industrial loans and consumer loans), Net Exports, Real GDP, Reserve Balances at Depository Institutions, Unemployment Rate, Personal Savings, and  Producer Price Index for All Commodities.  There are 2 hidden layers in the model, composed of 100 neurons each, and the model was trained using 100 epochs, eventually reaching a MSE of 0.0000265 for variables scaled on a 0 to 1 scale using SK-Learn's MinMaxScaler function.

![image](https://user-images.githubusercontent.com/75816400/137207761-ad6ddc26-5d50-40db-8ea9-df9401cb7d38.png)
![image](https://user-images.githubusercontent.com/75816400/137209083-de6f3b7c-d949-405f-98a4-67089f3458ac.png)

## Model 3: Neural Network Regression using Keras - scaled input and output values

#### Grade: B

After training the model on SK-lean's MinMaxScalar scaled values for all predictors, the model predicted CPI for 4/1/2020 to be 250.3, when the actual value is 256.192.  The previous model predicted 271.97.  The scaled data led to a big improvement in accuracy.  For the second test, the model predicted CPI for 4/1/2021 to be 262.52, when the actual value is 266.832.  The previous model predicted 277.64.  This is also a huge improvement with scaled data.  These improvements are impressive given the massive changes in trends of the input variables starting after 2/1/2020.

## Model 5 (in progress): Custom Model, Quantity Theory of Money Variation

### Grade: TBD

The Quantity Theory of Money (QTM) is a very general model relating the money supply and how fast it moves to the price level and level of output in the economy.  The equation is MV = PY, wher M is the money supply, V is the velocity of money (an average of how many times each dollar in the money supply changes hands in a given time period, usually a year), P is an index for the price level, and Y is output (essentially GDP).  So, for example, if the money supply increases, while velocity and output stay the same, the price level would have to increase to balance the equation because more dollars are competing for the same number of goods and services.  There are numerous factors that can affect each of these four variables individually--they are not each isolated to this equation, which makes them incredibly hard to model.  Given the massive increases in M1 and M2 money supplies in recent years while at the same time GDP has grown modestly, why hasn't the overall price level increased to match the increases in money supply?  

This is a question puzzling many economists.  There are many possible explanations:
 - As our trade deficit has grown over the last several decades, lots of the new money created has flowed out of the country, so it's not affecting prices domestically
 - Velocity is typically calculated as a residual.  We can measure money supply, prices and output, but it is hard to measure velocity, so it is calculated as what's left over.  Essentially, V = PY/M.  Economists used to assume that velocity was constant, yet that is not true.  I wonder how velocity is affected by age demographics (do young people spend faster than old) and wealth gaps (as wealth has accumulated among the wealthiest in our society, do the spend it more slowly than those living paycheck-to-paycheck).  If velocity slows for these reasons, that could explain prices increasing more slowly than the difference between growth in the money supply and growth in output.
 - Inflation expectations play a large role in the salaries people demand and how quickly they want to spend money.  If they expect the dollars in their bank account will be worth less one month from now than they are today, they will spend the money while goods are relatively cheaper.
 - Money supplies have increased most rapidly during times of crisis like the 2008 financial crisis and the COVID-19 pandemic, yet because the dollar is viewed as "safe" around the world, many people demand more dollars during these times of crisis, which holds up the value of the dollar.
 - Energy, especially oil, have a large influence on prices because they play a role in manufacturing, supply chain transportation, and quality of life.  The United States shale boom led to a drastic decrease in global oil prices, which has also helped to hold down prices.
 - Finally much of the money that has been created through federal stimulus and through the Federal Reserve's Quantitative Easing policies is being held as excess reserves in banks.  The increase in reserves held is astonishing.  This increase is in part due to a low demand for loans, while at the same time the Federal Reserve is paying interest on reserves, so banks are holding them to earn interest.
 
All these factors likely contribute some to holding down inflation.  At the same time as the pressures holding down in flation, as of this writing on 10/13/2021, there are global supply chain shocks and shortages spanning numerous industries that are putting upward pressure on prices as the world emerges from the COVID-19 pandemic.

My goal is to make sense of this mixture of influences on the long-term value of the dollar.  As Milton Friedman once said, "Inflation is always and everywhere a monetary phenomenon."  If that is the case, we can expect inflation for years to come.  However, Friedman made that statement at a time when the globe was not nearly as connected internationally as it is today and when the dollar was not as dominant globally as it is today.
