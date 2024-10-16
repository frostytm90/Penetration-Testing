# Vulner

## Objective
This project is designed to simulate the mindset and methods of a potential attacker. By scanning the network, identifying vulnerabilities, and attempting to exploit them, Individuals can gain a deeper understanding of the network's weaknesses. This isn't just about finding holes in the system; it's about learning how an attacker might think and act, so we can strengthen our defenses.

### Skills Learned
#### Network Scanning and Mapping:
- Using tools like Nmap for scanning network ports and services.
- Differentiating between basic and full network scans (including NSE scripts).

#### Vulnerability Analysis:

- Automating the identification of vulnerabilities in local networks using tools like Searchsploit.
- Understanding how to use the Nmap Scripting Engine (NSE) for vulnerability assessment.

#### Password Cracking:

- Detecting weak passwords for common login services such as SSH, RDP, FTP, and TELNET.
- Working with tools like Hydra and Medusa to automate brute-force attacks.

#### User Input Handling:

- Creating functions to validate user inputs and make the process more user-friendly.
- Collecting user-defined parameters for network scans and password lists.

#### Logging and Reporting:

- Logging scan results and providing an option to search and save the results in a structured manner.
- Generating reports, including the ability to save results in a ZIP file for easy sharing.

#### Automation Scripting:

- Writing automated scripts using tools mentioned to minimize manual intervention.
- Leveraging functions to modularize the code and improve reusability.

#### Security Tools Familiarity:

- Gaining hands-on experience with popular penetration testing tools like Nmap, Hydra, Medusa, and Searchsploit.

#### Shell Scripting:

- Developing skills in Bash scripting to automate tasks.
- Using comments in code for documentation and attributing borrowed code.

#### Penetration Testing Workflow:

- Understanding and following a structured penetration testing workflow, including scanning, password cracking, vulnerability mapping, and result logging.

#### Credential Analysis:

- Evaluating credential strength in the network by using pre-defined or user-supplied password lists.

#### User Experience and Interface Design:

- Designing user interactions to select between basic or full scans, and enabling effective user feedback during each stage of the process.

#### Security Protocols Knowledge:

- Gaining knowledge of common network protocols such as SSH, RDP, FTP, and Telnet, and understanding their security implications.

#### Documentation:

- Documenting code with comments for better readability and understanding, especially when working in collaborative environments or for academic purposes.
- Preparing submission materials, including screenshots to demonstrate project functionality.

#### Data Management:

- Managing output data, including saving results in ZIP format for easy archival and transfer.
- Allowing search functionality within log results for efficient data retrieval.

#### Risk Identification and Mitigation:

- Learning how to identify security risks related to network vulnerabilities and weak passwords.
- Applying measures to understand potential mitigation strategies.

#### Operational Security Order:

- Familiarizing with the concept of an operation order and how it applies to structuring penetration testing projects for ongoing monitoring and asset protection.

#### Project Structuring and Modularity:

- Structuring a project into distinct modules (e.g., user input handling, weak credential detection, vulnerability mapping) to enhance maintainability and clarity of the code.

#### Use of Pre-built Tools and Custom Scripts:

- Learning how to effectively combine pre-built security tools and custom scripts to create an integrated penetration testing system.

#### Cybersecurity Automation Techniques:

- Building foundational knowledge in cybersecurity automation, especially focusing on tasks that benefit from reduced manual intervention to enhance security coverage and efficiency.

#### Report Generation and Presentation:

- Understanding the importance of presenting findings in a way that is useful to stakeholders, including providing clear visual representations and structured reports of detected vulnerabilities.

### Tools Used

1. Nmap - For network scanning and identifying open ports and services.
2. Hydra - For performing brute-force attacks on services like SSH, FTP, RDP, and Telnet.
3. Searchsploit - For identifying known vulnerabilities related to the services detected.
4. Nipe - For anonymizing the connection.
5. curl - Used for verifying anonymous connection.
    * jq - Used alongside curl for data manipulation in JSON format.
6. Grep - For searching within result files.
7. Zip Utility - For compressing result files into a ZIP archive.
8. apt-get - Linux package manager for installing and updating system tools.
9. pip - Python package installer for managing Python packages.
10. Geany - Text editor for manually viewing the results.

## Methodologies

The methodologies used in this project are focused on systematically identifying and evaluating the security posture of the network. The approach is divided into several stages, each utilizing specific tools and techniques to gather information, assess vulnerabilities, and attempt exploitation. The following sections detail the steps taken during the assessment.

### Network Scanning
* Method:
    * The script scans the network for open TCP ports and identifies the services running on them using Nmap. The scan aims to provide essential details about active services within the specified network range.

