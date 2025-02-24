# Quiz 43 

## UML Diagram

![Screenshot 2025-02-24 at 10 22 26 PM](https://github.com/user-attachments/assets/bd3870fd-fa23-4933-8c10-39b9a79c1ce5)

## Code

```
class palNum:
    def __init__(self, first, last):
        self.first = first
        self.last = last

    def get_pal_list(self):
        pal_numbers = []
        for num in range(self.first, self.last + 1):
            if str(num) == str(num)[::-1]:
                pal_numbers.append(num)

        return pal_numbers


test = palNum(1,22)
print(test.get_pal_list())
```

## Proof of Work

![image](https://github.com/user-attachments/assets/831456c9-2920-4c28-809f-b3604ec1747b)

