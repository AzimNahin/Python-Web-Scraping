
# 🕸️ Web Scraping Financial Data of U.S. Public Companies

This project scrapes financial and organizational data of the top public companies in the U.S. based on revenue, directly from Wikipedia. It processes the first table listed on the Wikipedia page for Fortune 500 companies and stores the clean data into a structured CSV format for further analysis.

---

## 📁 Project Structure

```
.
├── Web_Scraping.ipynb          # Jupyter Notebook containing scraping and data cleaning logic
├── Public_Company_List.csv     # Final output CSV file with company data
└── README.md                   # Project documentation (this file)
```

---

## 📌 What This Project Does

✅ Automates retrieval of Fortune 500 company data from Wikipedia  
✅ Extracts structured data from the **first HTML table** on the page  
✅ Dynamically reads and stores table headers  
✅ Cleans the extracted table rows and standardizes them  
✅ Converts the data into a well-formatted `pandas.DataFrame`  
✅ Saves the final dataset as `Public_Company_List.csv` in local storage

---

## 🔍 Extracted Fields

The CSV file contains the following columns, as dynamically extracted from the table headers:

- Rank
- Name
- Industry
- Revenue
- Profit
- Employees
- Headquarters
- and possibly other metadata depending on Wikipedia's table structure

The structure of the table may vary over time, but this notebook adapts by programmatically parsing the headers.

---

## 🧪 Technologies Used

- **Python 3**
- **Jupyter Notebook** — for step-by-step documentation and reproducibility
- **pandas** — for handling tabular data
- **requests** — for fetching webpage content
- **BeautifulSoup4** — for HTML parsing and table extraction

---

## 🚀 How to Run

### 1. Install Dependencies

You can install the necessary Python libraries using pip:

```bash
pip install pandas requests beautifulsoup4
```

### 2. Open the Notebook

Open `Web_Scraping.ipynb` in [Jupyter Notebook](https://jupyter.org/) or Jupyter Lab.

### 3. Run the Cells

Run all cells sequentially. This will:
- Fetch the Wikipedia page
- Parse the HTML table
- Create a clean dataset
- Save the output as `Public_Company_List.csv`

The final dataset will be saved to your working directory.

---

## 📂 Output Description

**`Public_Company_List.csv`**  
A structured CSV file containing financial and organizational details of the top U.S. companies, including:

| Rank | Name | Industry | Revenue | Profit | Employees | Headquarters |
|------|------|----------|---------|--------|-----------|---------------|
| 1    | Walmart | Retail | $600B   | $13.7B | 2,300,000 | Arkansas      |
| ...  | ...      | ...      | ...     | ...    | ...         | ...           |

---

## 👨‍💻 Contributor
- [Azim Nahin](https://github.com/AzimNahin)
