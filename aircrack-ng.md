# Detailed Documentation on Using Aircrack-ng for Network Penetration Testing

## Introduction

Aircrack-ng is a versatile and popular suite of tools for assessing wireless network security. It includes tools for capturing packets, cracking WEP and WPA/WPA2 keys, and performing various tasks related to Wi-Fi network penetration testing. This documentation will guide you through using Aircrack-ng effectively for network penetration testing.

## Installation

Aircrack-ng is available for various platforms. To install Aircrack-ng, follow the instructions for your specific operating system:

- **Linux**: Most Linux distributions include Aircrack-ng in their repositories. You can install it using your package manager. For example, on Debian/Ubuntu, run:

  ```bash
  sudo apt-get install aircrack-ng
  ```

- **macOS**: You can install Aircrack-ng on macOS using Homebrew. Run the following command:

  ```bash
  brew install aircrack-ng
  ```

- **Windows**: Download the Windows version from the official Aircrack-ng website: [Aircrack-ng for Windows](https://www.aircrack-ng.org/downloads.html)

## Basic Usage

### 1. Capturing Packets

- To capture packets from a Wi-Fi network, you'll need a wireless network adapter that supports monitor mode.

- Put your wireless adapter into monitor mode with the following command:

  ```bash
  sudo airmon-ng start <interface>
  ```

  Replace `<interface>` with the name of your wireless interface (e.g., wlan0).

- Once your adapter is in monitor mode, use `airodump-ng` to scan for nearby Wi-Fi networks and capture packets:

  ```bash
  airodump-ng wlan0mon
  ```

  Replace `wlan0mon` with your monitor interface name.

### 2. Capturing a WPA Handshake

- To crack a WPA/WPA2 key, you need to capture a WPA handshake. When you see a target network with a handshake, press `Ctrl + C` to stop capturing.

### 3. Cracking WEP Keys

- Aircrack-ng can be used to crack WEP keys from captured packets. To do so, use the following command:

  ```bash
  aircrack-ng -b <BSSID> -w <wordlist> <capture-file>
  ```

  Replace `<BSSID>` with the BSSID of the target network, `<wordlist>` with the path to a wordlist file, and `<capture-file>` with the name of the capture file.

### 4. Cracking WPA/WPA2 Keys

- Aircrack-ng can be used to crack WPA/WPA2 keys once you have captured a WPA handshake. Use the following command:

  ```bash
  aircrack-ng -w <wordlist> -b <BSSID> <capture-file>
  ```

  Replace `<wordlist>` with the path to a wordlist file, `<BSSID>` with the BSSID of the target network, and `<capture-file>` with the name of the capture file.

## Advanced Usage

### 1. Deauthentication Attacks

- Aircrack-ng can be used to perform deauthentication attacks to force clients to disconnect from a Wi-Fi network. This can be useful for capturing WPA handshakes.

- To perform a deauthentication attack on a specific client, use the following command:

  ```bash
  aireplay-ng --deauth <number_of_deauth_packets> -a <BSSID> -c <client_MAC> wlan0mon
  ```

  Replace `<number_of_deauth_packets>` with the number of deauthentication packets to send, `<BSSID>` with the BSSID of the target network, `<client_MAC>` with the MAC address of the client, and `wlan0mon` with your monitor interface name.

### 2. Generating Wordlists

- Aircrack-ng does not include a wordlist generator, but you can create your own wordlists or use existing ones.

- Tools like `crunch` or `hashcat` can be used to generate custom wordlists.

### 3. Filtering Captured Packets

- Aircrack-ng can capture a large amount of unnecessary data. You can use `tcpdump` or Wireshark to filter and analyze the captured packets more effectively.

### 4. Using the Aircrack-ng Suite

- Aircrack-ng includes several tools besides `airodump-ng` and `aireplay-ng`. Explore tools like `airbase-ng`, `airdecap-ng`, and `aircrack-ng` to expand your capabilities in Wi-Fi penetration testing.

## Conclusion

Aircrack-ng is a powerful suite of tools for assessing the security of wireless networks. This documentation provides an overview of its capabilities, from capturing packets and performing deauthentication attacks to cracking WEP and WPA/WPA2 keys. Always use Aircrack-ng responsibly and ensure you have explicit authorization to conduct network penetration tests, as unauthorized testing is illegal and unethical.
