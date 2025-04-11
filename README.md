
# 🕸️ Web Scraping Project: Public Company Data Extraction

This project is a demonstration of how to use **Python** to scrape structured data from a live webpage using `requests`, `BeautifulSoup`, and `pandas`. The goal is to collect tabular data of the largest public companies in the United States by revenue from Wikipedia and save the data into a structured CSV file.

---

## 📘 Project Description

# Import Libraries

# Fetch the Page


# Fetch the Tables

# Fetch Table Headers

# Create Dataframe

# Insert Data into Dataframe

# Convert to CSV

---

## 💻 Extracted Code

```python
from bs4 import BeautifulSoup
import requests
import pandas as pd
```

```python
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'
response = requests.get(url)

soup = BeautifulSoup(response.text,'html')
print(soup)
```

```python
table = soup.find_all('table')
table1, table2, table3 = table
```

```python
table_headers = table1.find_all('th')

table_headers = [header.text.strip() for header in table_headers]

print(table_headers)
```

```python
df = pd.DataFrame(columns=table_headers)
print(df)
print(len(df))
```

```python
rows = table1.find_all('tr')[1:]

for row in rows:
    columns = row.find_all('td')
    columns = [column.text.strip() for column in columns]
    location = len(df)
    df.loc[location] = columns

print(df)
```

```python
path = 'D:\Python\Public_Company_List.csv'
df.to_csv(path, index = False)
```

---

## 📁 Output

The notebook creates an output file:

- `Public_Company_List.csv` – A CSV containing structured data of companies scraped from Wikipedia.

---

## 🧰 Dependencies

Install the required Python libraries before running the notebook:

```bash
pip install beautifulsoup4 requests pandas
```

---

## 📌 Usage

1. Open the `Web_Scraping.ipynb` notebook.
2. Run each cell step-by-step to:
   - Fetch the HTML content of the Wikipedia page.
   - Extract the relevant table.
   - Convert it into a clean pandas DataFrame.
   - Export the data to a CSV file.
3. Use the resulting CSV file for analysis or visualization.

---

## 📝 Notes

- Ensure that the structure of the Wikipedia page hasn't changed, or table parsing may need to be adjusted.
- This notebook is ideal for beginners learning data scraping and transformation.

---

## 🚀 Future Improvements

- Add support for scraping multiple years or tables.
- Automate table selection using table titles or structure.
- Enhance data cleaning and type conversion.
