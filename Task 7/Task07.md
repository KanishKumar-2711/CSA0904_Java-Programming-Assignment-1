TASK 7 – METHOD OVERRIDING

1. Introduction

Method overriding is an object-oriented programming concept in which a subclass provides its own implementation of a method already defined in its superclass.

In the Campus Smart-Parking System, different vehicle types have different parking rates. Therefore, the calculateFee() and ratePerHour() methods can be overridden to provide vehicle-specific behaviour.

2. Method Overriding in the Parking System

The Vehicle class acts as the parent class, and TwoWheeler, Car and ElectricCar are subclasses.

Example:

class Vehicle {
    double ratePerHour() {
        return 0;
    }
}

class TwoWheeler extends Vehicle {
    @Override
    double ratePerHour() {
        return 10;
    }
}

class Car extends Vehicle {
    @Override
    double ratePerHour() {
        return 30;
    }
}

Here, both subclasses override the ratePerHour() method with their own parking rates.

3. Rules of Method Overriding

1. The method name must be the same as the superclass method.
2. The parameter list must be the same.
3. The return type must be the same or a compatible covariant return type.
4. The access level cannot be more restrictive than the superclass method.
5. The @Override annotation is used to identify an overridden method.
6. Static methods are hidden, not overridden.
7. Private methods cannot be overridden.

4. Use of @Override Annotation

The @Override annotation tells the compiler that a method is intended to override a superclass method.

Example:

class Car extends Vehicle {
    @Override
    double ratePerHour() {
        return 30;
    }
}

If the method name or parameters are incorrect, the compiler reports an error. This helps avoid accidental mistakes.

5. Use of final Keyword

The final keyword prevents further modification or overriding.

- A final variable cannot be reassigned.
- A final method cannot be overridden by subclasses.
- A final class cannot be inherited.

Example:

class Vehicle {
    final void displayRules() {
        System.out.println("Follow parking rules");
    }
}

The displayRules() method cannot be overridden by subclasses.

6. Overriding Object Class Methods

Java provides methods such as toString(), equals() and hashCode() through the Object class.

These methods can be overridden to provide meaningful behaviour.

toString():

@Override
public String toString() {
    return "Vehicle Registration Number: " + regNo;
}

This returns vehicle information as a readable string.

equals():

@Override
public boolean equals(Object obj) {
    if (this == obj) return true;
    if (!(obj instanceof Vehicle)) return false;

    Vehicle other = (Vehicle) obj;
    return regNo.equals(other.regNo);
}

This compares two vehicles using their registration numbers.

hashCode():

@Override
public int hashCode() {
    return regNo.hashCode();
}

The hashCode() method is overridden consistently with equals().

7. Alternative Approach – Using switch Statement

Instead of method overriding, parking fees can be calculated using a switch statement based on vehicle type.

Example:

double calculateFee(String type, int hours) {
    double rate;

    switch (type) {
        case "TwoWheeler":
            rate = 10;
            break;
        case "Car":
            rate = 30;
            break;
        default:
            rate = 0;
    }

    return rate * hours;
}

8. Comparison of Method Overriding and switch Statement

Method Overriding:

- Each vehicle subclass has its own implementation.
- New vehicle types can be added by creating subclasses.
- Uses runtime method selection.
- Fee calculation takes O(1) time for a fixed-rate implementation.
- Existing classes generally do not need changes when a new subclass is added.

Switch Statement:

- All vehicle rates are handled in one method.
- Adding a new vehicle type requires modifying the switch statement.
- The method checks vehicle type before calculating the fee.
- For k vehicle types, selection takes O(k) time in the worst case.
- The central calculation method must be updated when new types are introduced.

9. Conclusion

Method overriding allows different vehicle types to implement their own parking behaviour. It improves code reusability, flexibility and maintainability. The @Override annotation helps identify mistakes, while the final keyword prevents unwanted changes. Method overriding is more suitable than a large switch statement when the system supports multiple vehicle types.
