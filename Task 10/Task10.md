TASK 10 – PACKAGES, ACCESS MODIFIERS AND ENCAPSULATION

1. Introduction

Packages, access modifiers and encapsulation are important Java concepts used to organize and protect the Campus Smart-Parking System.

Packages group related classes, access modifiers control visibility, and encapsulation protects the internal data of objects.

2. Package Structure

The Campus Smart-Parking System can be divided into three packages.

1. parking.model
2. parking.service
3. parking.app

parking.model

Contains the main data classes:

- Vehicle
- TwoWheeler
- Car
- ElectricCar
- ParkingTicket
- ParkingSlot

parking.service

Contains the business logic:

- ParkingFacility
- FeeCalculationService
- VehicleAllocationService

parking.app

Contains the main application class:

- ParkingApplication

This structure improves code organization, readability and maintenance.

3. Access Modifiers

Java provides four main access levels.

Private:

- Accessible only within the same class.
- Used to protect important data.
- Example: private String regNo;

Default:

- Accessible only within the same package.
- Used when no access modifier is specified.

Protected:

- Accessible within the same package and by subclasses, subject to Java's inheritance access rules.
- Useful for inherited methods.

Public:

- Accessible from anywhere where the class is available.
- Used for methods that need to be accessed by other packages.

4. Encapsulation

Encapsulation means combining data and methods into a single class and restricting direct access to internal data.

In Java, encapsulation is achieved using private fields and public getter and setter methods.

Example:

class Vehicle {
    private String regNo;

    public Vehicle(String regNo) {
        setRegNo(regNo);
    }

    public String getRegNo() {
        return regNo;
    }

    public void setRegNo(String regNo) {
        if (regNo != null && !regNo.isEmpty()) {
            this.regNo = regNo;
        }
    }
}

Here:

- regNo is private.
- getRegNo() retrieves the registration number.
- setRegNo() updates it after validation.
- Direct access to regNo is restricted.

5. Data Validation

Validation ensures that only valid information is stored in the system.

Examples:

- Registration number should not be null or empty.
- Parking duration should not be negative.
- Slot number should be within the valid range.
- Parking fee should not be negative.

Validation prevents incorrect data from affecting the system.

6. Wrapper Classes and Autoboxing

Wrapper classes convert primitive data types into objects.

Examples:

- int – Integer
- double – Double
- char – Character
- boolean – Boolean

Autoboxing automatically converts a primitive value into its corresponding wrapper object.

Example:

int count = 10;
Integer total = count;

Unboxing converts a wrapper object into a primitive value.

Example:

Integer value = 20;
int number = value;

Important: Using == to compare Integer objects can produce unexpected results because it may compare object references instead of values. Use equals() to compare their values.

Example:

Integer a = 200;
Integer b = 200;

System.out.println(a.equals(b));

Output:

true

7. Alternative Approach – Public Fields

An alternative is to declare class fields as public instead of using private fields and getter/setter methods.

Example:

class Vehicle {
    public String regNo;
}

This allows direct access to the registration number but does not provide proper data protection or validation.

8. Comparison

Public Fields:

- Direct access to data.
- Simple to write.
- No automatic validation.
- Internal data can be changed from anywhere.
- May cause invalid values to enter the system.

Encapsulation:

- Uses private fields.
- Provides controlled access through methods.
- Allows validation at the point of modification.
- Improves data security and maintainability.
- Requires additional getter and setter methods.

Validation can be performed in setters, constructors or dedicated methods. Repeating the same validation in multiple places increases maintenance effort, so common validation logic should be reused.

9. Conclusion

Packages improve code organization, while access modifiers control the visibility of classes and members. Encapsulation protects important vehicle and parking information. Wrapper classes and autoboxing help work with primitive values as objects. These concepts make the Campus Smart-Parking System more secure, organized and maintainable.
