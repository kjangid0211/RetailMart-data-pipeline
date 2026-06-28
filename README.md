# RetailMart Data Pipeline
### Junior Data Engineer — Technical Assignment

---

## About the Project

This project builds an end-to-end data pipeline for RetailMart Pvt. Ltd., a retail chain operating across India. The company collects raw daily sales data from all its stores in three separate CSV files. The data is messy — it contains duplicate records, missing values, incorrect data types, and mixed date formats.

The pipeline automatically cleans, transforms, and loads this data into a SQLite database and generates business reports that answer:
- Which products are selling the most and in which city?
- What is the total revenue generated per store per day?
- Which stores or products have missing or incorrect data?

---

## Project Structure

```
RetailMart-data-pipeline/
├── pipeline.ipynb          # Main pipeline notebook — all 6 tasks
├── sales_data.csv          # Raw sales transactions (with deliberate data issues)
├── products.csv            # Product reference data
├── stores.csv              # Store reference data
├── merged.csv              # Final merged and cleaned output dataset
└── README.md
```

## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/kjangid0211/retailmart-pipeline
cd retailmart-pipeline
```

**2. Install dependencies**
```bash
pip install pandas numpy
```

**3. Run the pipeline**
```bash
python pipeline.py
```

All output files and the database will be generated automatically in the same folder.

---

## Pipeline Stages

| Stage | What Happens |
|---|---|
| **1. Ingestion** | Loads all three CSV files into pandas DataFrames and prints shape, data types, and null counts for each |
| **2. Cleaning** | Removes duplicate rows, fills missing quantity with 0, drops invalid amount rows, converts dates and types |
| **3. Transformation** | Merges all three DataFrames, adds total_revenue column, aggregates by city, category, and month |
| **4. SQL Loading** | Writes final data to SQLite database and runs 4 analysis queries |
| **5. Reporting** | Prints a summary report and exports 3 output CSV files |

---

## Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.x | Core pipeline language |
| pandas | Data loading, cleaning, merging, and aggregation |
| NumPy | Statistical calculations on revenue data |
| sqlite3 | Embedded SQL database — no server needed |
| Git & GitHub | Version control and project submission |

---

## Data Quality Issues Handled

The `sales_data.csv` file was designed with real-world data problems to test the pipeline:

- 3 rows with missing `quantity` values → filled with 0
- 2 rows with missing `amount` values → dropped
- 1 row with non-numeric `amount` (e.g. N/A) → dropped
- 3 exact duplicate rows → removed
- Mixed date formats → normalised to datetime

---

## Output Files

- **`retail_mart.db`** — SQLite database containing the `retail_sales` table
- **`merged.csv`** — Complete merged and cleaned dataset

---

## Author

**Kartik Jangid**  
Roll No. 23EJIDS032  
GitHub: [kjangid0211](https://github.com/kjangid0211)
