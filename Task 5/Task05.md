TASK 5 – APPLY STATIC MEMBERS AND THE OBJECT LIFE CYCLE

1. Static Variables

Static variables belong to the class rather than individual objects. They are shared by all objects of that class.

In the Campus Smart-Parking System, a static variable can be used for generating unique parking ticket numbers.

Example:

class ParkingTicket {
    static int ticketCounter = 1000;

    String ticketNumber;

    ParkingTicket() {
        ticketNumber = "T" + (++ticketCounter);
    }
}

Every new ParkingTicket object receives a different ticket number. A static variable is suitable because the ticket counter must be shared instead of starting separately for every ticket object.

2. Static Methods and Static Blocks

Static methods can be called using the class name without creating an object.

Example:

class ParkingTicket {
    static int ticketCounter = 1000;

    static int getTicketCount() {
        return ticketCounter - 1000;
    }
}

The method can be called using:

System.out.println(ParkingTicket.getTicketCount());

A static block is executed once when the class is initialized. It can be used to initialize static data.

Example:

static {
    ticketCounter = 1000;
}

Static methods are useful for operations related to the entire parking system, such as checking the ticket count.

3. Object Life Cycle and Garbage Collection

A ParkingTicket object is created when a vehicle enters the parking facility.

When the vehicle leaves, the ticket is processed and the parking slot is released. If the ticket object is no longer referenced by the program, it becomes eligible for garbage collection.

Garbage collection automatically removes objects that are no longer reachable. Java manages this process, so the programmer does not need to delete objects manually.

4. Passing and Returning Objects

Objects can be passed as arguments to methods and returned from methods.

Example:

class ParkingTicket {
    String ticketNumber;

    ParkingTicket(String ticketNumber) {
        this.ticketNumber = ticketNumber;
    }
}

class ParkingFacility {
    void displayTicket(ParkingTicket ticket) {
        System.out.println(ticket.ticketNumber);
    }

    ParkingTicket createTicket(String number) {
        return new ParkingTicket(number);
    }
}

Here, the ParkingTicket object is passed to the displayTicket() method and returned by the createTicket() method.

5. Alternative Concept and Complexity Analysis

The ticket counter can be implemented as an instance variable instead of a static variable.

If the counter is an instance variable, every ParkingFacility object maintains a separate counter. For example, the north gate and south gate may generate the same ticket number.

If the counter is static, all ParkingFacility objects share one counter, helping to maintain unique ticket numbers across the facilities.

Comparison:

- Static counter: One shared counter is maintained for all facility objects.
- Instance counter: Each facility object maintains its own counter.
- For k ParkingFacility objects, an instance counter requires O(k) space.
- A single static counter requires O(1) space.
- Generating the next ticket number takes O(1) time in both approaches.

If each facility must maintain a separate ticket sequence, an instance counter is suitable. If ticket numbers must be unique across the entire university, a shared static counter is more appropriate.

Conclusion

Static members are useful for storing common information such as ticket counters. Object life-cycle management and garbage collection help Java manage memory automatically. Objects can also be passed to and returned from methods, making the parking system easier to organize and maintain.
