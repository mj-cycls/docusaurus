---
title: "Stock Market: Part 1"
---

# ⚡️ Stock market: part 1

### 1. Just the symbol
via `yfinance`

Initiate the client
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

Write the logic and `UI` in the `main` function. In this instance input is the user's message which you can grab with `messages[0]["content"]`. then just return a `UI.Text` element to the user by passing a string of the `input` and `price` like this:

```py
def main(messages):
    input = messages[0]["content"]
    price = stock(input)
    return UI.Text(f"Price of {input}: {price:0.2f}")
```

Run the server
```py
sarya.run()
```

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
    return UI.Text(f"Price of {input}: {price:0.2f}")

sarya.run()
```
