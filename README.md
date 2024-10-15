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

Tools Check and Installation
Overview
In the initial phase of the script, the goal is to ensure that all the necessary tools and Python packages are installed and up to date. This is crucial for the rest of the script to function correctly, as missing tools would cause errors later in the process.

Code Section

Here’s the code snippet that handles tool checking, installation, and updating:

![Code Snippet](C:\Users\frost\Penetration-Testing\images\code_snippet.png "Code Snippet")

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*