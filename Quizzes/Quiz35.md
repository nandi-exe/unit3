# Quiz 35

## Code
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
## Proof of Work
<img width="742" alt="image" src="https://github.com/user-attachments/assets/8d03392f-c1c0-47cd-bcaa-c9dfec409f3a" />
