# TASK-7-Get-Basic-Sales-Summary-from-a-Tiny-SQLite-Database-using-Python. 

# Sales Data Analysis with SQLite and Python

# Objective

In this project, I used Python along with SQLite, pandas, and matplotlib to perform basic sales analysis. The goal was to connect to an SQLite database, run SQL queries to get sales data (total quantity sold and revenue per product), and

display the results using print statements and a bar chart.

# Tools Used

Python (for scripting)

SQLite (built into Python, no setup required)

pandas (for data manipulation)

matplotlib (for creating visualizations)

Jupyter Notebook or Python (.py) file

# Dataset

The dataset consists of an SQLite database (sales_data.db) with a sales table containing the following columns:

product: Name of the product

quantity: Number of items sold

price: Price per item

# Task Breakdown

Create SQLite Database & Sales Table: I created an SQLite database called sales_data.db and inserted sample data into the sales table. This table contains products, their sold quantities, and their respective prices.

python

Copy

Edit

import sqlite3

# Connect to SQLite database (this creates the database if it doesn't exist)
conn = sqlite3.connect("sales_data.db")

# Create a cursor object to execute SQL commands
cursor = conn.cursor()

# Create the 'sales' table with sample columns
cursor.execute('''
CREATE TABLE IF NOT EXISTS sales (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    product TEXT,
    quantity INTEGER,
    price REAL
)
''')

# Insert some sample data into the sales table

cursor.executemany('''
INSERT INTO sales (product, quantity, price)
VALUES (?, ?, ?)
''', [
    ('Product A', 10, 20.0),
    ('Product B', 5, 40.0),
    ('Product C', 8, 15.0),
    ('Product D', 12, 25.0)
])

# Commit changes and close the connection
conn.commit()
conn.close()

