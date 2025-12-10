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
    - From `vehicle_type_code_#`, flag for government-owned vehicles, ambulance, etc.

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

- There are no missing rows for `crash_date` or `number_of_persons_injured`. While there are many NaNs for all `vehicle_type_code_#` columns, we are only using them to create a new flag column, and can make reasonable assumptions based on the missing values (Info about assumptions detailed in the [assumptions](#assumptions) section).

- There was a lot of inconsistency in the strings. Specifically, the `vehicle_type_code_#` strings had many issues to deal with, including inconsistent letter case, leading & trailing whitespace, and invalid entries.

- Missing values in the `vehicle_type_code_#` columns were filled with an empty space to get rid of all NaNs.

- Mapped every vehicle entry to 1 of 19 categories: 
    `Sedan`, `SUV`, `Taxi`, `Pickup Truck`, `Van`, `Truck`, `Bus`,
    `Motorcycle`, `Moped`, `Scooter`, `Ambulance`, `Fire Truck`,
    `Garbage Truck`, `Delivery Truck`, `Forklift / Construction`,
    `Trailer`, `Government Vehicle`, `Commercial Vehicle`, or `Unknown`

- *Used keywords with theFuzz library to map certain keywords to government-owned vehicles:
    `fdny`, `nypd`, `usps`, `postal`, `mta`, `dot`,
        `city`, `nyc`, `ems`, `sanitation`,
        `gov`, `government`, `parks`, `transit`     
  
### Feature Engineering

`month` & `season`

### EDA Findings
  
Hour of Day vs Number of Collisions (All Collisions) | Barchart displaying Season vs. Number of Collisions grouped by Cause (All Collisions)
:-------------------------:|:-------------------------:
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/9bab05e7-43b9-40c3-8a49-62d93f79b0d9" /> | <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/d6ca9c7c-95b4-4c75-aa6f-0919babb53dd" />

- Line Chart Insights:
     - The two biggest jumps in collisions are the hours leading up to 8 AM and the hours leading up to 5 PM, indicating that most collisions may happen on the way to or from work.
     -  The majority of collisions happen during nighttime, indicating that the dark may be a factor in the collisions.
- Bar Chart Insights:
    - Surprisingly, Summer had the most collisions, and Winter had the least, despite dangerous weather conditions
        - An article based in Virginia [[1]](#ref1) cites the following factors as an explanation for the rise in collisions during summertime:
            - Inexperienced Teens on Summer Break
            - Traffic Congestion
            - Road Construction
            - Tourist in unfamiliar locations
            - Increased Number of Drivers and Trip Duration
            - Drunk Driving
            - Vehicle Failure
            - Fewer People on Non-Motorized Vehicles

- Government vehicles were involved in 157817/370001(~43%) of collisions in NYC from January 2022 - December 2025
<details>
  <summary>
 KPIs from collisions with government-owned vehicles (As listed in DataFrame):</summary>

###### Casualties:
    - Total persons injured in government vehicle crashes: 88938
    - Total persons killed in government vehicle crashes: 384
    - Number of government vehicle crashes with no injury or death: 95305
    - Total people affected by vehicle crashes: 184627

###### Causes:
    - Unspecified                                              169504
    - Driver Inattention/Distraction                            47387
    - Following Too Closely                                     13498
    - Failure to Yield Right-of-Way                             12257
    - Passing or Lane Usage Improper                             7886
    - Other Vehicular                                            7562
    - Unsafe Speed                                               6973
    - Passing Too Closely                                        5886
    - Traffic Control Disregarded                                5381
    - Backing Unsafely                                           5337
    - Turning Improperly                                         3832
    - Unsafe Lane Changing                                       3678
    - Alcohol Involvement                                        3678
    - Driver Inexperience                                        3675
    - Reaction to Uninvolved Vehicle                             2463
    - View Obstructed/Limited                                    1801
    - Pedestrian/Bicyclist/Other Pedestrian Error/Confusion      1706
    - Aggressive Driving/Road Rage                               1609
    - Pavement Slippery                                          1511
    - Fell Asleep                                                 930
    - Brakes Defective                                            736
    - Oversized Vehicle                                           497
    - Outside Car Distraction                                     465
    - Steering Failure                                            413
    - Obstruction/Debris                                          411
    - Passenger Distraction                                       404
    - Lost Consciousness                                          386
    - Illnes                                                      348
    - Glare                                                       304
    - Tire Failure/Inadequate                                     298
    - Fatigued/Drowsy                                             229
    - Failure to Keep Right                                       229
    - Driverless/Runaway Vehicle                                  186
    - Drugs (illegal)                                             143
    - Animals Action                                              135
    - Pavement Defective                                          125
    - Traffic Control Device Improper/Non-Working                 122
    - Accelerator Defective                                       110
    - Cell Phone (hand-Held)                                       92
    - Lane Marking Improper/Inadequate                             86
    - Physical Disability                                          85
    - Tinted Windows                                               39
    - Prescription Medication                                      33
    - Eating or Drinking                                           26
    - Vehicle Vandalism                                            25
    - Headlights Defective                                         25
    - Other Lighting Defects                                       19
    - Using On Board Navigation Device                             16
    - Tow Hitch Defective                                          13
    - Other Electronic Device                                      12
    - Cell Phone (hands-free)                                       9
    - Windshield Inadequate                                         7
    - Listening/Using Headphones                                    6
    - Shoulders Defective/Improper                                  6
    - Texting                                                       4
</details>

<a id="assumptions"></a>
### Assumptions & Limitations(*)

- For all columns regarding vehicle types, we assumed that missing values in these rows did not indicate government vehicle involvement unless explicitly stated.

- For the vehicles `Ambulance`, `Bus`, `Garbage Truck`, `Delivery Truck`, and `Fire Truck`, we assumed that they were all government-owned vehicles, not commercial or private.

-  The EDA puts all vehicles contributing to a collision on one line, separated by "|". This may affect the specific count of government vehicles, but it correctly gives the number of collisions involving government vehicles.

-  We assumed that the type of government-owned vehicles is listed with priority over the style of vehicle. E.g., we assume that none of the vehicles listed as a Sedan are government-owned, or else they would have been listed as such.

### References
<a id="ref1"></a>
1. Why are Car Accidents More Likely to Happen in the Summer?
  https://virginiatrialfirm.com/car-accident-lawyers/why-are-car-accidents-more-likely-to-happen-in-the-summer/
<br>
***

