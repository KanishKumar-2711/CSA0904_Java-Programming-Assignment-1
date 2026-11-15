# TASK 12 – DAY-4 DESIGN CHALLENGE

## 1. Introduction

The university wants to extend the existing Campus Smart-Parking System by introducing new vehicle categories and additional parking rules.

The new requirements include:

1. Electric bikes with a flat parking fee.
2. Delivery vans charged at double the car parking rate between 9 AM and 5 PM.
3. Visitors who can purchase a one-day parking pass.
4. A larger parking facility containing five floors with different numbers of parking slots.

The existing design must be evaluated and modified to support these requirements without rewriting the complete system.

## 2. Impact Analysis

**Electric Bikes:**

A new ElectricBike class is required. It should support a flat parking fee instead of the normal hourly calculation.

**Delivery Vans:**

A new DeliveryVan class is required. Its parking fee should be calculated at twice the car rate when parked between 9 AM and 5 PM.

**Visitor One-Day Pass:**

A new pass system is required to identify visitors holding valid one-day passes. The system should apply the appropriate pass-based pricing rule.

**Five-Floor Parking Facility:**

The parking facility must support five floors with different numbers of slots. A jagged array can be used because each floor may have a different number of slots.

## 3. Evaluation of Existing Design

The existing design already uses inheritance, abstraction, interfaces and polymorphism.

However, some modifications are required to support the new rules.

- The Vehicle hierarchy must be extended with new vehicle categories.
- The fee calculation design must support different pricing rules.
- The ticket system must store the necessary entry and exit information.
- The parking facility must support different slot counts for each floor.
- The pass system must identify valid visitor passes.

Therefore, the existing design should be modified rather than completely redesigned.

## 4. Revised Class Structure

The revised design contains the following classes and interfaces:

**Vehicle (Abstract Class)**

Stores common vehicle information such as registration number and defines common vehicle behaviour.

**TwoWheeler**

Represents normal two-wheelers.

**Car**

Represents cars.

**ElectricCar**

Represents electric cars and implements the Chargeable interface.

**ElectricBike**

Represents electric bikes and provides a flat parking fee.

**DeliveryVan**

Represents delivery vans and applies the special time-based pricing rule.

**ParkingTicket**

Stores ticket number, vehicle details, entry time and exit time.

**ParkingFacility**

Manages floors, parking slots, allocation and release.

**Pass (Interface)**

Defines common pass validation behaviour.

**VisitorPass**

Represents a visitor's one-day parking pass.

**PricingRule (Interface)**

Defines a common method for calculating parking fees using different pricing rules.

## 5. Use of Jagged Array

A jagged array is suitable because each floor can have a different number of parking slots.

Example:

```java
String[][] parkingSlots = {
    new String[20],
    new String[25],
    new String[30],
    new String[35],
    new String[40]
};
```

Here, the parking facility contains five floors with different slot capacities.

The total number of slots is:

20 + 25 + 30 + 35 + 40 = 150 slots.

## 6. Implementation of New Categories

**ElectricBike:**

The ElectricBike class extends Vehicle and provides a flat parking fee.

Example:

```java
class ElectricBike extends Vehicle {
    ElectricBike(String regNo) {
        super(regNo);
    }

    double calculateFlatFee() {
        return 20;
    }
}
```

The flat fee in this example is Rs. 20.

**DeliveryVan:**

The DeliveryVan class extends Vehicle and uses a special rate during the specified time period.

Example:

```java
class DeliveryVan extends Vehicle {
    DeliveryVan(String regNo) {
        super(regNo);
    }

    double calculateVanFee(double carFee) {
        return carFee * 2;
    }
}
```

The delivery van fee is twice the car fee. The system must also check whether the parking period falls within the specified 9 AM to 5 PM rule.

## 7. Visitor One-Day Pass

A VisitorPass can be used to represent a valid one-day visitor parking pass.

The pass should store:
- Pass number
- Visitor details
- Valid date
- Pass status

The system checks whether the pass is valid before applying the pass-based pricing rule.

Example:

```java
interface Pass {
    boolean isValid();
}
```

A VisitorPass class can implement this interface and check its validity.

## 8. Revised Pricing Rule

A PricingRule interface can be introduced to separate fee calculation from vehicle information.

Example:

```java
interface PricingRule {
    double calculateFee(int minutes);
}
```

Different pricing classes can implement this interface:

- NormalHourlyPricing
- ElectricBikeFlatPricing
- DeliveryVanPricing
- VisitorPassPricing

This design allows new pricing rules to be introduced without changing the existing vehicle classes unnecessarily.

## 9. Testing the New Requirements

| Test Case | Expected Result |
|---|---|
| Electric bike enters | Flat fee applied |
| Delivery van during 9 AM–5 PM | Double car rate applied |
| Delivery van outside specified time | Normal applicable rate applied |
| Valid visitor pass | Pass benefit applied |
| Expired visitor pass | Pass benefit rejected |
| Five-floor parking facility | Different slot counts supported |
| Parking facility is full | New entry rejected |

The actual results must be recorded after executing the updated program.

## 10. Design Evaluation

The modified design supports the new requirements through inheritance, interfaces and separate pricing rules.

**Advantages:**
- New vehicle categories can be added.
- Pricing rules are separated from vehicle information.
- Different parking floor capacities are supported.
- Visitor passes can be validated independently.
- Existing functionality can be reused.

**Limitations:**
- More classes increase the complexity of the system.
- Pass validation requires date and status checking.
- Time-based pricing requires accurate entry and exit times.
- A database may be needed for permanent ticket and pass records.

## 11. Conclusion

The existing Campus Smart-Parking System can be extended by modifying its class structure and introducing new interfaces and pricing rules. Electric bikes, delivery vans, visitor passes and different floor capacities can be supported without completely rewriting the existing system. The revised design improves flexibility, maintainability and future extensibility.
