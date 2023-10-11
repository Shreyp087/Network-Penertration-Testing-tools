# Detailed Documentation on Using Nmap

## Introduction

Nmap (Network Mapper) is a versatile and powerful open-source network scanning and discovery tool that is widely used by security professionals, network administrators, and penetration testers. Nmap helps you discover hosts, services, and open ports on a network, making it an essential tool for network reconnaissance and security assessment.

This documentation will provide a detailed guide on how to use Nmap for network scanning and information gathering.

## Installation

### Linux (Debian/Ubuntu)
```bash
sudo apt-get install nmap
```

### Linux (Red Hat/CentOS)
```bash
sudo yum install nmap
```

### macOS (Homebrew)
```bash
brew install nmap
```

### Windows
1. Download the Nmap installer from [https://nmap.org/download.html](https://nmap.org/download.html).
2. Run the installer and follow the installation instructions.

## Basic Usage

### 1. Scanning a Single Host

To perform a basic scan of a single host, use the following command:

```bash
nmap <target>
```

Replace `<target>` with the IP address or hostname of the target system. For example:

```bash
nmap 192.168.1.1
```

### 2. Scanning Multiple Hosts

You can scan multiple hosts by specifying a range of IP addresses or a list of hosts:

```bash
nmap 192.168.1.1-10
```

Or specify a list of hosts in a text file:

```bash
nmap -iL targets.txt
```

### 3. Scanning Specific Ports

By default, Nmap scans the 1,000 most common ports. To scan specific ports, use the `-p` option:

```bash
nmap -p 80,443,8080 <target>
```

### 4. Detecting Operating System

Nmap can attempt to detect the operating system of the target host using the `-O` flag:

```bash
nmap -O <target>
```

### 5. Aggressive Scanning

For a more comprehensive scan, you can use the `-A` option to enable aggressive mode:

```bash
nmap -A <target>
```

Aggressive mode includes OS detection, version detection, script scanning, and traceroute.

### 6. Saving Results to a File

You can save the scan results to a file for later analysis:

```bash
nmap -oN scan_results.txt <target>
```

Replace `scan_results.txt` with your desired filename.

### 7. Verbose Output

To see more details about the scan, use the `-v` option:

```bash
nmap -v <target>
```

### 8. Intensive Scan

For a more comprehensive scan, including all 65,535 ports, use the `-p-` option:

```bash
nmap -p- <target>
```

## Advanced Usage

### Service and Version Detection

Use the `-sV` flag to perform service and version detection:

```bash
nmap -sV <target>
```

### Script Scanning

Nmap includes a variety of scripts that can be used to perform targeted scans and vulnerability assessments. Use the `--script` option to specify a script:

```bash
nmap --script <script-name> <target>
```

For example, to run a script that checks for common web vulnerabilities:

```bash
nmap --script http-enum.nse <target>
```

### Timing and Performance

Nmap allows you to adjust the timing and performance of scans. The `-T` option can be used to set the timing template:

```bash
nmap -T<0-5> <target>
```

- `-T0` (Paranoid): Very slow and stealthy
- `-T1` (Sneaky): Slow and low impact
- `-T2` (Polite): Default
- `-T3` (Normal): Default
- `-T4` (Aggressive): Faster and more conspicuous
- `-T5` (Insane): Very fast but likely to trigger IDS/IPS

### Firewall Evasion

Nmap has options for firewall evasion, such as the `-f` flag to fragment packets and the `--mtu` option to set the maximum transmission unit.

### Timing Controls

You can adjust scan timing using the `--max-rtt-timeout`, `--min-rtt-timeout`, `--initial-rtt-timeout`, and `--max-retries` options to fine-tune your scan.

### Using Nmap Scripting Engine (NSE)

The Nmap Scripting Engine (NSE) allows you to create and run custom scripts for advanced network tests. The scripts are located in the `/usr/share/nmap/scripts` directory. To run a script:

```bash
nmap --script <script-name> <target>
```

## Conclusion

Nmap is an essential tool for network scanning, reconnaissance, and security assessment. This documentation provides a basic overview of Nmap's capabilities, but there are many more options and features to explore. It's important to use Nmap responsibly and only on systems for which you have explicit permission to test. Always follow ethical hacking guidelines and respect privacy and data protection laws when conducting network penetration tests.
