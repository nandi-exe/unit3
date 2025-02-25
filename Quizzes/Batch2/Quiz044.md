# Quiz 44 

## UML Diagram

![Screenshot 2025-02-25 at 12 19 22 AM](https://github.com/user-attachments/assets/4b9f6c8e-c0cd-477f-bf4d-e130b40ca028)

## Code

```
class RainDrops:
    def pour(self, n: int) -> str:
        result = ""
        if n % 3 == 0:
            result += "Pling"
        if n % 5 == 0:
            result += "Plang"
        if n % 7 == 0:
            result += "Plong"
        return result if result else str(n)

raindrop = RainDrops()
print(raindrop.pour(28))  
print(raindrop.pour(30))
print(raindrop.pour(34))
```

## Proof of Work

<img width="1391" alt="Screenshot 2025-02-25 at 0 15 14" src="https://github.com/user-attachments/assets/5c086ab3-ad9a-43af-aaff-b80dc9f722c4" />

