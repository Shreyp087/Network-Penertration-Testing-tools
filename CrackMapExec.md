# Detailed Documentation on Using CrackMapExec for Network Penetration Testing

CrackMapExec (CME) is a versatile post-exploitation tool and Swiss Army knife for pentesters and red teamers. It automates common pentesting tasks, from enumeration to exploitation, and is used to interact with Windows systems. This documentation will guide you through using CrackMapExec effectively for network penetration testing.

## Installation

CrackMapExec is available on GitHub and can be installed on various platforms. It's compatible with both Linux and macOS. Below are the installation instructions for these two operating systems:

### Linux:

1. Install the required dependencies:

```bash
sudo apt-get install python3-pip
sudo apt-get install libssl-dev
```

2. Install CrackMapExec using pip:

```bash
pip3 install crackmapexec
```

### macOS:

1. Install Homebrew (if not already installed):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Install CrackMapExec using Homebrew:

```bash
brew install crackmapexec
```

## Basic Usage

CrackMapExec (CME) is a versatile tool with a wide range of features. Here are some common use cases and commands to get started:

### 1. Enumerating Shares on a Target:

To list available shares on a target, use the following command:

```bash
crackmapexec smb <target>
```

Replace `<target>` with the IP address or hostname of the target system. This command will enumerate available shares.

### 2. Scanning for SMB Vulnerabilities:

CME allows you to scan for vulnerabilities in SMB (Server Message Block) services. Use the following command to perform an SMB vulnerability scan:

```bash
crackmapexec smb <target> -t 5 --port 139,445
```

The `-t` option specifies the number of threads, and `--port` specifies the ports to scan. In this example, it scans ports 139 and 445.

### 3. Exploiting Vulnerabilities:

CME can be used to exploit discovered vulnerabilities. For example, to perform a remote code execution (RCE) on a vulnerable target:

```bash
crackmapexec smb <target> -x "python /path/to/exploit.py"
```

This command runs the specified Python script on the target machine.

### 4. Enumerating Users:

To enumerate users on a target system, use the following command:

```bash
crackmapexec smb <target> --users
```

This command lists available users on the target.

## Advanced Usage

CrackMapExec offers advanced features and capabilities for more in-depth network penetration testing:

### 1. Credential Brute-Forcing:

CME supports credential brute-forcing. To perform a brute force attack on a target with a wordlist, use the following command:

```bash
crackmapexec smb <target> -u user -P /path/to/wordlist.txt
```

This command attempts to brute force the password for the specified user.

### 2. Pass-The-Hash (PTH) Attacks:

CME allows pass-the-hash attacks. Use the following command to perform a pass-the-hash attack:

```bash
crackmapexec smb <target> -u user -H hash
```

Replace `<target>` with the target IP address, `<user>` with the username, and `<hash>` with the password hash.

### 3. Shell Sessions:

You can spawn a shell session on a remote machine using CME. For example, to get a shell session on a target:

```bash
crackmapexec smb <target> -x "shell"
```

This will open an interactive shell on the target system.

### 4. Looting:

CME allows you to "loot" sensitive data from compromised systems. To loot data from a target, use the following command:

```bash
crackmapexec smb <target> -x "loot"
```

This command retrieves sensitive data from the target machine.

## Conclusion

CrackMapExec is a powerful and versatile tool for network penetration testing, automating a wide range of tasks from enumeration to exploitation. This documentation provides an overview of its capabilities, from basic usage to advanced features. Always use CrackMapExec responsibly and ensure that you have explicit authorization to conduct network penetration tests, as unauthorized testing is illegal and unethical.
