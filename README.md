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

![Code Snippet](.\images\userinput_handling.png "User Handling")

### Detailed Explanation

* Getting Network Range (`get_network_input`):
    * The script first prompts the user to input a network range in the format 192.168.x.x/24.
        * If the input doesn’t match the expected format, the script prints an error message and recursively calls the function to prompt the user again. This ensures that only valid input is accepted.    
    * **Regex Validation**: The input is validated using a regular expression that checks for proper IP address formatting (e.g., four octets separated by periods) and the subnet mask length (e.g., /24).
* Regex Breakdown:
    * ^\d{1,3}: This part checks for the first octet of the IP address, which should be a number between 1 and 3 digits long.
    * (\.\d{1,3}){3}: This checks for the next three octets, each separated by a dot, again ensuring they are between 1 and 3 digits.
    * /\d{1,2}$: This checks for the subnet mask, which is typically between 1 and 2 digits (e.g., /24).

    > Example Input:
    > Valid: 192.168.1.0/24
    > Invalid: 192.168.256.0/33

* Getting Output Directory (`get_output_directory`):
    * The user is asked whether they want to save the output in the current directory or specify a custom directory.
    * **Directory Handling**:
        * If the user chooses to save in the current directory (yes), the script uses os.getcwd() to get the current working directory and logs a status message indicating where the output will be saved.
        * If the user chooses a custom directory (no), the script prompts the user to input a directory path. If the directory doesn’t exist, it’s created using os.makedirs() to ensure that the output can be saved there.
        * If the user provides an invalid choice (not yes or no), the script recursively calls the function to prompt for valid input.

    > Example Input:
    > Choosing yes: The output will be saved in the current directory, such as /home/user/.
    > Choosing no: The user might input /home/user/custom_dir, and the script will create this directory if it doesn’t exist.
* Choosing Scan Type (get_scan_type):
    * The user is prompted to select either a "Basic" or "Full" scan.
    * **Input Validation**: The input is converted to lowercase and validated against the allowed choices (basic or full). If the input is invalid, the script prints an error message and prompts the user again.

    > Example Input:
    > Valid: basic, full
    > Invalid: medium (would trigger an error and prompt the user again)

#### Why This is Important

User input is a critical aspect of the script, as it defines how the subsequent processes will be executed. By validating inputs and providing feedback, the script ensures that only valid data is processed, minimizing the risk of errors during execution.

This part of the script adds flexibility, allowing users to customize the scanning process according to their needs. For example, they can specify which network range to scan and where to save the results, ensuring that the script fits seamlessly into their workflow.

    > Example in Practice
    > Network Input: When the script asks for the network range, the user might input 192.168.1.0/24.
      The script will validate this input and proceed only if it’s in the correct format.
    > Output Directory: If the user chooses to save the results in a custom directory,
      they might input /home/user/scans, and the script will create this directory if it doesn’t already exist.

By handling user inputs effectively, the script ensures that the entire process is configured correctly from the start, leading to more accurate and reliable outcomes. With these inputs set, the script can then move forward to the actual scanning and analysis
phases. This user-centric approach makes the tool both powerful and accessible to users of varying expertise levels.

### Perform the TCP Scan

### Overview

This part of the script is responsible for conducting the TCP scan using Nmap, which is essential for identifying open ports and services on the target network. The scan results are saved to a specified output file, allowing for further analysis in subsequent steps.

### Code Section

Below is the code snippet that handles the TCP scan:

![Code Snippet](.\images\tcpscan.png "tcp_scan")

### Detailed Explanation

* Nmap Command Breakdown:
    * `nmap -sS`: This flag tells Nmap to perform a TCP SYN scan, also known as a stealth scan. This type of scan sends SYN packets to the target ports and listens for responses, allowing it to detect open ports without completing the TCP handshake. It’s a widely used method because it’s faster and less detectable than a full TCP connection scan.
    * `-sV`: This flag enables version detection, which allows Nmap to probe open ports and determine the services running on them along with their version numbers. This is crucial for vulnerability assessment and further analysis.
    * -oN {output_file}: This flag specifies the output format (normal format) and the file where the results will be saved. By saving the scan results to a file, the script ensures that the data can be accessed and used later in the process.
* File Handling:
    * Output File Creation: The scan results are saved in a file named tcp_scan_results.txt in the specified output directory. This file will contain all the information gathered during the TCP scan, including open ports and detected services.
    * Directory Management: The script checks whether the specified output directory exists and creates it if necessary. This ensures that the scan results are saved in the correct location.
* Logging:
    * Status Updates: The script logs status messages to keep the user informed about the progress of the scan. For example, it informs the user when the scan is starting and when it has completed. This is helpful for managing expectations, especially since network scans can take some time depending on the network size and the number of hosts.

    > Example in Practice:
        > Suppose the user inputs a network range of 192.168.1.0/24. The generated Nmap command would be:
        > *  `nmap -sS -sV 192.168.1.0/24 -oN /path/to/output_directory/tcp_scan_results.txt`
* Output Format:
    * Normal Format Output: The -oN flag ensures that the results are saved in a human-readable format. This is important because the next steps in the script will parse this file to extract relevant information such as service names, versions, and ports.
* Importance of the TCP Scan:
    * The TCP scan is a foundational step in the network assessment process. It identifies the open ports and running services, which are key targets for further analysis, such as vulnerability mapping and brute-force attacks. By understanding the network’s attack surface, security practitioners can prioritize areas for deeper investigation.

#### Why This is Important

The TCP scan serves as the foundation for identifying potential entry points into the network. By discovering open ports and services, the script sets the stage for subsequent vulnerability assessments and brute-force attacks. This step is critical for understanding the network's exposure and identifying weak points that could be exploited by attackers.

By automating this process, the script ensures that all potential attack vectors are identified quickly and efficiently. This information is then used to guide further analysis, making it a crucial part of any cybersecurity assessment.

> Example in Practice
> After running the scan, the user might review the tcp_scan_results.txt file and see output like this:
> ![Code Snippet](.\images\tcpscan_example.png "tcpscan_example")
> This output reveals that FTP, SSH, and HTTP services are running on the target machine, with specific versions identified. These
> services become targets for further testing and exploitation. 
>
> * In summary, this part of the script efficiently identifies open 
>   ports and running services, setting the stage for the vulnerability assessments and brute-force attacks that follow. The use of
>   Nmap’s powerful scanning capabilities ensures comprehensive coverage of the network, while the output file provides a structured
>   format for analysis

### Extracting Service Ports

### Overview

This section of the script is responsible for parsing the results of the TCP scan and extracting
the open ports and corresponding services. The extracted data is stored in a dictionary for easy
access during the vulnerability assessment and brute-force attack stages.

### Code Section

Here is the code snippet that handles the extraction of service ports:

![Code Snippet](.\images\code_snippet.png "Code Snippet")

Every screenshot should have some text explaining what the screenshot is about.


Example below.