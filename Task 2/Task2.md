TASK 2 – CHOOSE THE DATA REPRESENTATION

1. Data Types Used

The following Java data types are selected for the Campus Smart-Parking System.

- Slot number – int, used to store floor and slot numbers.
- Vehicle registration number – String, used to store vehicle numbers.
- Entry time – LocalDateTime, used to store vehicle entry date and time.
- Exit time – LocalDateTime, used to store vehicle exit date and time.
- Parking duration – long, used to store parking duration in minutes.
- Parking fee – double, used to store decimal fee values.
- Vehicle type – String or enum, used to identify vehicle categories.
- Ticket number – int, used to generate unique ticket IDs.

2. Representation of Floors and Slots

A two-dimensional jagged array is used to represent parking floors and slots.

Example:

String[][] slots = new String[3][];

slots[0] = new String[20];
slots[1] = new String[30];
slots[2] = new String[50];

Each row represents a parking floor, and each column represents a parking slot. A null value indicates an empty slot, while a vehicle registration number indicates an occupied slot.

A jagged array is suitable because different floors can have different numbers of parking slots.

3. Type Conversion and Casting

Type conversion is required when calculating parking duration and fees.

Example:

int minutes = 90;
double hours = minutes / 60.0;
System.out.println(hours);

Output:
1.5

If integer division is used:

double hours = minutes / 60;

The result will be 1.0 instead of 1.5 because integer division removes the decimal part.

Therefore, using 60.0 avoids loss of precision.

4. Input Method

The Scanner class is used to receive input from the user.

Example:

import java.util.Scanner;

class ParkingInput {
public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);

    System.out.print("Enter vehicle number: ");
    String vehicleNo = sc.nextLine();

    System.out.print("Enter vehicle type: ");
    String type = sc.nextLine();

    System.out.println("Vehicle Number: " + vehicleNo);
    System.out.println("Vehicle Type: " + type);

    sc.close();
}

}

Sample Output:

Enter vehicle number: TN01AB1234
Enter vehicle type: Car
Vehicle Number: TN01AB1234
Vehicle Type: Car

5. Alternative Concept and Complexity Analysis

Instead of using a jagged two-dimensional array, we can use a one-dimensional array or an ArrayList.

A one-dimensional array can use the formula:

index = floor × slotsPerFloor + slot

However, this formula is suitable when all floors have an equal number of slots. For different floor sizes, additional calculations or offset information are required.

Comparison:

Jagged Array:

- Represents floors and slots separately.
- Supports different floor sizes.
- Provides O(1) slot access.
- Requires O(S) space.

One-Dimensional Array:

- Stores all slots in a single sequence.
- Requires index mapping.
- Provides O(1) access.
- Requires O(S) space.

ArrayList:

- Supports dynamic storage.
- Can be used with nested lists for different floor sizes.
- Provides O(1) index access.
- Requires O(S) space.

Here, S represents the total number of parking slots.

Conclusion

A jagged array is selected because it supports different numbers of parking slots on different floors. It provides direct access to slots and is suitable for the Campus Smart-Parking System.