* Tools Used:
    * Nmap: Utilized for discovering open ports and identifying the services running on those ports. The script does not use NSE
    scripts.

* Command Example:
    * `Basic Scan: nmap -sS -sV {network_range}`

### Vulnerability Assessment

* Method:
    * The script identifies potential vulnerabilities by using service versions discovered in the network scan and cross-referencing them with known exploits.

* Tools Used:
    * Searchsploit: A command-line interface for the Exploit-DB database, allowing the script to find known exploits for the detected service versions.

* Command Example:
    * `searchsploit {service_version}`

### Brute-force Attacks

* Method:
    * This method tests for weak or default credentials on selected services by attempting multiple username and password combinations.

* Tools Used:
    * Hydra: A versatile tool for performing brute-force attacks on services such as SSH, FTP, RDP, and Telnet.

* Command Example:
    * `hydra -L {username_list} -P {password_list} {ip} {service} -s {port}`

#### Logging and Reporting

* Method:
    * All results from network scans, vulnerability assessments, and brute-force attacks are logged in a structured format. The script also offers options to search through these logs or compress them for further use.

* Tools Used:
    * Text Files: For storing results.
    * Grep: A command-line utility for searching within the results.
    * Zip Utility: For compressing all results into a single file.

* Command Example:
    * Search: `grep {search_term} {output_file}`
    * Zip: `zip -r scan_results.zip {output_directory}`

### Tool Management

* Method:
    * Ensures that all necessary tools are installed and up-to-date. This method checks for missing tools and installs them if necessary.

* Tools Used:
    * Apt-get (Linux Package Manager): Used for installing and updating system tools.
    * Pip (Python Package Installer): For managing Python packages.

* Command Example:
    * System Tools: `sudo apt-get install {missing_tools}`
    * Python Packages: `pip install {missing_packages}`

## Discussion

### Tools Check and Installation

### Overview

In the initial phase of the script, the goal is to ensure that all the necessary tools and Python packages are installed and up to date. This is crucial for the rest of the script to function correctly, as missing tools would cause errors later in the process.

### Code Section

Here’s the code snippet that handles tool checking, installation, and updating:

![Code Snippet](.\images\code_snippet.png "Code Snippet")

### Detailed Explanation

#### Tools List:
* required_tools: This dictionary holds the names of the tools that are necessary for the script to function. 
    
    For example:
    > * nmap for network scanning,
    > * searchsploit for vulnerability assessment,
    > * hydra for brute-force attacks,
    > * pip for Python package management.
    
    This ensures that the script covers different aspects of penetration testing, from scanning to exploitation.

* Tool Check Function (`is_tool_installed`):
    * This function tries to run each tool with the --version flag to check if it’s installed. If the tool isn’t found (FileNotFoundError), it returns False, indicating that the tool needs to be installed.
    * This approach is efficient because it doesn’t require complex checks and leverages existing command-line utilities to determine the presence of the tool.

* Installation and Update Function (`install_and_update_tools`):
    * Missing Tools Identification:
        * The script loops through the required tools and identifies any that aren’t installed. These tools are added to a missing_tools list, which will be installed later.
    * System Tools Installation:
        * If there are any missing tools, the script uses apt-get to update the package list (sudo apt-get update) and then installs the missing tools (`sudo apt-get install -y`). The ==-y== flag automatically answers "yes" to prompts during installation, ensuring the process is non-interactive.
        * If the installation fails, the script exits (sys.exit(1)), preventing further execution without the required tools.
        * Python Package Check and Installation:
            * Similar to system tools, the script checks if the required Python packages (like colorama) are installed. If they’re missing, the script uses pip to install them. This ensures that the script can handle colored output for better user experience.
* Error Handling:
    * The script handles errors gracefully by checking for issues during tool installation. If something goes wrong, it prevents further execution, ensuring that the user is aware of the problem and can resolve it before continuing.

#### Why This is Important 
Ensuring that the environment is correctly set up is a crucial first step in any script. By automating the process of checking for and installing necessary tools, this script reduces the likelihood of encountering errors later on due to missing dependencies. It also makes the script more user-friendly, as it handles the setup process automatically.
    
This part of the script essentially acts as a "gatekeeper," ensuring that all the necessary components are in place before the main functionality of the script begins.

### User Input Handling

### Overview

The script gathers various inputs from the user, such as the network range to scan, the output
directory, and the type of scan to perform. This section is essential because it sets up the
parameters for the entire operation, allowing for a tailored experience based on user needs.

### Code Section

Below is the code snippet that handles user input:


Every screenshot should have some text explaining what the screenshot is about.

Example below.