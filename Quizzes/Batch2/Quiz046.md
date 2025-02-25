# Quiz 46  

## UML Diagram

![quiz46](https://github.com/user-attachments/assets/c97451b7-3703-4283-a5ff-250126eaa7e6)

## Code

```
class Citizen:
    def __init__(self, name: str, city: str, status: str):
        self.name = name
        self.city = city
        self.status = status

    def get_info(self):
        return f"Name: {self.name}, City: {self.city}, Status: {self.status}"


class Employee(Citizen):
    def __init__(self, name: str, city: str, status: str, salary: float):
        super().__init__(name, city, status)
        self.salary = salary

    def get_salary(self):
        return f"Salary: ${self.salary}"


class PartTimeEmployee(Employee):

    def __init__(self, name: str, city: str, status: str, salary: float, ft_fraction: float, unionstatus: bool):
        super().__init__(name, city, status, salary)
        self.ft_fraction = ft_fraction
        self.unionstatus = unionstatus

    def check_unionstatus(self):
        return f" Union Status: {self.unionstatus}"


    def get_ftfraction(self):
        return f" Full-Time Fraction: {self.ft_fraction}"


citizen = Citizen("Alice", "Lincoln", "Employed")
print(citizen.get_info())

employee = Employee("Bob", "Lilongwe", "Employed", 55000)
print(employee.get_salary())

part_time = PartTimeEmployee("Linda", "Cape Town", "Part-time Employee", 45000, 0.8, True)
print(part_time.check_unionstatus())
print(part_time.get_ftfraction())
```

## Proof of Work

<img width="1352" alt="Screenshot 2025-02-25 at 0 57 08" src="https://github.com/user-attachments/assets/47236e3f-de20-4417-8290-f59e3ca70b33" />
