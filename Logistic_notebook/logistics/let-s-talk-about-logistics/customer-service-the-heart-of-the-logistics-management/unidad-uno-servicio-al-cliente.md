

# Focus on Customer Service:

#### What is customer service in the context of logistics?

In the field of logistics, customer service focuses on ensuring that customers receive their products effectively and efficiently. This includes ensuring accurate delivery times, communicating any potential delays, and providing quick solutions to any issues that may arise during the shipping process. The goal is to optimize every customer touchpoint to achieve a satisfactory experience that encourages loyalty and repeat purchases.

#### How Python can help measure and improve customer service

Python is a powerful tool for analyzing data and optimizing processes in customer service. Here are some ways it can be useful:

1. **Data Analysis:** Use libraries like Pandas and NumPy to analyze large volumes of customer data, identify patterns, and predict trends.

By implementing these solutions, companies can offer more agile, reliable, and personalized service, thus achieving better customer relationships.

{% hint style="info" %}
Definition of Customer Service Customer service refers to the set of activities, processes, and strategies that a company or business implements to meet the needs and expectations of its customers. It involves providing assistance, support, and a positive experience to customers before, during, and after a sale or interaction.
{% endhint %}

## SC Objectives

{% tabs %}
{% tab title="1" %}
Understand and effectively address customer needs
{% endtab %}

{% tab title="2" %}
Resolve problems, complaints, and inquiries in a timely and efficient manner
{% endtab %}

{% tab title="3" %}
Build long-lasting, trusting customer relationships
{% endtab %}

{% tab title="4" %}
Exceed customer expectations and build brand loyalty
{% endtab %}

{% tab title="5" %}
Differentiate yourself from the competition through exceptional service
{% endtab %}
{% endtabs %}

### How is customer satisfaction measured in a company?[#](broken-reference)

Methods for measuring customer satisfaction:

1. **Satisfaction surveys:** These are direct tools that allow companies to obtain feedback on the customer experience. They can include questions about product quality, customer service, and the likelihood of recommending the company to others.
2. **Social media comment analysis:** Evaluating customer reviews and comments on social platforms can provide a clear view of their satisfaction. This method helps identify trends and areas for improvement.
3. **Complaints and claims index:** Tracking the number and nature of complaints can help companies measure customer satisfaction. An increase in complaints may indicate service or product issues.
4. **Focus groups:** Gathering a group of customers to discuss their experiences and opinions about a product or service can offer valuable insight into their satisfaction and expectations.
5. **Customer retention and loyalty rate:** Measuring how many customers return for repeat purchases can be a direct indicator of their satisfaction. A high level of retention suggests that customers are happy with the company's offerings.

