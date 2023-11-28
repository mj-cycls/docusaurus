---
title: "Stock Market: Part 1"
---

# ⚡️ Stock market: part 1

We will make a stock market app that you can chat with. Part 1, will cover how to get the data for a specific company (symbol) and return the price of the stock back to the user.

### 1. Data
for this example we will use the `yfinance` package to get the stock market data. If you don't have it already you can install it with:
```
pip install yfinance
```

Initiate the client. I had already named it `@stock-1` in the developer portal:
```py
from sarya import Sarya, UI
import yfinance as yf

sarya = Sarya(token="TOKEN")
```

Use `yfinance` package to fetch the stock symbol
```py
def price(symbol):
    data = yf.download(symbol, period='1d')
    return data.Open[0]
```

### 2. User interface
Write the logic and `UI` in the `main` function. In this instance input is the user's message which you can grab with `messages[0]["content"]`. then just return a `UI.Text` element to the user by passing a string of the `input` and `price` like this:
```py
def main(messages):
    input = messages[0]["content"]
    price = stock(input)
    return UI.Text(f"Price of {input}: {price:0.2f}")
```

Publish the app by running the server:
```py
sarya.run()
```

### 3. Just the symbol
Here is the full code:
```py
from sarya import Sarya, UI
import yfinance as yf

sarya = Sarya(token="TOKEN")

def price(symbol):
    data = yf.download(symbol, period='1d')
    return data.Open[0]

def main(messages):
    input = messages[0]["content"]
    price = stock(input)
    return UI.Text(f"price of {input}: {price:0.2f}")

sarya.run()
```

and if you run it:
```
User  | @stock-1 GOOG
Sarya | price for GOOG: 137.57

User  | @stock-1 TSLA
Sarya | price for TSLA: 236.68
```
