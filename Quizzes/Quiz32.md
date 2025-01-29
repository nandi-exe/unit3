# Quiz 32

## Code
```
email_list = []
class HResources:
    def __init__(self,name,email,nationality,occupation, department):
        self.fullname = name
        self.nationality = nationality
        self.job = occupation
        self.email = email
        self.department = department

    def get_email(self):
        fname, lname = self.fullname.split(" ")
        self.email = f'{fname}.{lname}@companya.org'
        self.email = self.email.lower()
        if self.email in email_list:
            print("This email address is already in use")
        else:
            email_list.append(self.email)
            return self.email

    def greet(self):
        print(f"Welcome to CompanyA!"
              f"\nYour information is as follows:"
              f"\nName: {self.fullname}"
              f"\nNationality: {self.nationality}"
              f"\nDepartment: {self.department}"
              f"\nEmail: {self.email}"
              f"\nOccupation: {self.job}")
        pass
## Proof of Work
<img width="1470" alt="image" src="https://github.com/user-attachments/assets/9decdacf-b5b0-4cb2-b1e8-72bd4ce8bc73" />
```
## Proof of Work
![image](https://github.com/user-attachments/assets/1e3c7d3d-678a-4ef4-a384-88f51d48b66e)
