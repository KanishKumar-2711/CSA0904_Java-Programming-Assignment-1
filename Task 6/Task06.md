TASK 6 – DESIGN THE INHERITANCE HIERARCHY

1. Introduction

Inheritance is an important concept in Java that allows one class to acquire the properties and methods of another class. In the Campus Smart-Parking System, inheritance is used to represent different types of vehicles such as TwoWheeler, Car and ElectricCar.

2. Superclass and Subclasses

The Vehicle class is the superclass because all vehicles share common properties and behaviours.

The subclasses are:

- Vehicle – Contains common details such as registration number and parking fee calculation.
- TwoWheeler – Represents two-wheeler vehicles.
- Car – Represents car vehicles.
- ElectricCar – Represents electric cars and their charging facility.

The design uses hierarchical and multilevel inheritance.

- Hierarchical inheritance: TwoWheeler and Car inherit from Vehicle.
- Multilevel inheritance: ElectricCar inherits from Car, which inherits from Vehicle.

3. Inherited and Additional Properties

Vehicle (Superclass)

Fields:

- Registration number

Methods:

- getRegNo()
- calculateFee()
- ratePerHour()

TwoWheeler (Subclass)

Inherited:

- Registration number
- Common vehicle methods

Additional behaviour:

- Parking rate of Rs. 10 per hour.

Car (Subclass)

Inherited:

- Registration number
- Common vehicle methods

Additional behaviour:

- Parking rate of Rs. 30 per hour.

ElectricCar (Subclass)

Inherited:

- Registration number and vehicle methods from Vehicle through Car.

Additional behaviour:

- Charging fee calculation.
- Charging rate of Rs. 12 per kWh.

4. Use of super Keyword

The "super" keyword is used to access the superclass constructor, fields and methods.

Using super for constructors:

class Car extends Vehicle {
    Car(String regNo) {
        super(regNo);
    }
}

This calls the Vehicle constructor and initializes the registration number.

Using super for methods:

class ElectricCar extends Car {
    ElectricCar(String regNo) {
        super(regNo);
    }

    void display() {
        System.out.println(getRegNo());
    }
}

The subclass uses the inherited method to access the registration number.

Using super for fields:

If a subclass needs to access a protected field from its superclass, it can use "super.fieldName". Private fields cannot be accessed directly from a subclass and should be accessed through public or protected methods.

5. Constructor Execution Order

When an ElectricCar object is created, constructors execute from the topmost superclass to the lowest subclass.

Example:

ElectricCar e = new ElectricCar("TN03C3");

Execution order:

1. ElectricCar constructor starts.
2. It calls the Car constructor using "super(regNo)".
3. Car constructor calls the Vehicle constructor.
4. Vehicle constructor initializes the registration number.
5. Car constructor completes.
6. ElectricCar constructor completes.

Therefore, the constructor execution order is:

Vehicle → Car → ElectricCar

6. UML Class Diagram

             Vehicle
                |
       -------------------
       |                 |
   TwoWheeler           Car
                          |
                     ElectricCar

- Vehicle is the superclass.
- TwoWheeler and Car are subclasses.
- ElectricCar is a subclass of Car.

7. Alternative Concept – Composition

Instead of inheritance, composition can be used.

In this approach, a single Vehicle class contains a VehicleType object. The VehicleType object stores the vehicle category and its hourly rate.

Example:

class VehicleType {
    String type;
    double rate;

    VehicleType(String type, double rate) {
        this.type = type;
        this.rate = rate;
    }
}

class Vehicle {
    String regNo;
    VehicleType vehicleType;

    Vehicle(String regNo, VehicleType vehicleType) {
        this.regNo = regNo;
        this.vehicleType = vehicleType;
    }

    double calculateFee(int hours) {
        return hours * vehicleType.rate;
    }
}

8. Comparison of Inheritance and Composition

Inheritance:

- Each vehicle type has its own subclass.
- Adding a new type requires creating a new subclass.
- Fee calculation uses the subclass-specific rate method.
- Method execution takes O(1) time.
- Each vehicle object stores its common data and has an object of its specific subclass.

Composition:

- A single Vehicle class uses a VehicleType object.
- Adding a new type mainly requires creating a new VehicleType configuration.
- Fee calculation takes O(1) time when the rate is directly available.
- Each vehicle stores a reference to its VehicleType object.

Both approaches have O(1) fee calculation time in this simple design. Composition can make adding vehicle categories easier, while inheritance is useful when vehicle types have different behaviours.

9. Conclusion

Inheritance helps organize the vehicle classes and reduces repeated code. The Vehicle class contains common properties, while subclasses provide their specific behaviour. Composition is another approach that can make the system easier to extend when new vehicle categories are introduced.
