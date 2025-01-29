# 📂 Georeferenzied database

This repository includes an **SQLite database (`database.db`)**, which contains metadata related to images and their corresponding label files. The database is structured to provide quick access to image-related data.

## 🔹 Database Structure
- The database contains a key table where each row corresponds to an image and its associated label.
- The **`name`** field in the database is the unique identifier for each entry. It corresponds to:
  - The **image filename** stored in an external cloud drive.
  - The **label filename** (without the file extension) in the same drive.

## 🌍 Accessing the Image and Label Files
- Since the actual images and label files are stored externally, you can download them from the provided **cloud storage link**.
- The filenames in the database match exactly with those in the drive, making it easy to map the records.

## 🛠 How to Open the Database
You can explore the database using **DBeaver, SQLite Browser, or Python**.

### Using DBeaver
1. Open **DBeaver** and click **"Database" > "New Connection"**.
2. Select **SQLite** and provide the path to `database.db`.
3. Click **"Finish"** and run queries like:
   ```sql
   SELECT * FROM table_name;
   ```

### Using SQLite CLI
1. Install SQLite if not already installed.
2. Open a terminal and navigate to the repository folder.
3. Run:
   ```sh
   sqlite3 database.db
   ```
4. Inside the SQLite shell, use:
   ```sql
   .tables  -- List all tables
   SELECT * FROM table_name LIMIT 10;  -- View sample data
   ```

### Using Python
```python
import sqlite3
import pandas as pd

# Connect to the database
conn = sqlite3.connect("database.db")

# Read data into a DataFrame
df = pd.read_sql("SELECT * FROM table_name", conn)

# Display data
print(df.head())

# Close connection
conn.close()
```

---
