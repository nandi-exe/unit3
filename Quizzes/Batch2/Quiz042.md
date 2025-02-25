# Quiz 42

## ER Diagram

![Screenshot 2025-02-25 at 1 44 29 PM](https://github.com/user-attachments/assets/8ba40178-37eb-4a92-8f6a-e5d9de19446d)

## Code
```
import sqlite3
from passlib.context import CryptContext
from passlib.hash import sha256_crypt
from my_lib import DatabaseManager

hash_function = sha256_crypt.using(rounds = 30000)
pwd_config = CryptContext(
    schemes=["sha256_crypt"],
    default="sha256_crypt"
)

def check_hash(input_str, hash):
    return pwd_config.verify(input_str, hash)

def encrypt_password(in_password:str):
    return pwd_config.hash(in_password)

x = DatabaseManager("bitcoin_exchange.db")
result = x.search("SELECT * from ledger")
x.close()

for row in result:
    u_id, sender_id, receiver_id, amount, sign = row
    print(u_id, sender_id, receiver_id, amount, sign)
    text = f"id {u_id},sender_id {sender_id},receiver_id {receiver_id},amount {amount}"
    if check_hash(input_str = text,hash = sign):
        print(f"Tx(id={u_id}) Signature matches")
    else:
        print(f"Tx(id={u_id}) Error signature")
```

## Proof of Work

<img width="779" alt="Screenshot 2025-02-25 at 13 39 55" src="https://github.com/user-attachments/assets/e8003021-3b8f-4bb6-a654-4f2b5623c382" />
