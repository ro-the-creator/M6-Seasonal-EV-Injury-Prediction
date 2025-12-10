# **Initial EDA Tracker**

<div align='center'>

This markdown documents the initial EDA, cleaning, and proposed scope of the project.
</div>

# **Scope**

### Proposed Business Question

<div align='center'>

**Do drivers of government vehicles need more training??**
</div>

### Proposed Variables

- y = `number_of_persons_injured` (Continuous)

<br>

- X1 = `is_government` (Binary)
    - From `vehicle_type_code_#`, flag for e-bikes, e-scooters, etc.

    - No scaling needed?

<br>

- X2 = `season` (Categorical)
    - From `crash_date`

    - **Winter:** Dec, Jan, Feb

    - **Spring:** Mar, Apr, May

    - **Summer:** Jun, Jul, Aug

    - **Fall:** Sep, Oct, Nov

    <br>

- X3 = `government_crash_date` (Interaction)
    - How the effect of `is_government` changes given varying `season`.

### Factors to Tweak (If Output is Poor)

- Try phases of the day instead of seasons of the year

- Pull from Dec 2021 as well (for even season coverage)

- Try other injury/death statistic columns
    - `number_of_persons_killed`
    - `number_of_pedestrians_injured`
    - etc.

<br>

# Cleaning, Feature Engineering, & EDA

There are no missing rows for `crash_date` or `number_of_persons_injured`. While there are many NaNs for all `vehicle_type_code_#` columns, we are only using them to create a new flag column, and can make reasonable assumptions based on the missing values (Info about assumptions detailed in the [assumptions](#assumptions) section).

### Feature Engineering

`month` & `season`

### Assumptions & Limitations

- For all columns regarding vehicle types, we assumed that missing values in these rows did not indicate government vehicle involvement unless explicitly stated.

- For the vehicles `Ambulance`, `Bus`, `Garbage Truck`, `Delivery Truck`, and `Fire Truck`, we assumed that they were all government-owned vehicles, not commercial or private.

-  The EDA puts all vehicles contributing to a collision on one line, separated by "|". This may affect the specific count of government vehicles, but it correctly gives the number of collisions involving government vehicles.
<br>

***

