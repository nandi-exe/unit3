# Quiz 33

## Paper Solution
![IMG_1444](https://github.com/user-attachments/assets/4e2937f6-adbe-407b-b598-c4a35ec66eee)

## Code
class CompoundInterest:
    def __init__(self,principle:int,rate:float):

        self.principle = principle
        self.rate = rate

    def calculate(self,years:int) -> float:
        return round(self.principle*(1+self.rate)**years,2)

attempt = CompoundInterest(principle=500,rate=0.15)

print("Compound Interest")
print(f'8 Years: {attempt.calculate(8)}')
print(f'16 Years: {attempt.calculate(16)}')
## Proof of Work
<img width="1122" alt="image" src="https://github.com/user-attachments/assets/a2f6c1ee-c12f-4f9b-aa98-3316aacce2a7" />

