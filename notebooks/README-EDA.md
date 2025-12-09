# **Initial EDA Tracker**

<div align='center'>

This markdown documents the initial EDA, cleaning, and proposed scope of the project.
</div>

# **Scope**

### Proposed Business Question

<div align='center'>

**Do electric vehicles during certain seasons contribute to more people injured?**
</div>

### Proposed Variables

- y = `number_of persons_injured` (Continuous)

<br>

- X1 = `is_electric` (Binary)
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

- X3 = `electric_crash_date` (Interaction)
    - How the effect of `is_electric` changes given varying `season`.

### Factors to Tweak (If Output is Poor)

- Try phases of the day instead of seasons of the year

- Pull from Dec 2021 as well (for even season converage)

- Try other injury/death statistic columns
    - `number_of_persons_killed`
    - `number_of_pedestrians_injured`
    - etc.

<br>

# Cleaning, Feature Engineering, & EDA

There are no missing rows for `crash_date` or `number_of_persons_injured`. While there are many NaNs for all `vehicle_type_code_#` columns, we are only using them to create a new flag column, and can make reasonable assumptions based on the missing values (Info about assumptions detailed in the [assumptions](#assumptions) section).

### Feature Engineering

`month` & `season`

### Assumptions

- For all columns regarding vehicle types, we assumed that missing values in these rows did not indicate electric vehicle involvement unless explicitely stated.

<br>

***


Can you help me decide on a model to use based on this scope:

### Proposed Business Question

**Do electric vehicles during certain seasons contribute to more people injured?**

### Proposed Variables

- y = `number_of persons_injured` (Discrete)

- X1 = `is_electric` (Binary)
    - From `vehicle_type_code_#`, flag for e-bikes, e-scooters, etc.

- X2 = `crash_date` (Categorical)
    - **Winter:** Dec, Jan, Feb

    - **Spring:** Mar, Apr, May

    - **Summer:** Jun, Jul, Aug

    - **Fall:** Sep, Oct, Nov

- X3 =