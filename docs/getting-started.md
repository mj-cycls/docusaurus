---
sidebar_position: 1
title: ⚡️ Getting Started
---

# ⚡️ Getting started

Sarya is a python framework for building, and publishing AI applications. It provides everything you need to transform your project into beautiful UI across multiple platforms. 

in order to get started make sure you generate `TOKEN` from the developer portal at [platform.sarya.com](https://platform.sarya.com).

We will refer to app and marid interchangeably.

### 1. Install

```sh
pip install sarya
```

or using poetry
```sh
poetry add sarya
```

### 2. Get the Sarya Client

The developer portal generates a `TOKEN` for each app/marid. with `Sarya` client you need to provide the name, handler, and description of the marid:

```py
from sarya import Sarya, UI

sarya = Sarya(token="TOKEN")
```

### 3. Add the Entry Point
The main function works as the entry point of your marid, in this example we just send "Hello World!" for each user request.
```py
def main():
    return UI.Text("Hello World!")
```

### 4. Run the Server
Sarya's marids are just regular servers. Your app/marid is published with `run()` so that Sarya calls to it with each relevant request:
```py
sarya.run()
```

### 5. Hello World! 👋
The full example:
```py
from sarya import Sarya, UI

sarya = Sarya(token="TOKEN")

def main():
    return UI.Text("Hello World!")

sarya.run()
```

### 6. Extra: Mirror 🪞
Here is another marid that just replies back to user what they wrote, basically a mirror:
```py
from sarya import Sarya, UI
 
sarya = Sarya(token="TOKEN")

def main(messages):
    return UI.Text(messages[0]["content"]) # incoming messages

sarya.run()
```




