TASK 9 – ABSTRACT CLASSES AND INTERFACES

1. Introduction

Abstract classes and interfaces are important concepts in Java Object-Oriented Programming.

They provide a common structure for related classes and help achieve abstraction.

In the Campus Smart-Parking System, the Vehicle class is designed as an abstract class, while Chargeable is used as an interface for electric vehicles.

2. Abstract Class – Vehicle

An abstract class is a class that cannot be instantiated directly. It can contain both abstract methods and normal methods.

The Vehicle class is an abstract class because all vehicles share common properties, but their parking rates may differ.

Example:

abstract class Vehicle {
    private String regNo;

    Vehicle(String regNo) {
        this.regNo = regNo;
    }

    public String getRegNo() {
        return regNo;
    }

    protected abstract double ratePerHour();
}

The ratePerHour() method is abstract because each vehicle category provides its own parking rate.

3. Abstract Method Implementation

Subclasses must implement the abstract method unless they are also declared abstract.

Example:

class TwoWheeler extends Vehicle {
    TwoWheeler(String regNo) {
        super(regNo);
    }

    @Override
    protected double ratePerHour() {
        return 10;
    }
}

class Car extends Vehicle {
    Car(String regNo) {
        super(regNo);
    }

    @Override
    protected double ratePerHour() {
        return 30;
    }
}

Here, each subclass provides its own implementation of ratePerHour().

4. Interface – Chargeable

An interface defines a contract that implementing classes must follow.

The Chargeable interface is used for vehicles that support charging.

Example:

interface Chargeable {
    double chargingFee(int kWh);
}

The ElectricCar class implements this interface.

class ElectricCar extends Car implements Chargeable {
    ElectricCar(String regNo) {
        super(regNo);
    }

    @Override
    public double chargingFee(int kWh) {
        return kWh * 12;
    }
}

The charging fee is calculated at Rs. 12 per kWh.

5. Difference Between Abstract Class and Interface

Abstract Class:

- Can contain instance variables.
- Can have constructors.
- Can contain abstract and concrete methods.
- A class can extend only one class.
- Useful for sharing common properties and behaviour.

Interface:

- Defines a contract for implementing classes.
- Can contain abstract, default and static methods.
- Does not have constructors.
- A class can implement multiple interfaces.
- Useful for defining common capabilities.

6. Multiple Interfaces

Java does not support multiple inheritance of classes, but it allows a class to implement multiple interfaces.

Example:

interface Chargeable {
    double chargingFee(int kWh);
}

interface Payable {
    double calculatePayment();
}

class ElectricCar extends Car implements Chargeable, Payable {

    ElectricCar(String regNo) {
        super(regNo);
    }

    @Override
    public double chargingFee(int kWh) {
        return kWh * 12;
    }

    @Override
    public double calculatePayment() {
        return 100;
    }
}

Here, ElectricCar implements both Chargeable and Payable interfaces.

7. Default and Static Methods in Interfaces

An interface can contain default and static methods.

Default Method:

A default method provides a method implementation that implementing classes can use or override.

interface Chargeable {
    double chargingFee(int kWh);

    default void showChargingMessage() {
        System.out.println("Vehicle is charging");
    }
}

Static Method:

A static method belongs to the interface itself and can be called using the interface name.

interface Chargeable {
    static double getRate() {
        return 12;
    }
}

It can be called using:

double rate = Chargeable.getRate();

8. Alternative Approach

An alternative design is to use interfaces instead of an abstract Vehicle class.

For example, Vehicle can be changed into an interface with default methods, while Chargeable can be implemented for electric vehicles.

However, this approach loses the direct use of a shared Vehicle constructor and instance fields in a common superclass. Each implementing class would need to manage its own registration number.

Using an abstract class is more suitable when related classes share common state and constructors.

9. Time and Space Complexity

- Calling a vehicle's ratePerHour() method takes O(1) time in this design.
- Calling chargingFee() takes O(1) time.
- Storing n vehicle objects requires O(n) space.
- The interfaces do not introduce significant additional storage for each object.

10. Conclusion

Abstract classes and interfaces improve the design of the Campus Smart-Parking System. The abstract Vehicle class provides common vehicle information and behaviour, while the Chargeable interface defines charging functionality. These concepts improve abstraction, flexibility and code reusability.
