# Data-Analyst-Assistant-Using-a-LLM-Agent
A Python-based data analysis assistant leveraging a Large Language Model (LLM) agent to interactively analyze datasets, generate insights, and visualize results. This project combines Pandas, Seaborn, and LangChain with OpenAI's API to create an intelligent assistant capable of interpreting data and producing human-readable explanations.


## Features
  - Automated Data Analysis: Quickly generate descriptive statistics and summaries of datasets.
  - Data Visualization: Generate line graphs and other visualizations using Seaborn.
  - Outlier Detection: Identify extreme values and anomalies in your dataset.
  - Interactive Agent: Ask natural language questions about your dataset and receive analytical responses.
  - Kaggle Integration: Easily download and analyze Kaggle datasets.
    
##Tech Stack
  - Python 3.11+
  - Pandas – For data manipulation and analysis.
  - Seaborn – For visualizations.
  - LangChain & LangChain-Experimental – To create an LLM-powered agent.
  - OpenAI API – LLM backend for interpreting and analyzing data.
  - Google Colab – Optional environment for running notebooks.
  - Kaggle API – To download datasets programmatically.

## Installation
Install the required packages:
```
pip install langchain langchain_experimental langchain-openai
pip install dotenv kaggle pandas seaborn
```
## Setup
1. Google Drive (Optional): Mount your Google Drive to store datasets.

```
from google.colab import drive
drive.mount('/content/drive')
```

2. Kaggle API: Set up Kaggle credentials in your Google Drive or local environment.
```
import os
os.environ['KAGGLE_CONFIG_DIR'] = '/content/drive/MyDrive/kaggle'
```

3. OpenAI API Key: Store your API key securely.
```
from getpass import getpass
os.environ["OPENAI_API_KEY"] = getpass("OpenAI API Key: ")
```

## Usage
1. Load a dataset:

```
import pandas as pd

csv_file = '/content/drive/MyDrive/kaggle/climate_change_data.csv'
df = pd.read_csv(csv_file)
```

2. Create the LLM agent:
```
from langchain_experimental.agents.agent_toolkits import create_pandas_dataframe_agent
from langchain_openai import OpenAI

agent = create_pandas_dataframe_agent(
    OpenAI(temperature=0),
    df,
    verbose=True,
    allow_dangerous_code=True
)
```
3. Analyze data interactively:

```
agent.invoke("Analyze this data, and write a brief explanation around 100 words.")

```

4. Generate visualizations:
```
agent.run("""
Create a line graph with seaborn containing the annual average CO2 emissions
in Portugal over the years.
""")
```

5. Identify outliers:
```
agent.run("Can you identify any outliers in the dataset?")
```

## Example Output
  - A concise summary of the dataset with mean, standard deviation, and insights.
  - Line graph showing annual average CO2 emissions in a specific country.
  - Detected outliers for columns like temperature, CO2 emissions, and sea-level rise.

## Contributing
Contributions are welcome! You can:
  - Add support for more visualizations.
  - Extend the LLM agent for advanced statistical analysis.
  - Optimize agent responses for large datasets.

# License
This project is licensed under the MIT License.

## Acknowledgements
  - LangChain for enabling LLM agents.
  - OpenAI for the language model.
  - Kaggle for datasets.


