**System Hardware ID Generator Script Documentation**

[![DOI](https://zenodo.org/badge/890989091.svg)](https://doi.org/10.5281/zenodo.14187889)
[![License](https://img.shields.io/badge/license-Custom-blue.svg)](LICENSE.md)
[![Python Version](https://img.shields.io/badge/python-3.6%2B-blue)](https://www.python.org/downloads/)
[![Cross-Platform](https://img.shields.io/badge/cross--platform-yes-brightgreen.svg)](#4-detailed-description)
[![License Management](https://img.shields.io/badge/license-management-blue.svg)](README.md#6-applications-and-use-cases)
[![Hardware ID](https://img.shields.io/badge/hardware-identification-blue.svg)](README.md#41-generating-hardware-id-hwid)
[![Device Auth](https://img.shields.io/badge/device-authentication-green.svg)](README.md#6-applications-and-use-cases)
[![Code Protection](https://img.shields.io/badge/code-protection-red.svg)](README.md#key-features)
[![Secure Distribution](https://img.shields.io/badge/secure-distribution-green.svg)](README.md#7-recommendations-and-best-practices)
[![Python Security](https://img.shields.io/badge/python-security-blue.svg)](README.md#security-and-best-practices)


*Version: 1.1\
© 2024 αβ.net (alphabetanet.com) - Alpha Beta Network. All Rights
Reserved.*

------------------------------------------------------------------------

**Note:** This project is currently in **Beta Testing** and available
for free.

**Table of Contents**

- [1. Introduction](#1-introduction)
- [2. Installation](#2-installation)
  - [2.1 Installing Required Packages](#21-installing-required-packages)
- [3. Main Functions of the Script](#3-main-functions-of-the-script)
- [4. Detailed Description](#4-detailed-description)
  - [4.1 Generating Hardware ID (HWID)](#41-generating-hardware-id-hwid)
  - [4.2 Using the Script as a Module](#42-using-the-script-as-a-module)
- [5. Usage Examples](#5-usage-examples)
  - [5.1 Running the Script Directly](#51-running-the-script-directly)
  - [5.2 Importing the Module](#52-importing-the-module)
  - [5.3 Using the .pyz Archive](#53-using-the-pyz-archive)
- [6. Applications and Use Cases](#6-applications-and-use-cases)
- [7. Recommendations and Best Practices](#7-recommendations-and-best-practices)
- [Appendix A: Generating Hardware IDs](#appendix-a-generating-hardware-ids)
- [Appendix B: Contact Information](#appendix-b-contact-information)

------------------------------------------------------------------------

# 1. Introduction

The **System Hardware ID Generator Script** is a Python tool designed to
generate a unique Hardware ID (HWID) for the device it runs on. The HWID
is represented as an 18-digit integer, making it efficient for storage
in databases and indexing. This script can be used in various
applications such as software licensing, device authentication, and
hardware inventory management.

Key features of the script include:

-   **Unique Hardware Identification**: Generates a unique HWID based on
    the system\'s hardware information.

-   **Cross-Platform Compatibility**: Works on Windows, macOS,
    Linux/Unix, and other operating systems where Python 3.6+ is
    installed.

-   **Modular Design**: Can be used as a standalone script or imported
    as a module in other Python projects.

-   **Cached HWID Value**: Caches the HWID value during import for
    performance optimization.

This tool is effectively used in the Alpha Beta Network cloud platform,
including the [Python Obfuscator
Online](https://obfuscator.xn--mxac.net/), [Secure Python Code Manager
Script](https://github.com/alphabetanetcom/secure-python-code-manager),
and [Local Python Code Protector
Script](https://github.com/alphabetanetcom/local-python-code-protector).\
\
The published scripts system_hardware_id_generator.py (uses cloud
protection) and system_hardware_id_generator.pyz (uses local protection
and is able to run without internet connection) are ready-to-use secure
cross platform versions in order to ensure the confidentiality of the
algorithm used.

------------------------------------------------------------------------

# 2. Installation

Before using the System Hardware ID Generator Script, ensure that you
have **Python 3.6+** installed on your system.

**2.1 Installing Required Packages**

The script requires the following Python packages:

-   requests

-   psutil

-   cryptography

You can install them using pip:

```bash

pip install requests psutil cryptography
```
Ensure that you are using the correct version of pip associated with
your Python 3 installation. If you are using a virtual environment,
activate it before installing the package.

------------------------------------------------------------------------

# 3. Main Functions of the Script

The System Hardware ID Generator Script provides the following
functionalities:

-   **Generate Hardware ID (HWID)**: Computes a unique HWID based on the
    system\'s hardware and platform information.

-   **Provide HWID via Module Import**: Allows other Python scripts to
    import the module and obtain the HWID programmatically.

------------------------------------------------------------------------

# 4. Detailed Description

## 4.1 Generating Hardware ID (HWID)

The script gathers system information such as hostname, processor,
system type, and machine architecture. It then concatenates these
details and computes a SHA-256 hash. The hash is converted to an
18-digit integer, which serves as the unique HWID.

**Key Functions:**

-   Saves the HWID to a log file named system_hardware_id\_\<HWID\>.log.

-   generate_hwid(): Public function that returns the cached HWID.

## 4.2 Using the Script as a Module

The script is modular and can be imported into other Python projects. It
provides the generate_hwid() function, which returns the cached HWID
value. This ensures that the HWID is generated only once per session,
optimizing performance.

**Error Handling:**

-   The script includes try-except blocks to handle potential exceptions
    during HWID generation and file operations.

-   If an error occurs, a warning message is displayed, and a default
    HWID of \"0\" is returned.

------------------------------------------------------------------------

# 5. Usage Examples

## 5.1 Running the Script Directly

To generate and display the HWID, run the script directly from the
command line:

```bash

python system_hardware_id_generator.py
```
**Output:**

```javascript

Your Hardware ID (HWID) is: 123456789012345678
```
The HWID will also be saved to a log file
named system_hardware_id_123456789012345678.log in the current
directory.

## 5.2 Importing the Module

You can import the script as a module in your Python project to obtain
the HWID:

```python

# test_hwid.py

from system_hardware_id_generator import generate_hwid

def main():
    try:
        hwid = generate_hwid()
        print(f"Generated HWID: {hwid}")
        print(f"HWID length: {len(hwid)} characters")
    except Exception as e:
        print(f"Error occurred while generating HWID: {e}")

if __name__ == "__main__":
    main()
```
**Example Output:**

```javascript

Generated HWID: 123456789012345678

HWID length: 18 characters
```
*This example is based on the test_hwid.py file.*

## 5.3 Using the .pyz Archive

The script can be packaged into a .pyz archive for distribution. To use
the module from the .pyz file:

```python

# test_hwid_from_pyz.py
import sys

# Add .pyz archive path to the system's module search path
sys.path.insert(0, 'system_hardware_id_generator.pyz')

from system_hardware_id_generator import generate_hwid

def main():
    try:
        hwid = generate_hwid()
        print(f"Generated HWID: {hwid}")
        print(f"HWID length: {len(hwid)} characters")
    except Exception as e:
        print(f"Error occurred while generating HWID: {e}")

if __name__ == "__main__":
    main()
```
**Instructions:**

-   Ensure the system_hardware_id_generator.pyz file is in the same
    directory as your script or provide the correct path.

-   This approach adds the .pyz archive to the system path, allowing you
    to import modules contained within it.

**Example Output:**

```javascript

Generated HWID: 123456789012345678

HWID length: 18 characters
```
*This example is based on the test_hwid_pyz.py file.*

------------------------------------------------------------------------

# 6. Applications and Use Cases

The System Hardware ID Generator Script can be used in various
scenarios:

-   **Software Licensing**:

    -   Bind licenses to specific devices using the HWID.

    -   Control the number of software installations.

    -   Prevent unauthorized software usage.

-   **Security Systems**:

    -   Identify devices in corporate networks.

    -   Track suspicious activities from specific devices.

    -   Authenticate devices accessing protected resources.

-   **Monitoring and Inventory**:

    -   Manage hardware assets in organizations.

    -   Track changes in device configurations.

    -   Automate IT asset inventory.

-   **Analytics and Statistics**:

    -   Collect data about devices used.

    -   Analyze user distribution by hardware types.

    -   Track unique software installations.

-   **Technical Support**:

    -   Quickly identify devices during support requests.

    -   Track support history for specific devices.

    -   Automate support processes.

-   **Development and Testing**:

    -   Debug issues on specific devices.

    -   Reproduce errors in specific configurations.

    -   Automate testing across different devices.

-   **System Integration**:

    -   Integrate into larger systems as a component.

    -   Use in access control systems.

    -   Integrate with monitoring and logging systems.

------------------------------------------------------------------------

# 7. Recommendations and Best Practices

-   **Use the Cached HWID**: Utilize the cached HWID provided by
    the generate_hwid() function to optimize performance in your
    applications.

-   **Handle Exceptions**: Implement appropriate error handling when
    using the module to ensure your application can handle any issues
    during HWID generation.

-   **Security Considerations**: When using HWIDs for licensing or
    security purposes, ensure that the HWID generation method meets your
    security requirements and consider potential spoofing risks.

-   **Integration with Other Tools**: The script can be effectively used
    in conjunction with other tools like the [Local Python Code
    Protector
    Script](https://github.com/alphabetanetcom/local-python-code-protector) for
    enhanced code protection.

------------------------------------------------------------------------

# Appendix A: Generating Hardware IDs

To restrict code execution to specific devices or for any application
requiring a unique device identifier, use the System Hardware ID
Generator Script as described in the usage examples.

**Steps:**

1.  **Run the script on the target device:**

```bash

python system_hardware_id_generator.py
```
2.  **The script will display the HWID:**

```javascript

Your Hardware ID (HWID) is: 123456789012345678
```
3.  **Use the HWID as needed in your application or licensing system.**

------------------------------------------------------------------------

# Appendix B: Contact Information

If you experience issues or have questions not covered in this
documentation, please contact the **Alpha Beta Network Research Team**.

-   **Website:** https://alphabetanet.com \| https://αβ.net

-   **Official Telegram Channel**: https://t.me/alphabetanetcom

Stay connected to receive updates, provide feedback, and get early
access to extended functionality.

------------------------------------------------------------------------

© 2024 αβ.net (alphabetanet.com) - **Alpha Beta Network**. All Rights
Reserved.

------------------------------------------------------------------------
