# Reverse Backdoor Attack

This project demonstrates a reverse backdoor attack where a compromised machine establishes a connection to an attacker-controlled listener. This allows the attacker to remotely execute commands, upload or download files, and maintain persistence on the target machine.

## Table of Contents
- [Project Overview](#project-overview)
- [Setup](#setup)
- [Usage](#usage)
- [Files](#files)
- [Google Slides Presentation](#google-slides-presentation)
- [Disclaimer](#disclaimer)

## Project Overview
The Reverse Backdoor Attack project consists of two Python files:
1. `listener.py`: A listener script that the attacker runs to accept incoming connections from compromised machines and execute commands remotely.
2. `backdoor.py`: A backdoor script that the compromised machine runs, which connects to the attacker's machine and executes received commands.

For a visual overview of the project, refer to the [Google Slides Presentation](https://docs.google.com/presentation/d/1cR8Kd3NaZGm7ixpJIfu66Cd8MsmYCI3oFXDkPCdrfos/edit#slide=id.g4dfce81f19_0_45).

## Setup

### Prerequisites
- Python 3.x
- Basic understanding of networking and socket programming

### Running the Listener
1. Update the IP address in `listener.py` to the attacker's IP address.
2. Start the listener on the attacker's machine:
   ```bash
   python listener.py
### Running the Backdoor
1. Update the IP address in `backdoor.py` to match the attacker's IP address.
2. Deploy and run `backdoor.py` on the target machine.

### Usage

#### Commands
Once the listener is connected to a target machine, you can use various commands:

- `download <file_path>`: Download a file from the target machine.
- `upload <file_path>`: Upload a file to the target machine.
- `cd <directory>`: Change the working directory on the target machine.
- `exit`: Close the connection.
- 
Example:

     ```bash
     Copy code
     >> download /path/to/target/file.txt
     [+] Download successful.
     

## Files

### listener.py
This script creates a socket listener, accepts incoming connections, and allows the attacker to execute remote commands.

#### Key Functions
- `reliable_send`: Serializes and sends data reliably.
- `reliable_receive`: Receives data and handles incomplete data.
- `execute_remotely`: Executes commands on the connected target machine.
- `write_file`: Decodes and writes downloaded files to the attacker's machine.
- `read_file`: Encodes and reads files for upload to the target.

### backdoor.py
This script runs on the target machine, connects back to the attacker's listener, and executes commands received from the attacker.

#### Key Functions
- `become_persistent`: Makes the script persistent by adding a registry key to start on boot (Windows).
- `reliable_send`: Serializes and sends data reliably.
- `reliable_receive`: Receives data and handles incomplete data.
- `execute_system_command`: Executes system commands on the target.
- `write_file`: Decodes and saves uploaded files from the attacker.
- `read_file`: Encodes files for download by the attacker.

## Google Slides Presentation
For a complete overview and additional details about the project, please view the [Google Slides Presentation](https://docs.google.com/presentation/d/1cR8Kd3NaZGm7ixpJIfu66Cd8MsmYCI3oFXDkPCdrfos/edit#slide=id.g4dfce81f19_0_45).

## Disclaimer
This project is intended solely for educational purposes. Unauthorized use of this code on any system without explicit permission is illegal and unethical. Ensure that any testing is conducted in a controlled environment with appropriate permissions.
