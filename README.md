# Home Automation System

## Description

This repository contains the code for a home automation system designed to control the lighting based on environmental input using a Raspberry Pi. The system interfaces with an LDR (Light Dependent Resistor) to detect ambient light levels and controls an LED as an output device.

## Repository Structure

- `lightcontrol/`: The Django app that manages the lighting system.
  - `models.py`: Defines the data model for system settings.
  - `urls.py`: URL declarations for the application.
  - `views.py`: Handles requests and renders responses to the web interface.
  - `gpio_control.py`: Functions for interacting with GPIO pins (for LED and LDR).
  - `templates/dashboard.html`: HTML templates for the web interface.
  - `static/js/lightcontrol.js`: Static files like CSS and JavaScript for frontend interactivity.
- `myhomeautomation/`: The main project directory with settings and root configurations.
  - `settings.py`: Settings/configuration for the Django project.
  - `urls.py`: URL declarations for the entire Django project.
- `db.sqlite3`: The SQLite database file containing the application's persistent data.
- `manage.py`: The Django command-line utility for administrative tasks.

## Wiring Instructions

To use the home automation system, you'll need to connect the LED and LDR (Light Dependent Resistor) to your Raspberry Pi's GPIO pins. Follow these instructions to properly wire your components:

### LED Connection (GPIO 17):

1. Connect the longer lead (anode) of the LED to GPIO pin 17 (physical pin 11) on the Raspberry Pi.
2. Connect the shorter lead (cathode) of the LED to a current-limiting resistor.
3. Connect the other end of the resistor to one of the ground (GND) pins on the Raspberry Pi.
   
   - **Note:** Ensure that the LED is connected with the correct polarity (anode to GPIO 17 and cathode to GND) to avoid damaging the LED.

### LDR Connection (GPIO 4):

1. Connect one leg of the LDR to GPIO pin 4 (physical pin 7) on the Raspberry Pi.
2. Connect the other leg of the LDR to one of the 3.3V pins on the Raspberry Pi.
3. Place a pull-down resistor (10k ohms) between the same leg connected to GPIO 4 and a ground (GND) pin on the Raspberry Pi.

   - **Note:** The LDR is used to detect ambient light levels. The pull-down resistor ensures stable readings when the LDR is not exposed to light.

After completing these wiring connections, you can proceed with setting up and running the home automation system as described below.

## How to Execute the Code

### Prerequisites

- Python 3.7 or higher
- Django 1.11.29 or higher
- Raspberry Pi with GPIO access
- An LED and LDR correctly wired to the Raspberry Pi

### Setup

1. Clone the repository:

    ```bash
    git clone https://github.com/ahmaad-ansari/SOFE4610U-Assignment-3.git
    cd SOFE4610U-Assignment-3
    ```

2. Run database migrations:

    ```bash
    python3 manage.py makemigrations lightcontrol
    python3 manage.py migrate
    ```

### Running the Development Server

1. To start the server:

    ```bash
    python manage.py runserver 0.0.0.0:8000
    ```

2. Open a web browser and navigate to:

    ```
    http://<Raspberry_Pi_IP>:8000
    ```

### Usage

- Use the web interface to toggle the LED state or switch Auto Mode on/off.
- When Auto Mode is active, the LED is controlled automatically based on LDR input.

## Webserver Screenshots

Here you can provide screenshots of your web interface for the light control dashboard. This can help users to understand what the interface looks like and how it operates.

<img style="height:400px" src="https://github.com/ahmaad-ansari/SOFE4610U-Assignment-3/assets/88805493/69e71ba7-f723-4ac0-92fd-817c9d8e7ba6" alt="">
<img style="height:400px" src="https://github.com/ahmaad-ansari/SOFE4610U-Assignment-3/assets/88805493/20431deb-c280-4742-acfa-63835a145307" alt="">
<img style="height:400px" src="https://github.com/ahmaad-ansari/SOFE4610U-Assignment-3/assets/88805493/e9800e7e-8bef-4fcb-af59-15a41a8ba4ed" alt="">

## Sequence Diagram
Here is the sequence diagram illustrating the flow of operations from the user interaction to the database update and response back to the user for a simple LED toggle:

<img style="height:400px" src="https://github.com/ahmaad-ansari/SOFE4610U-Assignment-3/assets/88805493/3fd5cf51-c917-4fad-8ad9-4bdb4e82cf00" alt="">

## Demo Video




https://github.com/ahmaad-ansari/SOFE4610U-Assignment-3/assets/88805493/e49333a0-bb9f-43e9-91ed-733b6d8003c6





## Additional Notes

- The GPIO control code is tailored for the Raspberry Pi. Adaptations may be required for other platforms.
- This system is designed for demonstration purposes and is not production-ready.
