# Quiz 39

## Diagram

![Screenshot 2025-01-31 at 8 26 00 AM](https://github.com/user-attachments/assets/dfbb4a47-f072-4fcd-8c74-81d441d3d70a)

## Code
```
import sqlite3

haiku = """Code flows like a stream
Algorithms guide its way
In silence, it solves"""

db_name = "haikus.db"

# Connect to file as an SQLite database
connection = sqlite3.connect(db_name)
cursor = connection.cursor()

# Create table if it doesn't exist
query_create = """CREATE TABLE IF NOT EXISTS words (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    length INTEGER,
    word TEXT
);"""
cursor.execute(query_create)

# Insert words into the database
for word in haiku.split():
    query_add = """INSERT INTO words (length, word) VALUES (?, ?);"""
    cursor.execute(query_add, (len(word), word))

# Commit after all inserts (better performance)
connection.commit()

# Query the average word length
query_avg = """SELECT AVG(length) FROM words;"""
cursor.execute(query_avg)
average_length = cursor.fetchone()[0]

print("The average word length is", average_length)



# Close the database connection
connection.close()
```
## Proof of Work
<img width="1008" alt="image" src="https://github.com/user-attachments/assets/ac522f07-1486-4e37-ba02-975efe100881" />
