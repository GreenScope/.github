## Brief Description
GreenScope is a an Archive that stores information regarding the environment of Pakistan. It uses it's own apparatus called EEDLs (ESP Environmental Data Loggers) to gather relevant information. EEDLs are mini weather stations which take live readings and transmit them to the GreenScope database. GreenScope offers features such as graphing, AI data analysis and API keys to import readings for your own projects.

## Goal
We wish to promote the usage of Robotics in Measuring & Monitoring the environmental conditions of Pakistan at a greater extent. We wish to display a method cheap enough so that it can be used in remote non-urban areas. For this purpose the apparatus we developed, EEDL, costs roughly Rs 50K. We wish to make the data collected by GreenScope available to all including students to promote student projects based upon environment. This is why we not only provide an AI chatbot to analyze the data based on user requirements, but we also provide API keys to import the data into your own program.

## Scalability
At the current stage, Green Scope is just going to record data from different parts of Lahore, Pakistan, but the main selling point of our site is it's scalability. We are creating Green Scope in such a way that minimizes initial configurations and helps in the ease of expansion of the system. We intend to use a unified transmission setup that can be configured directly from the EEDL allowing us to introduce as many new EEDLs with no changes to the website. Should there be a need to make changes to the website we are using Jekyll, a static site builder, to ensure that any additions can be made by simply filling up a few variables.

<hr>

![Mind Map of GreenScope](https://github.com/user-attachments/assets/e234e7c3-354a-4fec-b5ca-ff55272b9b00)


<hr>

# EEDL
EEDL stands for *ESP32 Environmental Data Logger*. It uses multiple dedicated sensors to take readings and calculate certain values and transmits the values to the GreenScope database using PHP and SQL. The ESP32 serves as the control unit, transmitter and a sequencer. The EEDL costs roughly around Rs 50K and can record the following:

### Hardware
#### Sensors (Subject to change depending in availability)

| **Sensor**                   | **Price (Rs)** | **Parameters Recorded**                                    | **Communication Method** | **Calibration**  |
|:----------------------------:|:--------------:|:----------------------------------------------------------:|:-------------------------:|:---------------:|
| **BME280**                   | 500            | Temperature (°C), Relative Humidity (%), Pressure (hPa)    | I2C                       | None            |
| **BH1750**                   | 400            | Light Intensity (lux)                                      | I2C                       | None            |
| **SCD41**                    | 6,000          | CO₂ Concentration (ppm)                                    | I2C                       | None            |
| **CCS811**                   | 1,500          | Smoke Concentration (ppm)                                  | I2C                       | None            |
| **PMS5003**                  | 4,000          | PM2.5 Concentration (µg/m³)                                | Serial                    | None            |
| **SPEC Sensors 3SP-CO-1000** | 5,600          | CO Concentration (ppm)                                     | Current?                  | None?           |
| **TGS822**                   | 3,000          | Methane Concentration (ppm)                                | Analog                    | Analog to ppm   |

---

### Software methodology

The program has been divided into as many sub modules as possible to ensure minimum effects of runtime errors. Each sensor has it's own function and these are called by another sequencer function which ensures taking upto 10 readings before calculating the averages of the values and storing them in a custom defined data structure called "Reading".

After all values have been stored there will be another sequencing function that will transmit the readings to the database via a PHP file that injects the data using SQL.

---

### List of recordings

| No# | Quantity Name                |
|:---:|:-----------------------------|
| 1   | Temperature                  |
| 2   | Relative Humidity            |
| 3   | Absolute Humidity            |
| 4   | Dew Point                    |
| 5   | Atmospheric Pressure         |
| 6   | Light Intensity              |
| 7   | Air Content                  |
| 7.1 | CO<sub>2</sub> concentration |
| 7.2 | CO concentration             |
| 7.3 | CH<sub>4</sub> concentration |
| 7.4 | Smoke concentration          |
| 7.5 | PM2.5 concentration          |
| 7.6 | Air Quality Index            |

---

# Collaborators

| Name             | Contribution                                         |
|:----------------:|:-----------------------------------------------------|
| M. Umar Shahbaz  | Database, EEDL Design, Graph Plotter, Administration |
| Maarij Zafar     | EEDL software, AI Statistics                         |
| M. Ahsan Saleem  | Website, EEDL Build                                  |
| M. Haris         | Website, EEDL Build                                  |
| M. Taha          | Website, Media                                       |
| Ch. Abdur Rehman | EEDL Build, Calibration                              |
