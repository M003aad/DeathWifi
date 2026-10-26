# Wi-Fi Deauth & Security Assessment Tool

A Python-based utility for scanning local Wi-Fi networks and performing deauthentication security audits. This script utilizes Linux network management tools (`nmcli`) and the `aircrack-ng` suite (`airmon-ng`, `airodump-ng`, `aireplay-ng`) to identify Wi-Fi networks and test target response to deauth attacks.

> **Disclaimer**: This tool is developed strictly for **educational purposes and authorized security penetration testing only**. Executing deauthentication attacks on networks without explicit permission from the network owner is illegal. The author(s) assume no liability and are not responsible for any misuse or damage caused by this program.

---

## Features

- Scans available Wi-Fi access points and displays relevant parameters (SSID, BSSID/MAC, Signal Strength, Security/Encryption Type, Channel, Frequency, Bitrate).
- Formatted tabular output for easy target selection.
- Automated target selection using network indices.
- Automatic monitor mode management via `airmon-ng`.
- Automated targeted deauthentication execution.

---

## Prerequisites & Dependencies

### System Requirements
- **Operating System**: Linux (Tested on Debian/Ubuntu/Kali Linux). *Not compatible with Windows.*
- **Root Privileges**: High-level permissions (`sudo`) are required to manage wireless interface state and execute raw packet injection commands.
- **Hardware**: A Wi-Fi network card that supports **Monitor Mode** and **Packet Injection**.

### System Utilities
Ensure the following tools are installed on your Linux system:
```bash
sudo apt update
sudo apt install network-manager aircrack-ng net-tools
```

### Python Dependencies
The script relies on Python 3 and the following external libraries:
- `pandas`
- `tabulate`
- `pygame`

Install them via `pip`:
```bash
pip install -r requirements.txt
```

---

## Usage

1. **Clone or Download the Repository:**
   ```bash
   git clone https://github.com/M003aad/Deathwifi.git
   cd Deathwifi
   ```

2. **Execute the Script with Root Privileges:**
   ```bash
   sudo python3 script.py
   ```

3. **Follow On-Screen Prompts:**
   - The script will clear the terminal and scan for available Wi-Fi networks using `nmcli`.
   - A formatted table will show all detected access points.
   - Enter the comma-separated sequence numbers (`N°`) corresponding to the networks you want to target (e.g., `1, 3`).
   - The script will enable monitor mode on `wlan0`, initiate `airodump-ng` targeting the chosen BSSID and channel, and execute `aireplay-ng` deauthentication packets.
   - Press `Ctrl + C` at any point to stop the attack and reset the network interface.

---

## Credits & Acknowledgments

- **Original Concept & Base Code**: Special thanks to **David** for the initial codebase and conceptual design upon which this project is built and modified.
- **Aircrack-ng Suite**: Powered by the open-source [Aircrack-ng](https://www.aircrack-ng.org/) security toolset.

---

## License

This project is licensed under the **MIT License**.