# Quiz 34

## Diagrams

![Screenshot 2025-01-31 at 9 40 08 AM](https://github.com/user-attachments/assets/b1db4b18-becd-4dfa-aece-624873bdfee5)

## Code
```
class Flight:
    def __init__(self, flight_number, origin, destination, departure_time, arrival_time):
        self.flight_number = flight_number
        self.origin = origin
        self.destination = destination
        self.departure_time = departure_time
        self.arrival_time = arrival_time
        self.passenger_list = []

    def add_passenger(self, passenger_name):
        if passenger_name not in self.passenger_list:
            self.passenger_list.append(passenger_name)
            return f"{passenger_name} has been added to the flight."
        else:
            return f"{passenger_name} is already on the flight."

    def remove_passenger(self, passenger_name):
        if passenger_name in self.passenger_list:
            self.passenger_list.remove(passenger_name)
            return f"{passenger_name} has been removed from the flight."
        else:
            return f"{passenger_name} is not on the flight."

    def show_flight(self):
        details = (
            f"Flight Number: {self.flight_number}\n"
            f"Origin: {self.origin}\n"
            f"Destination: {self.destination}\n"
            f"Departure Time: {self.departure_time}\n"
            f"Arrival Time: {self.arrival_time}\n"
            f"Passengers: {', '.join(self.passenger_list) if self.passenger_list else 'No passengers yet.'}"
        )
        return details

flight = Flight("EAW520", "Johannesburg", "Seoul", "10:00 AM", "4:00 PM")
print(flight.show_flight())
print(flight.add_passenger("Esther Mawero"))
print(flight.add_passenger("Lungile Phiri"))
print(flight.add_passenger("Emily Banda"))
print(flight.show_flight())
print(flight.remove_passenger("Lungile Phiri"))
print(flight.show_flight())
```

## Proof of Work

<img width="1470" alt="image" src="https://github.com/user-attachments/assets/c3411074-244b-4d6a-ae20-e7a8f7b1dd84" />
