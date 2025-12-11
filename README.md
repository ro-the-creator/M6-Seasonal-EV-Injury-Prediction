# Module 6: Predicting EV-related Collision Injuries & Seasonal Trends

<div align='center'>

### **A predictive modeling project for the NYPD, forecasting seasonal trends of injuries involving government vehicles in New York City.**
</div>


# Project Overview

(README Directory here)

## Data Source

<div align='center'>

The dataset consists of vehicle accidents, where each row represents a unique crash event. According to NYC OpenData, each row is an MV104-AN police report, which is required to be filled out when someone is injured, killed, or when there is at least $1,000 worth of damage. More details, including an option to download the dataset, can be found [here](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95/about_data).

<br>

<details> <summary><strong> Data Dictionary (Click to Expand)</strong></summary> <br>
  
| **Column Name (Original)**    | **Description**                            | **Field Name (Cleaned)**        | **Type**           |
| ----------------------------- | ------------------------------------------ | ------------------------------- | ------------------ |
| CRASH DATE                    | Occurrence date of collision               | `crash_date`                    | Floating Timestamp |
| CRASH TIME                    | Occurrence time of collision               | `crash_time`                    | Text               |
| BOROUGH                       | Borough where collision occurred           | `borough`                       | Text               |
| ZIP CODE                      | Postal code of incident occurrence         | `zip_code`                      | Text               |
| LATITUDE                      | Latitude coordinate (WGS 1984, EPSG 4326)  | `latitude`                      | Number             |
| LONGITUDE                     | Longitude coordinate (WGS 1984, EPSG 4326) | `longitude`                     | Number             |
| LOCATION                      | Latitude, Longitude pair                   | `location`                      | Location           |
| ON STREET NAME                | Street on which the collision occurred     | `on_street_name`                | Text               |
| CROSS STREET NAME             | Nearest cross street to the collision      | `off_street_name`               | Text               |
| OFF STREET NAME               | Street address if known                    | `cross_street_name`             | Text               |
| NUMBER OF PERSONS INJURED     | Number of persons injured                  | `number_of_persons_injured`     | Number             |
| NUMBER OF PERSONS KILLED      | Number of persons killed                   | `number_of_persons_killed`      | Number             |
| NUMBER OF PEDESTRIANS INJURED | Number of pedestrians injured              | `number_of_pedestrians_injured` | Number             |
| NUMBER OF PEDESTRIANS KILLED  | Number of pedestrians killed               | `number_of_pedestrians_killed`  | Number             |
| NUMBER OF CYCLIST INJURED     | Number of cyclists injured                 | `number_of_cyclist_injured`     | Number             |
| NUMBER OF CYCLIST KILLED      | Number of cyclists killed                  | `number_of_cyclist_killed`      | Number             |
| NUMBER OF MOTORIST INJURED    | Number of vehicle occupants injured        | `number_of_motorist_injured`    | Number             |
| NUMBER OF MOTORIST KILLED     | Number of vehicle occupants killed         | `number_of_motorist_killed`     | Number             |
| CONTRIBUTING FACTOR VEHICLE 1 | Factors contributing to the collision      | `contributing_factor_vehicle_1` | Text               |
| CONTRIBUTING FACTOR VEHICLE 2 | Factors contributing to the collision      | `contributing_factor_vehicle_2` | Text               |
| CONTRIBUTING FACTOR VEHICLE 3 | Factors contributing to the collision      | `contributing_factor_vehicle_3` | Text               |
| CONTRIBUTING FACTOR VEHICLE 4 | Factors contributing to the collision      | `contributing_factor_vehicle_4` | Text               |
| CONTRIBUTING FACTOR VEHICLE 5 | Factors contributing to the collision      | `contributing_factor_vehicle_5` | Text               |
| COLLISION_ID                  | Unique record code (Primary Key)           | `collision_id`                  | Number             |
| VEHICLE TYPE CODE 1           | Vehicle category type                      | `vehicle_type_code1`            | Text               |
| VEHICLE TYPE CODE 2           | Vehicle category type                      | `vehicle_type_code2`            | Text               |
| VEHICLE TYPE CODE 3           | Vehicle category type                      | `vehicle_type_code_3`           | Text               |
| VEHICLE TYPE CODE 4           | Vehicle category type                      | `vehicle_type_code_4`           | Text               |
| VEHICLE TYPE CODE 5           | Vehicle category type                      | `vehicle_type_code_5`           | Text               |
</details>

</div>

## Business Problem

<div align='center'>

With increased tensions in NYC stemming from electric scooters and bikes, there has been a sharp spotlight on EV regulations. 

### **Safety concerns predate that rule change. A 2019 study by doctors at NYU Langone Medical Center, based on national data, found that e-bike riders were more likely to be seriously injured in crashes than riders of human-powered bicycles.**

</div>

<div align='right'>

#### **- Evan Simko-Bednarski, New York Daily News, TNS**

</div>
