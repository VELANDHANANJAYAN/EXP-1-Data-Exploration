# EXP 3: Predictive Analytics

## A. Regression Analysis: Build and Evaluate Linear Regression Models and Interpret Regression Coefficients

**Tools:** Python (Scikit-learn), R

### Python Code for Linear Regression

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
import matplotlib.pyplot as plt

# Example dataset (predicting 'y' based on 'x')
data = {
    'x': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    'y': [2, 4, 5, 4, 5, 7, 8, 9, 10, 12]
}

# Convert to DataFrame
df = pd.DataFrame(data)

# Define the predictor and target variables
X = df[['x']]  # Predictor variable (independent)
y = df['y']    # Target variable (dependent)

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Create and train the linear regression model
model = LinearRegression()
model.fit(X_train, y_train)

# Predict the target variable using the test set
y_pred = model.predict(X_test)

# Model evaluation
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

# Output regression coefficients
print(f"Intercept: {model.intercept_}")
print(f"Coefficient: {model.coef_[0]}")

# Model evaluation results
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Plotting the regression line
plt.scatter(X, y, color='blue', label='Data points')
plt.plot(X, model.predict(X), color='red', label='Regression line')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Linear Regression')
plt.legend()
plt.show()
```

## OUTPUT:

### 1. Regression Coefficients:
- **Intercept (b₀):** The value of `y` when `x` is 0. It represents the baseline value.
- **Coefficient (b₁):** The change in `y` for each unit increase in `x`.

**Example output:**
  **Intercept:** 0.6237623762376234  
  **Coefficient:** 1.0693069306930694

  
### 2. Model Evaluation:
- **Mean Squared Error (MSE):** A measure of the average squared difference between actual and predicted values. Lower values indicate a better fit.
- **R-squared (R²):** A measure of how well the independent variable(s) explain the variability in the dependent variable. An R² closer to 1 means a better model fit.

**Example output:**
  **Mean Squared Error:** 0.5315165179884329  
  **R-squared:** 0.9114139136685945

### 3. Regression Line Visualization:
The plot will show the data points and the fitted regression line.

![image](https://github.com/user-attachments/assets/ad3b5d6d-285e-4e81-ab05-7489c396ccfe)


