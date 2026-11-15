TASK 4 – DESIGN CLASSES, OBJECTS AND CONSTRUCTORS

1. Class Design

The Campus Smart-Parking System uses the following classes:

1. Vehicle

- Fields: registrationNumber, vehicleType, entryTime.
- Methods: getRegistrationNumber(), calculateFee(), displayDetails().
- Purpose: Stores vehicle information and provides common vehicle operations.

2. TwoWheeler

- Fields: specific two-wheeler details.
- Methods: calculateFee().
- Purpose: Represents two-wheeler vehicles.

3. Car

- Fields: specific car details.
- Methods: calculateFee().
- Purpose: Represents cars and their parking charges.

4. ElectricCar

- Fields: batteryCapacity, chargingRequired.
- Methods: calculateFee(), chargingFee().
- Purpose: Represents electric vehicles and their charging requirements.

5. ParkingSlot

- Fields: floorNumber, slotNumber, isOccupied.
- Methods: allocateSlot(), releaseSlot().
- Purpose: Manages the availability of individual parking slots.

6. ParkingTicket

- Fields: ticketNumber, vehicle, entryTime, floorNumber, slotNumber.
- Methods: generateTicket(), displayTicket().
- Purpose: Stores parking entry details and identifies each parking session.

7. ParkingFacility

- Fields: totalFloors, slots, totalOccupancy.
- Methods: allocate(), release(), findAvailableSlot().
- Purpose: Manages the complete parking facility.

2. Types of Constructors

A constructor is a special method used to initialize an object. It has the same name as the class and does not have a return type.

Default Constructor:

A default constructor initializes an object with default values. It is useful when an object does not require values during creation.

Example:

class Vehicle {
    String regNo;

    Vehicle() {
        regNo = "Not Assigned";
    }
}

Parameterized Constructor:

A parameterized constructor accepts values when an object is created. It helps initialize an object with meaningful information.

Example:

class Vehicle {
    String regNo;

    Vehicle(String regNo) {
        this.regNo = regNo;
    }
}

Overloaded Constructors:

A class can contain multiple constructors with different parameter lists. This allows objects to be created in different ways.

Example:

class ParkingTicket {
    String ticketNumber;
    String regNo;

    ParkingTicket(String ticketNumber) {
        this.ticketNumber = ticketNumber;
    }

    ParkingTicket(String ticketNumber, String regNo) {
        this.ticketNumber = ticketNumber;
        this.regNo = regNo;
    }
}

3. Use of this Keyword and Constructor Chaining

The "this" keyword refers to the current object. It is used to distinguish instance variables from constructor parameters.

Constructor chaining allows one constructor to call another constructor in the same class using "this()".

Example:

class ParkingTicket {
    String ticketNumber;
    String regNo;

    ParkingTicket(String ticketNumber) {
        this(ticketNumber, "Not Assigned");
    }

    ParkingTicket(String ticketNumber, String regNo) {
        this.ticketNumber = ticketNumber;
        this.regNo = regNo;
    }
}

Here, the first constructor calls the second constructor using "this()". This avoids repeating initialization code.

4. Copy Constructor

A copy constructor creates a new object using the values of an existing object.

It can be useful when re-issuing a duplicate parking ticket. However, the new ticket should receive a new unique ticket number instead of copying the original ticket number.

Example:

class ParkingTicket {
    String ticketNumber;
    String regNo;

    ParkingTicket(ParkingTicket oldTicket, String newTicketNumber) {
        this.ticketNumber = newTicketNumber;
        this.regNo = oldTicket.regNo;
    }
}

This copies the vehicle registration number but assigns a new ticket number. Therefore, ticket numbers remain unique.

5. Object Storage in Memory

Java stores objects and references in different memory areas.

- Stack: Stores local variables and reference variables used by methods.
- Heap: Stores objects created using the "new" keyword.
- Reference Variable: Holds the reference to an object stored in the heap.

Example:

ParkingTicket ticket = new ParkingTicket("T101", "TN01AB1234");

Here, the "ticket" reference variable is local to the method and refers to a ParkingTicket object created in the heap.

When an object is no longer reachable through any reference, it becomes eligible for garbage collection.

6. Alternative Concept and Complexity Analysis

Instead of using overloaded constructors, objects can be created using a default constructor followed by setter methods.

Example:

ParkingTicket ticket = new ParkingTicket();
ticket.setTicketNumber("T101");
ticket.setRegNo("TN01AB1234");

Another approach is using static factory methods, which create and return objects through named methods.

Comparison:

- Overloaded constructors initialize objects directly and can ensure that required values are provided.
- Default constructors with setters allow values to be assigned later, but an object may temporarily contain incomplete or invalid data.
- Static factory methods provide meaningful names and can validate values before creating an object.

Time Complexity:

Creating one ParkingTicket object takes O(1) time for each approach, assuming a fixed number of fields and simple validation.

Creating n ParkingTicket objects takes O(n) time.

Space Complexity:

All three approaches require O(n) space to store n ParkingTicket objects. The object storage requirement does not significantly change based on the creation method.

Conclusion

Classes and objects help organize the Campus Smart-Parking System into manageable components. Constructors initialize objects, constructor chaining avoids repeated code, and the "this" keyword refers to the current object. Proper object creation ensures valid data and improves the reliability of the system.
