TASK 8 – POLYMORPHISM

1. Introduction

Polymorphism is an important feature of Object-Oriented Programming. It allows one method or reference to behave in different ways depending on the situation.

In the Campus Smart-Parking System, polymorphism is used to calculate parking fees for different vehicle types.

Java supports two types of polymorphism:

1. Compile-time polymorphism
2. Runtime polymorphism

2. Compile-Time Polymorphism

Compile-time polymorphism is achieved through method overloading.

Method overloading means defining multiple methods with the same name but different parameter lists.

Example:

double calculateFee(int minutes) {
    return minutes * 1.0;
}

double calculateFee(int entryHour, int exitHour) {
    return (exitHour - entryHour) * 30.0;
}

Both methods have the same name but accept different parameters. The compiler decides which method to call based on the arguments.

3. Runtime Polymorphism

Runtime polymorphism is achieved through method overriding.

A parent class reference can store an object of its child class. The overridden method that executes depends on the actual object.

Example:

Vehicle v = new Car("TN02B2");

Here, the reference type is Vehicle, but the actual object is Car.

When an overridden method is called, Java executes the Car implementation at runtime.

4. Upcasting and Dynamic Method Dispatch

Upcasting means assigning a subclass object to a superclass reference.

Example:

Vehicle[] parked = {
    new TwoWheeler("TN01A1"),
    new Car("TN02B2"),
    new ElectricCar("TN03C3")
};

The Vehicle array stores objects of different subclasses.

When calculateFee() is called for each object, Java selects the appropriate implementation using dynamic method dispatch.

This reduces the need for separate fee-calculation code for every vehicle type.

5. Trace of Declared Type and Actual Object

Reference type| Actual object| Behaviour
Vehicle| TwoWheeler| Uses two-wheeler rate
Vehicle| Car| Uses car rate
Vehicle| ElectricCar| Uses car rate and charging fee

The reference type determines which methods are accessible, while the actual object determines which overridden implementation executes.

6. Complete the Code – FeeDemo

The given FeeDemo program contains three TODO sections:

1. Calculate the parking fee by charging every started hour.
2. Complete the Car constructor and its hourly rate.
3. Implement the ElectricCar charging fee.

The completed Java program is provided separately as "FeeDemo.java".

7. Alternative Approach

An alternative approach is to use a switch statement based on the vehicle type instead of runtime polymorphism.

For example, the program can check whether the vehicle is a TwoWheeler, Car or ElectricCar and calculate the corresponding fee.

However, this approach requires modifying the central calculation method whenever a new vehicle category is added.

8. Comparison

Polymorphism:

- Uses method overriding and dynamic method dispatch.
- Each subclass provides its own behaviour.
- New vehicle types can be added with less modification to existing code.
- Method selection takes O(1) time for this design.

Switch Statement:

- Checks the vehicle type before calculating the fee.
- The central method must be updated when a new type is added.
- For k vehicle types, selection can take O(k) time.
- All vehicle-specific fee logic is maintained in one method.

9. Conclusion

Polymorphism makes the Campus Smart-Parking System flexible and reusable. Compile-time polymorphism is achieved through method overloading, while runtime polymorphism is achieved through method overriding. Using a common Vehicle reference allows different vehicle objects to be processed through the same code.
