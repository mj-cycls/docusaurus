---
sidebar_position: 1
title: ⚡️ Getting Started
---

# ⚡️ Getting started

Sarya is a python framework for building, and publishing AI applications. It provides everything you need to transform your project into beautiful UI across multiple platforms. 

in order to get started make sure you generate `SARYA-TOKEN` from the developer portal at [portal.sarya.com](https://portal.sarya.com).

We will refer to app and marid interchangeably.

### 1. install

```sh
pip install sarya-sdk
```

or using poetry
```sh
poetry add sarya-sdk
```

### 2. Get the Sarya Client

The developer portal generates a `SARYA-TOKEN` for each app/marid. with `SaryaClient` you need to provide the name, handler, and description of the marid:

```py
from sarya import SaryaClient, UI

SaryaClient.token="SARYA-TOKEN" 
 
sarya=SaryaClient(name="hello world",handler="hello",
                    description="hello world marid")
```

### 3. Create the entry point
The main function works as the entry point of your marid, in this example we just send "Hello World!" for each user request.
```py
def main(x):
    return UI.Text("Hello World!")
```

### 4. Run the server
Sarya's marids are just regular servers. Your app/marid is published with `run()` so that Sarya calls to it with each relevant request:
```
sarya.run()
```

### 5. Hello World!
The full example:
```python
from sarya import SaryaClient, UI

SaryaClient.token="SARYA-TOKEN" 
 
sarya = SaryaClient(name="hello world",handler="hello",
                    description="hello world marid")

def main(x):
    return UI.Text("Hello World!")

sarya.run()
from sarya import SaryaClient, UI

SaryaClient.token="SARYA-TOKEN" 
 
sarya = SaryaClient(name="hello world",handler="hello",
                    description="hello world marid")

def main(x):
    return UI.Text("Hello World!")

sarya.run()
```

### 6. Another Example
Here is another marid that just replies to the user what user wrote, like a mirror
```python
from sarya import SaryaClient, UI

SaryaClient.token="SARYA-TOKEN" 
 
sarya = SaryaClient(name="hello world",handler="hello",
                    description="hello world marid")

def main(x):
    return UI.Text("Hello World!")

sarya.run()
from sarya import SaryaClient, UI

SaryaClient.token="SARYA-TOKEN" 
 
sarya = SaryaClient(name="hello world",handler="hello",
                    description="hello world marid")

def main(x):
    return UI.Text(x[0]["content"])

sarya.run()
```




