## 1. System Configuration & Management Utilities

### System Configuration (`msconfig`)
Used for advanced troubleshooting, with its primary purpose being the diagnosis of startup issues and boot configurations.

### System Information (`msinfo32`)
Gathers detailed information about the machine and displays a comprehensive view of hardware, system components, and the software environment to assist in system diagnostics.

### Computer Management (`compmgmt`)
The **Computer Management** utility is divided into three primary sections: **System Tools**, **Storage**, and **Services and Applications**.

#### System Tools
* **Task Scheduler:** Allows creating and managing automated tasks that run at specified times or triggers (e.g., at log in, log off, or on a recurring schedule like every 5 minutes).
  * *Security / OffSec note:* Commonly abused for **persistence** or **privilege escalation** if a scheduled task runs a modifiable script/binary with elevated privileges (`SYSTEM`).
* **Performance Monitor (`perfmon`):** Used to view system performance metrics either in real-time or from log files for local and remote troubleshooting.
* **Device Manager:** Allows viewing and configuring attached hardware components (e.g., enabling/disabling devices).

#### Storage
* **Disk Management:** Enables advanced storage operations such as:
  * Setting up a new drive
  * Extending or shrinking partitions
  * Assigning or changing drive letters (e.g., `E:`)
* **Windows Server Backup:** Available on Windows Server environments for backup management (typically not present in standard Windows 10/11 consumer editions).

---

## 2. User Account Control (UAC)

**UAC (User Account Control)** is a Windows security mechanism that prevents unauthorized or critical system changes without explicit user approval. Even when logged in with an Administrator account, applications run with standard privileges by default until the user approves elevation via a UAC prompt.

* **Purpose:** Blocks malware or background scripts from silently modifying system files, registry keys, or global settings.
* **Security / OffSec note:** In Windows privilege escalation, attackers often look for **UAC Bypass** techniques to elevate an admin session from *medium* to *high integrity* without triggering a visible prompt.

---

## 3. Command Prompt (`cmd.exe`) Essentials

Although originally predating the GUI, the Command Prompt remains an essential daily tool for system administration and security testing.

| Command | Description |
| :--- | :--- |
| `hostname` | Outputs the machine's computer name. |
| `whoami` | Displays the currently logged-in user (e.g., `MACHINE-NAME\user`). |
| `ipconfig` | Displays local IP addresses, subnet masks, and default gateways. |
| `curl ifconfig.me` | Retrieves the machine's public IP address. |
| `netstat` | Displays protocol statistics and active TCP/IP network connections. |
| `<command> /?` | Retrieves the built-in help manual for a specific command (e.g., `ipconfig /?`). |

---

## 4. Windows Defender & Endpoint Protection

Under **Virus & threat protection settings → Manage settings**, Windows provides several core defensive controls:

* **Real-time protection:** Locates and stops malware from installing or executing on the device.
* **Cloud-delivered protection:** Enhances detection speed and accuracy using Microsoft's cloud threat intelligence.
* **Automatic sample submission:** Sends suspicious sample files to Microsoft to improve threat analysis.
* **Controlled folder access:** Protects specified files, folders, and memory areas from unauthorized modifications by untrusted apps (effective against ransomware).
* **Exclusions:** Allows excluding specific files, folders, or processes from antivirus scanning to avoid false positives.
  * *Security / OffSec note:* Misconfigured or overly broad exclusions are prime targets for dropping and executing payloads undetected.
* **Notifications:** Alerts the user regarding critical device health and security events.

---

## 5. Windows Firewall Profiles

A **firewall** monitors and filters incoming (inbound) and outgoing (outbound) network traffic based on security rules. Windows Firewall uses three distinct network profiles:

* **Domain:** Applies automatically when the host system can authenticate to a Domain Controller (Active Directory environment).
* **Private:** User-assigned profile intended for trusted private or home networks.
* **Public:** The default profile for untrusted networks (e.g., coffee shops, airports, public Wi-Fi hotspots) with stricter filtering rules.