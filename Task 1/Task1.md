TASK 1 – Understand the Problem and Identify the Objects

1. Problem Analysis

The Campus Smart-Parking System is designed to manage vehicle parking in a university. It supports multiple floors and different vehicle types such as two-wheelers, cars and electric vehicles.

When a vehicle enters, the system checks for an available parking slot, allocates the slot and generates a unique parking ticket. When the vehicle leaves, the system releases the slot and calculates the parking fee based on the vehicle type and parking duration.

2. Inputs and Outputs

Inputs:

- Vehicle registration number
- Vehicle type
- Vehicle entry time
- Vehicle exit time
- Floor and slot details
- Monthly pass details

Outputs:

- Allocated parking floor and slot number
- Unique parking ticket
- Parking duration
- Calculated parking fee
- Slot availability status

3. Candidate Classes and Their Responsibilities

Class| Responsibility
Vehicle| Stores vehicle registration number and type
TwoWheeler| Represents two-wheeler vehicles
Car| Represents car vehicles
ElectricCar| Represents electric vehicles
ParkingSlot| Maintains slot number and availability
ParkingFloor| Manages parking slots on a floor
ParkingTicket| Stores ticket number, entry time and vehicle details
ParkingFacility| Manages floors, allocation and release of slots
User| Stores user information
Student| Represents student users
Staff| Represents staff users
Visitor| Represents visitor users

Each class has a separate responsibility, making the system easier to maintain and extend.

4. Business Rules

1. A parking slot can hold only one vehicle at a time.
2. A vehicle must be allocated only to a suitable free slot.
3. Every parking ticket must have a unique ticket number.
4. A vehicle cannot be parked without a valid registration number.
5. An occupied slot must be released when the vehicle leaves.
6. Students and staff with valid monthly passes can park free of charge.
7. Visitors must pay the applicable parking fee.
8. Electric vehicles can use charging slots with separate charges.

5. Assumptions

- The parking facility has multiple floors.
- Each floor contains a fixed number of parking slots.
- Vehicle registration numbers are unique.
- Parking fees depend on vehicle type and parking duration.
- The system records entry and exit times.
- Monthly passes are valid only for eligible students and staff.

6. Alternative Concept and Complexity Analysis

In the object-oriented approach, each vehicle is represented as a Vehicle object containing its registration number, type and entry time.

Alternatively, vehicles can be stored using parallel arrays:

- regNo[] – stores registration numbers.
- type[] – stores vehicle types.
- entryTime[] – stores entry times.

Comparison:

Feature| Object-Oriented Approach| Parallel Arrays
Vehicle storage| Vehicle objects| Separate arrays
Searching| O(n)| O(n)
Adding a new attribute| Add a field to Vehicle class| Add another parallel array
Maintenance| Easier| More difficult

Conclusion:

The object-oriented approach is better because it groups related vehicle information into a single object. It improves readability, maintainability and extensibility. Both approaches require O(n) time for a linear search. Each vehicle requires O(1) storage, but parallel arrays require additional array management.
