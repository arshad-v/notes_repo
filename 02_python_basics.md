
# 🐍 Python Basics & Project Setup Guide


---

## ✅ Project Setup

```bash
# Install Python, Git
# Install VS Code or any IDE


cd data-analyzer

# activate env
venv\Scripts\activate   # Windows



```

---

## 📦 Installing Required Libraries

```bash
pip install pandas
```

---

## 📌 Basic Python Concepts

### Variables & Input

```python
name = "Arshad"
age = 25
is_student = True

print("Name:", name)
print("Age:", age)
print("Is student?", is_student)

user_input = input("Enter a brand to filter: ")
```

---

### Loops

#### For loop

```python
for i in range(1, 6):
    print(i)
```

#### While loop

```python
counter = 1
while counter <= 3:
    print("Counter:", counter)
    counter += 1
```

---

### Conditionals

```python
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

---

## 📄 CSV File Handling (No Pandas)

### Write CSV

```python
import csv

data = [["Name", "Age"], ["Alice", 25], ["Bob", 30]]
with open("output.csv", "w", newline="") as f:
    writer = csv.writer(f)
    writer.writerows(data)
```

### Read CSV

```python
with open("output.csv", "r") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)
```

---

## 📊 CSV Reading with Pandas

```python
import pandas as pd

df = pd.read_csv("sample.csv")
print(df)
```

---

## 🧠 Filtering Rows with Condition

```python
for index, row in df.iterrows():
    if row["Brand"].lower() == user_input.lower():
        print(f"Match: {row['Brand']} {row['Model']}")
```

---

# 🗃️ SQLite Cheat Sheet

## 🔌 Connect to SQLite DB

```python
import sqlite3
conn = sqlite3.connect("sakila.db")
cursor = conn.cursor()
```

## 📋 List All Tables

```python
import pandas as pd
tables = pd.read_sql_query("SELECT name FROM sqlite_master WHERE type='table';", conn)
print(tables)
```

## 🔍 Read Data From Table

```python
df = pd.read_sql_query("SELECT * FROM actor LIMIT 10;", conn)
print(df)
```

## 🆕 Create Table and Insert Data

```python
cursor.execute("""
CREATE TABLE IF NOT EXISTS cars (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    brand TEXT,
    model TEXT,
    price INTEGER
)
""")
cursor.execute("INSERT INTO cars (brand, model, price) VALUES (?, ?, ?)", ("Honda", "Civic", 17000))
conn.commit()
```

## 🔎 Query with Filter

```python
df = pd.read_sql_query("SELECT * FROM cars WHERE price > 15000;", conn)
```

## ✅ Close Connection

```python
conn.close()
```

---


