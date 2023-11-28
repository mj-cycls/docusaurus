---
title: Stock Market
---

# ⚡️ Stock market

### 1. Just the symbol
via `yfinance`

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
