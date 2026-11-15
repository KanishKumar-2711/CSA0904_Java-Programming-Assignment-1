TASK 11 – SYSTEM IMPLEMENTATION AND TESTING

1. Introduction

The Campus Smart-Parking System is designed to manage vehicle entry, parking slot allocation, parking fee calculation and vehicle exit.

The system uses Java Object-Oriented Programming concepts such as classes, objects, inheritance, polymorphism, abstraction and encapsulation.

2. System Implementation

The main classes used in the system are:

- Vehicle – Stores common vehicle information.
- TwoWheeler – Represents two-wheeler vehicles.
- Car – Represents cars.
- ElectricCar – Represents electric vehicles with charging facilities.
- ParkingSlot – Stores parking slot information.
- ParkingTicket – Stores vehicle entry and exit details.
- ParkingFacility – Manages parking slot allocation and release.
- Chargeable – Defines charging functionality.

The system follows these basic operations:

1. Accept vehicle registration details.
2. Identify the vehicle category.
3. Find an available parking slot.
4. Allocate the slot to the vehicle.
5. Generate a parking ticket.
6. Calculate the parking fee during vehicle exit.
7. Release the parking slot.

3. Testing

Testing is performed to verify that the system works correctly under different conditions.

A. Normal Test Cases

Test Case| Input| Expected Result
Vehicle entry| Valid two-wheeler| Vehicle allocated successfully
Car entry| Valid car| Available slot assigned
Vehicle exit| Valid parking ticket| Fee calculated and slot released
Electric car entry| Valid electric car| Vehicle allocated successfully

B. Boundary Test Cases

Test Case| Input| Expected Result
Last available slot| Vehicle enters when one slot remains| Last slot allocated successfully
Parking full| Vehicle enters when all slots are occupied| Allocation rejected
Zero parking duration| 0 minutes| Parking fee is zero
Exact one-hour duration| 60 minutes| One-hour fee calculated
More than one hour| 61 minutes| Two-hour fee calculated

C. Invalid Test Cases

Test Case| Input| Expected Result
Invalid vehicle type| Unknown category| Error message displayed
Duplicate registration| Same vehicle enters twice| Duplicate entry rejected
Invalid slot| Negative or out-of-range slot| Release rejected
Invalid duration| Negative minutes| Invalid duration rejected

4. Daily Revenue Calculation

The daily revenue is calculated by adding the parking fees collected from all vehicles that exit during the day.

Example:

Vehicle| Parking Fee
TwoWheeler| Rs. 30
Car| Rs. 90
ElectricCar| Rs. 210
Total Revenue| Rs. 330

Total Revenue = 30 + 90 + 210 = Rs. 330.

The calculated total should be compared with the total produced by the program.

5. Evaluation of Object-Oriented Concepts

Encapsulation: Protects vehicle and ticket information using private fields and methods.

Inheritance: Allows different vehicle categories to reuse common Vehicle properties.

Polymorphism: Allows different vehicle types to calculate their parking fees using a common reference.

Abstraction: Defines common vehicle behaviour through abstract classes and interfaces.

Classes and Objects: Represent real-world entities such as vehicles, parking slots and tickets.

These concepts improve code reusability, flexibility and maintainability.

6. Alternative Approach – Data Structures

Different data structures can be used to store active parking tickets.

Array:

- Stores tickets in a fixed-size collection.
- Searching for a ticket takes O(n) time.
- Space requirement is O(n).

ArrayList:

- Allows dynamic storage of tickets.
- Searching for a ticket takes O(n) time.
- Space requirement is O(n).

HashMap:

- Stores tickets using registration number as the key.
- Searching for a ticket takes O(1) average time.
- Space requirement is O(n).

A HashMap is suitable when the system needs to search for active tickets frequently using vehicle registration numbers.

7. Limitations

- The basic system may not support online payments.
- Vehicle details may not be stored permanently.
- Real-time parking availability may not be displayed.
- Security and user authentication may need improvement.
- A larger parking facility may require a database.

8. Conclusion

The Campus Smart-Parking System provides an organized approach to vehicle entry, slot allocation, fee calculation and vehicle exit. Testing normal, boundary and invalid cases helps identify errors and improve reliability. Using suitable data structures and OOP concepts makes the system easier to maintain and extend.
