# Quiz 35

## Diagram

![Screenshot 2025-01-31 at 9 45 14 AM](https://github.com/user-attachments/assets/ab8d47f7-4535-41ce-a873-2def0cb66264)

## Code
```
class Person:
    def __init__(self,name:str, age:int):
        self.name = name
        self.age = age

    def get_age(self):
        return self.age

    def get_name(self):
        return self.name

class Student(Person):
    def __init__(self, name:str, age:int, grade:int):
        super().__init__(name = name, age = age)
        self.grade = grade

    def get_grade(self):
        return self.grade

attempt = Student(name = 'Nolan', age = 14, grade = 84)
attempt2 = Person(name = 'Nolan', age = 14)
print(f'{attempt2.get_name()}\n{attempt2.get_age()}')
print(f'{attempt.get_grade()}')
```

## Proof of Work
<img width="742" alt="image" src="https://github.com/user-attachments/assets/8d03392f-c1c0-47cd-bcaa-c9dfec409f3a" />
