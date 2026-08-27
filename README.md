# SEDS_INDUCTION_TASK
An ocean-floor monitoring system combining an Arduino-based sensor and state-machine setup with Python data analysis. The project uses Tinkercad to simulate sensor monitoring and Matplotlib to process and visualize depth data in real time, including handling corrupt and extreme measurements

Odysseus Ocean Floor Monitoring System

An Arduino and Python-based ocean-floor monitoring project combining a Tinkercad Arduino simulation with Python data analysis and visualization.

The Arduino component uses sensors and a state-machine system to monitor environmental conditions, while the Python component processes ocean-floor depth measurements and visualizes them progressively.

Project Overview

The project consists of two main components:

1. Arduino / Tinkercad Monitoring System

The Tinkercad simulation contains:

Arduino
Distance sensor
Light sensor
LCD display
Push button
LED
Buzzer

The Arduino program uses a state-machine approach to control the system based on sensor readings and user input. The current state is displayed on the LCD.

2. Python Ocean-Floor Data Analysis

The Python program reads ocean-floor depth measurements from Depth Data.csv and displays them using Matplotlib.

It includes:

CSV data processing
Handling of corrupt measurements
Handling of extreme sensor readings
Dynamic graph updating
Real-time visualization simulation
Tinkercad Simulation

The complete Arduino circuit can be viewed and simulated on Tinkercad:

Open the Odysseus Arduino Tinkercad Project

Open Tinkercad Project

Arduino / Tinkercad System
Components
Arduino
│
├── Distance Sensor
├── Light Sensor
├── LCD Display
├── Push Button
├── LED
└── Buzzer

The sensors provide environmental information to the Arduino, which uses the readings to determine the current state of the system.

State Machine

The Arduino program is organized into different states rather than handling all conditions in one block of code.

The general flow is:

              ┌─────────────┐
              │    STATE 1  │
              └──────┬──────┘
                     │
                     ▼
              ┌─────────────┐
              │    STATE 2  │
              └──────┬──────┘
                     │
                     ▼
              ┌─────────────┐
              │    STATE 3  │
              └─────────────┘

Sensor readings and button input determine when the system transitions between states.

The LCD displays the current state, while the LED and buzzer provide visual and audio feedback.

Python Ocean-Floor Analysis
Files
seds2.py
Depth Data.csv

The CSV file contains recorded ocean-floor measurements.

Expected format:

Point,Depth
1,-50.2
2,-52.7
3,-48.9
...

The first column represents the measurement point and the second column represents the depth.

Requirements
Python 3
Matplotlib

Install Matplotlib using:

pip install matplotlib

The Python program uses:

import csv
import matplotlib.pyplot as plt
import time
Real-Time Visualization

The Python program uses Matplotlib's interactive mode:

plt.ion()

Each measurement is added to the graph and the plot is updated dynamically.

The delay:

time.sleep(0.5)

simulates measurements arriving in real time.

The current system therefore simulates live data using the recorded CSV measurements.

Data Cleaning

The program handles invalid CSV values using exception handling.

For example, if a depth value cannot be converted into a number, the program skips that row instead of crashing.

Extreme measurements can also be identified and replaced with estimated values based on surrounding measurements, preventing a single faulty reading from distorting the graph.

Project Structure
Odysseus-Ocean-Floor/
│
├── README.md
├── seds2.py
├── Depth Data.csv
│
└── arduino/
    └── odysseus.ino

The Arduino circuit is available through the Tinkercad project linked above.

Running the Python Program

Place the Python script and CSV file in the same directory:

seds2.py
Depth Data.csv

Then run:

python seds2.py

The Matplotlib window will open and progressively display the ocean-floor depth data.

System Architecture

The overall concept is:

             TINKERCAD / ARDUINO
                     │
          ┌──────────┴──────────┐
          │                     │
   Distance Sensor        Light Sensor
          │                     │
          └──────────┬──────────┘
                     │
                  Arduino
                     │
              State Machine
                     │
              LCD / LED / Buzzer


          Recorded Depth Data
                  │
                  ▼
             Python / CSV
                  │
                  ▼
            Data Processing
                  │
                  ▼
             Matplotlib
                  │
                  ▼
            Depth Graph
Future Improvements
Connect the Arduino directly to Python using serial communication.
Replace the CSV input with live sensor data.
Add automatic outlier detection.
Display live sensor status.
Combine Arduino state information with the Python graph.
Save processed sensor measurements.
Build a physical version of the Tinkercad circuit.
Technologies Used
Technology	Purpose
Arduino	Sensor monitoring and state machine
Tinkercad	Circuit simulation
Distance Sensor	Distance measurement
Light Sensor	Environmental measurement
LCD	State display
Push Button	User input
LED	Visual feedback
Buzzer	Audio feedback
Python	Data processing
CSV	Data storage
Matplotlib	Data visualization
Purpose

The Odysseus Ocean Floor Monitoring System demonstrates the combination of embedded systems, sensor monitoring, data processing, and visualization.

The Arduino/Tinkercad component focuses on sensor input and state-machine control, while the Python component focuses on processing and visualizing ocean-floor depth data.https://www.tinkercad.com/things/3CIznUxZfU8-sedsaurduino?sharecode=1vJ5N5RSlcfiVbK8GGNGWLaZgiq7FBqAOhhL6DhOij0

The long-term goal is to connect these components so that sensor measurements can be collected by the Arduino and visualized live in Python.
