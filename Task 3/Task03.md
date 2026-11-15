TASK 3 – DESIGN THE CONTROL LOGIC

1. Slot Allocation Logic

The system searches each floor and its slots to find the first available parking slot. If a free slot is found, the vehicle is allocated to that slot and its floor and slot numbers are returned. If no free slot is available, the system returns null.

2. Parking Fee Calculation

The parking fee is calculated based on the vehicle type and parking duration. The system uses if-else statements to apply the appropriate fee.

- The first hour is charged according to the vehicle type.
- Every additional started hour is charged in full.
- A daily maximum fee can be applied.
- The fee is calculated based on the total parking duration.

3. Use of break, continue and return

- break: Stops a loop when the required condition is satisfied.
- continue: Skips the current iteration and moves to the next iteration.
- return: Returns the allocated slot or calculated fee and stops method execution.

4. Pseudocode for Slot Allocation

START

INPUT vehicleNo

FOR each floor
FOR each slot in the floor
IF slot is empty
Store vehicleNo in the slot
RETURN floor and slot
END IF
END FOR
END FOR

RETURN null

STOP

5. Pseudocode for Parking Fee Calculation

START

INPUT parking duration and vehicle type

IF parking duration is zero
fee = 0
ELSE
Calculate billable hours by rounding up
Get hourly rate based on vehicle type
fee = billable hours * hourly rate
END IF

IF daily maximum is applicable
Apply daily maximum limit
END IF

DISPLAY parking fee

STOP

6. Alternative Concept and Complexity Analysis

Instead of searching every floor and slot, we can maintain a count of free slots for each floor and a stack of available slot numbers.

In this approach, allocation takes a free slot directly from the stack, and release adds the slot back to the stack.

Comparison:

- Current approach: Allocation takes O(F × S) in the worst case because it searches all floors and slots.
- Stack approach: Allocation takes O(1) time.
- Current approach: Release takes O(1) time after validating the floor and slot.
- Stack approach: Release takes O(1) time.
- Both approaches require O(F × S) space for storing parking slots. The stack approach requires additional storage for free-slot information.

Here, F represents the number of floors and S represents the maximum number of slots per floor.

Conclusion

The parking allocation system uses nested loops to find available slots and conditional statements to validate and release occupied slots. The jagged array representation supports multiple floors with different slot capacities. The stack-based approach can improve allocation efficiency for larger parking facilities.
