## Overview
This Python application simulates a computer-based stock trading program. Its goal is to demonstrate the basic 
functionality of neural networks trained by supervised learning and reinforcement learning (deep Q-learning).

The application consists of a stock exchange and serveral connected traders. The stock exchange asks each trader once 
per day for its orders, and executes any received ones. Each trader computes its orders using stock market information 
provided by the stock exchange. A trader consists of two components: A neural network for predicting future stock 
prices, and a neural network for computing orders based on these predictions. Thereby, the first neural network can be 
trained using supervised learning, and the latter neural network can be trained using reinforcement learning (deep 
Q-learning).
### Predictor
A predictor (implemented by separate predictor classes like 'PerfectPredictor') works behind a trader and provides - 
if applicable - a price estimation for a specific stock. Among other ways, providing a price estimate can be 
accomplished by using a neural network that has been trained on a set of past stock prices. To receive an estimated 
stock price the trader calls its specific predictor with the latest stock prices and the predictor in turn replies with 
the estimated future stock price.   

## Required Tools
Trader AI's codebase relies on Python 3. To run Trader AI the following tools are required:
* Python 3
* pip (may come with your Python installation)
* virtualenv (optional)

## Run the Application
After installing all required tools (Python, *pip*, *\[virtualenv]*) execute the following commands:

### Clone the Repository
```
$ git clone https://github.com/senacor/Trader.AI.git
$ cd Trader.AI
```

### Create a Virtual Environment (optional)
If you want to use *virtualenv*, create a virtual environment. The directory *virtual_env* is already added to 
*.gitignore*.

#### On Mac
```
$ virtualenv -p python3 virtual_env
$ source virtual_env/bin/activate
```

#### On Windows
```
$ virtualenv -p [path\to\python3\installation\dir\]python virtual_env
$ virtual_env/Scripts/activate
```

### Install All Dependencies
This installs all required dependencies by Trader.AI.
```
$ pip install -r requirements.txt
```

### Run
```
$ python stock_exchange.py
```
After some Terminal action this should show a diagram depicting the course of different portfolios which use different
Trader implementations respectively.

Furthermore you can execute the test suite to see if all works well:
```
$ python test_suite_all.py
```

### Overview Of This Repository
This repository contains a number of packages and files. Following a short overview:
* datasets - CSV dumps of stock prices
* evaluating - Python package which contains all evaluating/ILSE logic
* model - Python package which contains all shared model classes
* predicting - Python package which contains all predicting logic
* trading - Python package which contains all trading logic
* `.travis.yml` - Configuration for Travis CI. See [https://travis-ci.org/senacor/Trader.AI/]()
* `definitions.py` - Contains some project-wide Python constants
* `dependency_injection_containers.py` - Contains all configured dependencies for dependency injection
* `logger.py` - Contains project-wide logger configuration
* `README.md` - This file
* `requirements.txt` - Contains an export of all project dependencies (by running `$ pip freeze > requirements.txt`)
* `stock_exchange.py` - Contains the central main method. This starts ILSE
* `utils.py` - Contains utility methods that are needed project-wide

This project is extended version of [Trader.AI project](https://github.com/senacor/Trader.AI)
