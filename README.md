# Risk Assessment

```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Generate a date range
dates = pd.date_range(start="2024-03-01", end="2024-03-10")

# Simulate non-linear, random walk for stock prices
np.random.seed(42)  # For reproducibility
close_prices = [31.25]  # Starting price
for _ in range(len(dates) - 1):
    # Random change, scaled up by multiplying with a random number
    change = np.random.randn() * np.random.choice([0.5, 1, 1.5, 2])
    new_price = close_prices[-1] + change
    close_prices.append(new_price if new_price > 0 else close_prices[-1])

# Convert lists to pandas DataFrame
df = pd.DataFrame({'Date': dates, 'Close': close_prices})

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(df['Date'], df['Close'], marker='o', linestyle='-', color='blue')
plt.title('Simulated Uber Stock Prices - March 2024')
plt.xlabel('Date')
plt.ylabel('Closing Price (USD)')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
