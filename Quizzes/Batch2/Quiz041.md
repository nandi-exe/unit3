# Quiz 41  

## ER Diagram

![Screenshot 2025-02-25 at 11 13 52 AM](https://github.com/user-attachments/assets/a4ce5295-5ac5-44ac-bd9b-3253048b8250)

## Code
```
import sqlite3

from kivymd.app import MDApp
from secure_password import encrypt_password

class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query, params=None):  # Allow query parameters
        if params:
            self.cursor.execute(query, params)
        else:
            self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()



class quiz040(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.components = {"basic":0}

    def build(self):
        return

    def save(self):
        pass

    def update(self):
        #This function updates all the labels in the form using the base salary and the percentage
        # Pseudocode
        # 1- get the base salary from the GUI
        base_salary = int(self.root.ids.base.text)
        # 2- if base salary define total=int(base) and an empty string to store build a hash (for_hash="") if no base then end the function
        if base_salary:
            total = int(base_salary)
        else:
            return
        # 3- for Each TextField with ids: "inhabitant","income_tax","pension","health" get the text property
        ids = ["inhabitant", "income_tax", "pension", "health"]
        for id in ids:
            value = self.root.ids[id].text.strip()
            # 4- if the TextField.text has a number (value), calculate the equation new_value="(base*int(value)//100) JPY" and subbctract the equation to the total
            if value.isdigit():
                amount = (base_salary * int(value)) // 100
                total -= amount
                # 5- if no: then new_value = " JPY"
                self.root.ids[id + "_label"].text = f"{amount} JPY"
            else:
                self.root.ids[id + "_label"].text = " JPY"

        self.root.ids.salary_label.text = f"Net Salary: {total} JPY"

        # Constructing the string for hashing
        for_hash = f"base{base_salary}," + ",".join(
            [f"{id_}{self.root.ids[id_].text}" for id_ in ids if id_ in self.root.ids]
        ) + f",total{total}"

        print("Hash input string:", for_hash)  # Debugging step

        # Encrypting the hash string
        hashed_value = encrypt_password(for_hash)

        #calculate total

        # update the percentage
        self.root.ids.hash.text = hashed_value[-50:]

    def save(self):
        try:
            base_salary = int(self.root.ids.base.text)
            ids = ["inhabitant", "income_tax", "pension", "health"]

            # Calculate deduction amounts instead of storing percentages
            deductions = {
                id_: (base_salary * int(self.root.ids[id_].text)) // 100
                if self.root.ids[id_].text.isdigit() else 0
                for id_ in ids
            }

            total = base_salary - sum(deductions.values())

            # Construct the string for hashing using calculated deduction values
            for_hash = f"base{base_salary}," + ",".join(
                [f"{id_}{deductions[id_]}" for id_ in ids]
            ) + f",total{total}"

            hashed_value = encrypt_password(for_hash)

            query = """INSERT INTO payments (base, inhabitant, income_tax, pension, health, total, hash)
                       VALUES (?, ?, ?, ?, ?, ?, ?)"""

            # Initialize database connection
            db = database_worker("payments.db")

            # Run the query with actual deduction values
            db.run_save(query, (
                base_salary,
                deductions["inhabitant"],  # Save the actual deducted amounts
                deductions["income_tax"],
                deductions["pension"],
                deductions["health"],
                total,
                hashed_value
            ))

            # Close the database connection
            db.close()

            # Update UI with confirmation
            self.root.ids.hash.text = "Payment saved"

        except ValueError:
            self.root.ids.salary_label.text = "Invalid Input"

    def clear(self):
        for label in ["base", "inhabitant","income_tax","pension","health"]:
            self.root.ids[label].text = ""
            self.root.ids[label+"_label"].text = " JPY"

        self.root.ids["salary_label"].text = " JPY"
        self.root.ids.hash.text = "----"


test = quiz040()
create = """CREATE TABLE if not exists payments(
         base INTEGER,
         inhabitant INTEGER,
         income_tax INTEGER,
         pension INTEGER,
         health INTEGER,
         total INTEGER,
         hash TEXT

     )"""
db = database_worker("payments.db")
db.run_save(create)
db.close()

test.run()
```

## Proof of Work

<img width="1470" alt="Screenshot 2025-02-25 at 11 16 44" src="https://github.com/user-attachments/assets/edc8d1f6-22c9-4ded-8d88-c8e45fc0f054" />

<img width="739" alt="Screenshot 2025-02-25 at 11 17 01" src="https://github.com/user-attachments/assets/512bff1e-7cd1-45d7-a9a7-22666658ae7a" />
