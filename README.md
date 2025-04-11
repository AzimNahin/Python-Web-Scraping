
# 🕸️ Web Scraping: Largest Public Companies in the U.S.

This project demonstrates how to perform **web scraping** using Python to extract structured tabular data from a Wikipedia page. It uses `requests` and `BeautifulSoup` to parse HTML and `pandas` to clean and analyze the data.

---

## 📌 Objective

To extract, clean, and save data from the [Wikipedia page on largest U.S. public companies by revenue](https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue), and store it in a CSV file for further use.

---

## 📂 Files Included

- `Web_Scraping.ipynb` – The Jupyter Notebook with code to:
  - Fetch the HTML content of a webpage
  - Parse and extract data from an HTML table
  - Create a structured DataFrame
  - Save the data as a CSV file

- `Public_Company_List.csv` – Output file containing the scraped and processed data.

---

## 🛠️ Requirements

Make sure you have the following libraries installed:

```bash
pip install beautifulsoup4 requests pandas
```

---

## 📑 Steps Covered in the Notebook

---

### **1. Import Libraries**

```python
from bs4 import BeautifulSoup
import requests
import pandas as pd
```

---

### **2. Fetch the Page**

```python
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')
```

---

### **3. Extract Table**

```python
tables = soup.find_all('table')  # Typically returns multiple tables

# Let's assume we want the first relevant table
target_table = tables[0]  # You might need to adjust index based on inspection

# Extract headers
headers = [header.get_text(strip=True) for header in target_table.find_all('th')]
```

---

### **4. Create DataFrame**

```python
df = pd.DataFrame(columns=headers)

# Extract rows
for row in target_table.find_all('tr')[1:]:
    cells = row.find_all(['td', 'th'])  # 'th' for some name cells
    row_data = [cell.get_text(strip=True) for cell in cells]
    if len(row_data) == len(headers):  # Ensure row has correct number of columns
        df.loc[len(df)] = row_data
```

---

### **5. Export to CSV**

```python
df.to_csv('Public_Company_List.csv', index=False)
print("Data saved to Public_Company_List.csv")
```

---

## 📊 Output

A well-formatted CSV file containing the following sample columns (depending on the Wikipedia table structure):
- Company
- Industry
- Revenue
- Employees
- Headquarters
- Year

---

## 📌 Notes

- Wikipedia pages may change in structure; it's good practice to validate selectors (`<table>`, `<th>`, `<td>`) regularly.
- Consider using `try-except` blocks for robustness if running on a schedule.

---

## 🚀 Future Work

- Automate data extraction from other Wikipedia finance/tech pages
- Use `matplotlib` or `seaborn` for data visualization
- Add functionality to scrape multiple years or compare across sectors