[ive consultores](https://iveconsultores.com/satisfaccion-del-cliente/)

### Mathematical Tools to Measure Customer Satisfaction

To analyze and measure each item in a customer satisfaction survey, companies can use mathematical techniques that provide valuable insights into the customer experience. One of the most commonly used techniques is multiple linear regression, which helps understand the relationship between variables and measure their impact on satisfaction.

#### Satisfaction Survey

Satisfaction surveys are a fundamental tool for collecting direct data from customers. These surveys can include questions about various aspects of the service or product, allowing companies to capture customers' attitudes and perceptions about their overall experience.

#### How to Formulate and Evaluate a Customer Satisfaction Survey

To formulate an effective customer satisfaction survey,

Define Clear Objectives: Establish which aspects of customer satisfaction you want to measure (e.g., service quality, customer service, etc.).

Evaluating a survey involves reviewing the quality of the questions and the representativeness of the responses, ensuring that the conclusions obtained are accurate and useful for decision-making.

#### Statistical Tools for Validating Survey Questions

When creating surveys, it is essential to ensure that the questions are valid and reliable. Here are some statistical tools that can be used for this validation:

**Reliability Analysis (Cronbach's Alpha):** Measures the internal consistency of the survey questions, ensuring that all questions intended to measure the same construct are correlated.

Using these tools ensures that a survey collects meaningful and representative data, consequently improving the effectiveness of customer satisfaction analysis.

To explain **Cronbach's alpha** mathematically, let's consider a set of questions designed to measure a single construct. This metric assesses internal consistency and is calculated with the following formula:

\
$$[ \alpha = \frac{N \cdot \bar{c}}{\bar{v} + (N - 1) \cdot \bar{c}} ]$$

Where:

* $$N$$ is the number of items (questions) in the scale.
* $$\bar{c}$$ is the mean of the covariances between the items.
* $$\bar{v}$$ is the mean of the variances of the individual items.

The alpha value ranges from 0 to 1, with a higher value indicating greater internal consistency.

### Multiple Linear Regression

Multiple linear regression is a statistical analysis technique used to model the relationship between a dependent variable (e.g., customer satisfaction) and multiple independent variables (e.g., service quality, scheduling convenience, etc.). Details of using regression include:

1. **Variable Selection:** First, all variables that may affect customer satisfaction are identified.
2. **Modeling:** A model is built that quantifies the relationship between the variables.
3. **Interpretation of Results:** The model coefficients allow for the interpretation of the individual impact of each independent variable on customer satisfaction.
4. **Prediction:** Based on the constructed model, the company can make accurate predictions and make informed decisions to improve its offering.

The combination of well-designed surveys and multiple linear regression analysis provides a solid foundation for understanding and improving customer satisfaction in any company.

The formula for multiple linear regression is:

$$
[ Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_nX_n + \varepsilon ]
$$

Where:

* $$Y$$ is the dependent variable.
* $$( \beta_0 )$$ is the intercept of the model.
* $$( \beta_1, \beta_2, \ldots, \beta_n )$$ are the regression coefficients.
* $$( X_1, X_2, \ldots, X_n )$$ are the independent variables.
* $$( \varepsilon )$$ is the error term.

### Let's look at an example.

```python
import pandas as pd
```

{% code overflow="wrap" %}
```python
Bd = pd.read_csv('/Users/CRC/Bd.csv') #puedes usar tu propia base de datos de encuensta de clientes; fuente --> Kaggle.com
```
{% endcode %}

```python
Bd.info()
```

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25976 entries, 0 to 25975
Data columns (total 25 columns):
 #   Column                             Non-Null Count  Dtype  
---  ------                             --------------  -----  
 0   Unnamed: 0                         25976 non-null  int64  
 1   id                                 25976 non-null  int64  
 2   Gender                             25976 non-null  object 
 3   Customer Type                      25976 non-null  object 
 4   Age                                25976 non-null  int64  
 5   Type of Travel                     25976 non-null  object 
 6   Class                              25976 non-null  object 
 7   Flight Distance                    25976 non-null  int64  
 8   Inflight wifi service              25976 non-null  int64  
 9   Departure/Arrival time convenient  25976 non-null  int64  
 10  Ease of Online booking             25976 non-null  int64  
 11  Gate location                      25976 non-null  int64  
 12  Food and drink                     25976 non-null  int64  
 13  Online boarding                    25976 non-null  int64  
 14  Seat comfort                       25976 non-null  int64  
 15  Inflight entertainment             25976 non-null  int64  
 16  On-board service                   25976 non-null  int64  
 17  Leg room service                   25976 non-null  int64  
 18  Baggage handling                   25976 non-null  int64  
 19  Checkin service                    25976 non-null  int64  
 20  Inflight service                   25976 non-null  int64  
 21  Cleanliness                        25976 non-null  int64  
 22  Departure Delay in Minutes         25976 non-null  int64  
 23  Arrival Delay in Minutes           25893 non-null  float64
 24  satisfaction                       25976 non-null  object 
dtypes: float64(1), int64(19), object(5)
memory usage: 5.0+ MB
```

```python
Bd.describe()
```

|       | Unnamed: 0   | id            | Age          | Flight Distance | Inflight wifi service | Departure/Arrival time convenient | Ease of Online booking | Gate location | Food and drink | Online boarding | Seat comfort | Inflight entertainment | On-board service | Leg room service | Baggage handling | Checkin service | Inflight service | Cleanliness  | Departure Delay in Minutes | Arrival Delay in Minutes |
| ----- | ------------ | ------------- | ------------ | --------------- | --------------------- | --------------------------------- | ---------------------- | ------------- | -------------- | --------------- | ------------ | ---------------------- | ---------------- | ---------------- | ---------------- | --------------- | ---------------- | ------------ | -------------------------- | ------------------------ |
| count | 25976.000000 | 25976.000000  | 25976.000000 | 25976.000000    | 25976.000000          | 25976.000000                      | 25976.000000           | 25976.000000  | 25976.000000   | 25976.000000    | 25976.000000 | 25976.000000           | 25976.000000     | 25976.000000     | 25976.000000     | 25976.000000    | 25976.000000     | 25976.000000 | 25976.00000                | 25893.000000             |
| mean  | 12987.500000 | 65005.657992  | 39.620958    | 1193.788459     | 2.724746              | 3.046812                          | 2.756775               | 2.977094      | 3.215353       | 3.261665        | 3.449222     | 3.357753               | 3.385664         | 3.350169         | 3.633238         | 3.314175        | 3.649253         | 3.286226     | 14.30609                   | 14.740857                |
| std   | 7498.769632  | 37611.526647  | 15.135685    | 998.683999      | 1.335384              | 1.533371                          | 1.412951               | 1.282133      | 1.331506       | 1.355536        | 1.320090     | 1.338299               | 1.282088         | 1.318862         | 1.176525         | 1.269332        | 1.180681         | 1.319330     | 37.42316                   | 37.517539                |
| min   | 0.000000     | 17.000000     | 7.000000     | 31.000000       | 0.000000              | 0.000000                          | 0.000000               | 1.000000      | 0.000000       | 0.000000        | 1.000000     | 0.000000               | 0.000000         | 0.000000         | 1.000000         | 1.000000        | 0.000000         | 0.000000     | 0.00000                    | 0.000000                 |
| 25%   | 6493.750000  | 32170.500000  | 27.000000    | 414.000000      | 2.000000              | 2.000000                          | 2.000000               | 2.000000      | 2.000000       | 2.000000        | 2.000000     | 2.000000               | 2.000000         | 2.000000         | 3.000000         | 3.000000        | 3.000000         | 2.000000     | 0.00000                    | 0.000000                 |
| 50%   | 12987.500000 | 65319.500000  | 40.000000    | 849.000000      | 3.000000              | 3.000000                          | 3.000000               | 3.000000      | 3.000000       | 4.000000        | 4.000000     | 4.000000               | 4.000000         | 4.000000         | 4.000000         | 3.000000        | 4.000000         | 3.000000     | 0.00000                    | 0.000000                 |
| 75%   | 19481.250000 | 97584.250000  | 51.000000    | 1744.000000     | 4.000000              | 4.000000                          | 4.000000               | 4.000000      | 4.000000       | 4.000000        | 5.000000     | 4.000000               | 4.000000         | 4.000000         | 5.000000         | 4.000000        | 5.000000         | 4.000000     | 12.00000                   | 13.000000                |
| max   | 25975.000000 | 129877.000000 | 85.000000    | 4983.000000     | 5.000000              | 5.000000                          | 5.000000               | 5.000000      | 5.000000       | 5.000000        | 5.000000     | 5.000000               | 5.000000         | 5.000000         | 5.000000         | 5.000000        | 5.000000         | 5.000000     | 1128.00000                 | 1115.000000              |

```python
print(Bd.iloc[:, 24])
```

```python
0                      satisfied
1                      satisfied
2        neutral or dissatisfied
3                      satisfied
4                      satisfied
                  ...           
25971    neutral or dissatisfied
25972                  satisfied
25973    neutral or dissatisfied
25974                  satisfied
25975    neutral or dissatisfied
Name: satisfaction, Length: 25976, dtype: object
```

```python
Bd['satisfaction_number'] = Bd.iloc[:, 24].replace({'satisfied': 1, 'neutral or dissatisfied': 0}).astype('int64')
Bd.info()
```

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25976 entries, 0 to 25975
Data columns (total 26 columns):
 #   Column                             Non-Null Count  Dtype  
---  ------                             --------------  -----  
 0   Unnamed: 0                         25976 non-null  int64  
 1   id                                 25976 non-null  int64  
 2   Gender                             25976 non-null  object 
 3   Customer Type                      25976 non-null  object 
 4   Age                                25976 non-null  int64  
 5   Type of Travel                     25976 non-null  object 
 6   Class                              25976 non-null  object 
 7   Flight Distance                    25976 non-null  int64  
 8   Inflight wifi service              25976 non-null  int64  
 9   Departure/Arrival time convenient  25976 non-null  int64  
 10  Ease of Online booking             25976 non-null  int64  
 11  Gate location                      25976 non-null  int64  
 12  Food and drink                     25976 non-null  int64  
 13  Online boarding                    25976 non-null  int64  
 14  Seat comfort                       25976 non-null  int64  
 15  Inflight entertainment             25976 non-null  int64  
 16  On-board service                   25976 non-null  int64  
 17  Leg room service                   25976 non-null  int64  
 18  Baggage handling                   25976 non-null  int64  
 19  Checkin service                    25976 non-null  int64  
 20  Inflight service                   25976 non-null  int64  
 21  Cleanliness                        25976 non-null  int64  
 22  Departure Delay in Minutes         25976 non-null  int64  
 23  Arrival Delay in Minutes           25893 non-null  float64
 24  satisfaction                       25976 non-null  object 
 25  satisfaction_number                25976 non-null  int64  
dtypes: float64(1), int64(20), object(5)
memory usage: 5.2+ MB
```

```python
new_Bd = Bd.select_dtypes(include=['int64'])
new_Bd.info()
```

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25976 entries, 0 to 25975
Data columns (total 20 columns):
 #   Column                             Non-Null Count  Dtype
---  ------                             --------------  -----
 0   Unnamed: 0                         25976 non-null  int64
 1   id                                 25976 non-null  int64
 2   Age                                25976 non-null  int64
 3   Flight Distance                    25976 non-null  int64
 4   Inflight wifi service              25976 non-null  int64
 5   Departure/Arrival time convenient  25976 non-null  int64
 6   Ease of Online booking             25976 non-null  int64
 7   Gate location                      25976 non-null  int64
 8   Food and drink                     25976 non-null  int64
 9   Online boarding                    25976 non-null  int64
 10  Seat comfort                       25976 non-null  int64
 11  Inflight entertainment             25976 non-null  int64
 12  On-board service                   25976 non-null  int64
 13  Leg room service                   25976 non-null  int64
 14  Baggage handling                   25976 non-null  int64
 15  Checkin service                    25976 non-null  int64
 16  Inflight service                   25976 non-null  int64
 17  Cleanliness                        25976 non-null  int64
 18  Departure Delay in Minutes         25976 non-null  int64
 19  satisfaction_number                25976 non-null  int64
dtypes: int64(20)
memory usage: 4.0 MB
```

```python
from sklearn.linear_model import LogisticRegression

X = new_Bd.drop('satisfaction_number', axis=1)  # Features
y = new_Bd['satisfaction_number']  # Target
```

```python
model = LogisticRegression(max_iter=1000)
model.fit(X, y)
```

```
LogisticRegression(max_iter=1000)
```

```python
coefficients = model.coef_
print(coefficients)
```

```python
[[-5.18027052e-05 -1.16258989e-05 -2.80761473e-02  3.95433258e-04
   7.36834576e-02 -7.33795504e-02  2.20575820e-02 -5.02928419e-02
   3.44141436e-02  1.39971393e-01  7.60752048e-02  1.00156931e-01
   6.77428471e-02  6.52574668e-02  3.40855476e-02  4.14320968e-02
   3.04496795e-02  6.91197925e-02 -6.33084903e-03]]
```

```python
intercept = model.intercept_
print(intercept)
```

```python
[-0.01461123]
```

```python
predictions = model.predict(X)
print(predictions)
```

<pre class="language-python"><code class="lang-python"><strong>[1 1 1 ... 0 1 0]
</strong></code></pre>
