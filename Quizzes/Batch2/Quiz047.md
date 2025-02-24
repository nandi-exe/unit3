# Quiz 47

## Paper Solution

![image](https://github.com/user-attachments/assets/8aa4b76a-1dd2-4c53-92f1-871e25e83b18)

## UML Diagram

![Screenshot 2025-02-24 at 11 03 52 PM](https://github.com/user-attachments/assets/1c93aaa0-d926-4f80-95f6-811f3112da62)

## Code


```
class CalorieCount:
    def __init__(self, daily_limit):
        self.daily_limit = daily_limit
        self.daily_intake = 0
        self.protein = 0
        self.carbs = 0
        self.fat = 0

    def addMeal(self, cal, pro, carbs, fat):
        self.daily_intake += cal
        self.protein += pro
        self.carbs += carbs
        self.fat = fat

    def getProteinPercentage(self):
        return 4*self.protein/self.daily_intake

    def onTrack(self):
        status = True
        if self.daily_intake > self.daily_limit:
            status = False
        return status

sunday = CalorieCount(1500)

sunday.addMeal(716, 38, 38, 45)
sunday.addMeal(230, 16, 8, 16)
sunday.addMeal(568, 38, 50, 24)
print(sunday.onTrack())
print(sunday.getProteinPercentage())
```

## Proof of Work

![image](https://github.com/user-attachments/assets/5e210489-1376-4662-a4fd-15a63c0178aa)

