# Detailed Documentation on Using RouterSploit for Network Penetration Testing

RouterSploit is an open-source exploitation framework designed specifically for targeting embedded devices like routers. It allows penetration testers and security researchers to identify and exploit vulnerabilities in router and IoT device firmware. This documentation will guide you through using RouterSploit effectively for network penetration testing.

## Installation

RouterSploit is a Python-based tool, and it can be installed on various platforms. It's compatible with both Linux and macOS. Below are the installation instructions for these two operating systems:

### Linux (Debian/Ubuntu):

1. Install the required dependencies:

```bash
sudo apt-get update
sudo apt-get install python3-pip python3-dev autoconf libgmp-dev libmpc-dev libmpfr-dev libtool libssl-dev libffi-dev libpcap-dev
```

2. Install RouterSploit using pip:

```bash
pip3 install routersploit
```

### macOS:

1. Install Homebrew (if not already installed):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Install RouterSploit using pip:

```bash
pip3 install routersploit
```

## Basic Usage

RouterSploit is a versatile tool with a wide range of features. Here are some common use cases and commands to get started:

### 1. Start RouterSploit:

To start RouterSploit, open a terminal and run the following command:

```bash
rsf
```

This command launches the RouterSploit framework.

### 2. Scan for Vulnerabilities:

RouterSploit provides a wide range of modules for scanning and exploiting vulnerabilities in routers and embedded devices. To list available modules, use the following command within the RouterSploit console:

```bash
show scanners
```

This command displays a list of available scanning modules. You can select a module for scanning vulnerabilities.

### 3. Exploit a Vulnerability:

To exploit a discovered vulnerability, you need to load the specific module and set the required options. For example, if you have identified an HTTP service vulnerability, use the following commands:

```bash
use scanners/autopwn
set target <target_ip>
run
```

This set of commands loads the autopwn module, sets the target IP, and runs the exploit. RouterSploit will attempt to exploit the target device.

## Advanced Usage

RouterSploit offers advanced features and capabilities for in-depth network penetration testing:

### 1. Payloads:

You can create custom payloads using the `generate` command. For example, to generate a custom payload for a reverse shell, use the following command:

```bash
generate payload <payload_type>
```

### 2. Integration with Metasploit:

RouterSploit can be integrated with the Metasploit framework for additional exploitation capabilities. You can use the `msf` command within RouterSploit to access Metasploit modules and functionality.

### 3. Custom Modules:

You can create custom modules for RouterSploit by developing Python scripts. Custom modules allow you to target specific vulnerabilities or devices. Refer to the RouterSploit documentation for details on creating custom modules.

### 4. Report Generation:

RouterSploit can generate reports for penetration testing assessments. To create a report, you can use the `report` command. For example:

```bash
report -t <target> -p <path_to_report>
```

This command generates a report for the target and saves it to the specified path.

### 5. Auto-pwn:

RouterSploit includes an auto-pwn module that automates the exploitation of known vulnerabilities in a target device. To use this module, use the following commands:

```bash
use scanners/autopwn
set target <target_ip>
run
```

RouterSploit will attempt to exploit all known vulnerabilities in the target device.

## Conclusion

RouterSploit is a powerful and versatile tool for network penetration testing, specifically targeting embedded devices like routers. This documentation provides an overview of its capabilities, from basic usage to advanced features. Always use RouterSploit responsibly and ensure that you have explicit authorization to conduct network penetration tests, as unauthorized testing is illegal and unethical.
