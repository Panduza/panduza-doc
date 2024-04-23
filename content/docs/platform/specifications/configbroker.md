# Panduza Python

# Prerequisites
- Windows or Linux
- Python3
- pip

# Installations and Implementations
# Windows
# Installations
1.	Install Python 3.x on your Windows system.
2.	Install the required Python packages using pip:
•	pip install cmath configparser subprocess threading flask logging psutil
# Implementation
1.	Create the configuration file at C:\Users\UF......\conf\network.json if it doesn't already exist.
2.	Save the provided code in a file (e.g., app.py) in your desired directory.
3.	Open a command prompt and navigate to the directory containing the app.py file.
4.	Run the application using the following command:
5.	python app.py
6.	The application will start running on http://192.168.97.45:8000/ (BROKER_HOST + BROKER_PORT that you choose).
7.	You can test the /update_config endpoint by sending a POST request with a JSON payload containing the new configuration.
# Linux
# Installations
1.	Install Python 3.x on your Linux system.
2.	Install the required Python packages using your system's package manager (e.g., apt-get, yum, dnf):
•	sudo apt-get install python3-cmath python3-configparser python3-subprocess python3-threading python3-flask python3-logging python3-psutil
# Implementation
1.	Create the configuration file at /etc/panduza/network.json if it doesn't already exist.
2.	Save the provided code in a file (e.g., app.py) in your desired directory.
3.	Open a terminal and navigate to the directory containing the app.py file.
4.	Run the application using the following command:
5.	python3 app.py
6.	The application will start running on http://192.168.97.45:8000/ (BROKER_HOST + BROKER_PORT that you choose).
7.	You can test the /update_config endpoint by sending a POST request with a JSON payload containing the new configuration.

# Specification for the provided code

This code is a Flask-based web application that provides an API for updating a configuration file. The application is designed to run on both Windows and Linux operating systems.

# Dependencies

The code uses the following Python libraries:
- `cmath`: for mathematical functions
- `configparser`: for reading and writing configuration files
- `subprocess`: for executing system commands
- `threading`: for running background tasks
- `flask`: for creating the web application
- `logging`: for logging error and informational messages
- `psutil`: for checking if a process is running
- `os`: for interacting with the operating system

# Functions

The code defines the following functions:

1. `is_mosquitto_running()`: Checks if the Mosquitto MQTT broker is running on the system.
2. `load_config()`: Reads the configuration file and returns a `configparser.ConfigParser` object.
3. `save_config(config)`: Writes the provided `configparser.ConfigParser` object to the configuration file.
4. `write_to_config_file(new_config)`: Writes the provided string `new_config` to the configuration file.



# Main Function
The `if __name__ == "__main__":` block sets up the logging configuration, starts a background thread (which is not implemented in the provided code), and runs the Flask application on the specified host and port.

# Configuration:
The code defines several constants related to configuration:
- `BROKER_HOST` and `BROKER_PORT`: the host and port of the MQTT broker.
- `API_HOST` and `API_PORT`: the host and port of the Flask API.
- `CONFIG_FILE`: the path to the configuration file, for example if on Windows, located at `C:\Users\UF187ATA\conf\network.json` on Windows or `/etc/panduza/network.json` on Linux. 

The code then checks if the configuration file exists. If it does not exist, it logs an error and returns a 500 error code.

# API Endpoint:
The code defines an API endpoint `/update_config` that accepts POST requests. This endpoint allows updating the configuration by writing the new JSON content to the configuration file.

Upon success, the endpoint returns a success message with an HTTP code 200. In case of an error, it returns an error message with an HTTP code 500.

# Error Handling:
The code defines two error handlers for 500 errors (internal server error). These error handlers log errors and return a generic error message to the user.

# Execution:
Finally, the code defines the main entry point of the application. It configures logging, starts a thread for the MQTT broker, and launches the Flask application on the host and port defined in the constants.
