# SecTUI - Linux Security & Network Auditor

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3](https://img.shields.io/badge/python-3-blue.svg)](https://www.python.org/)

**SecTUI** (Security TUI) is a zero-dependency, interactive terminal dashboard designed for quick and efficient Linux server security auditing. 

Built entirely with standard Python libraries (`curses`), it instantly consolidates critical information regarding your firewall, exposed ports, active network processes, and disk usage. It is the perfect standalone tool for initial server assessments and quick-wins in DevSecOps.

## ✨ Features

- **Multi-Firewall Analysis**: Checks status, default policies, and rule counts for `UFW`, `iptables` (v4/v6), and `nftables`.
- **Network Mapping**: Identifies listening ports and active network connections (using `ss`, `netstat`, and `lsof`).
- **Anomaly Detection**: Custom risk-scoring algorithm that flags suspicious processes (e.g., exposed on `0.0.0.0`, running as `root`, or atypical python scripts).
- **System Hardening**: Automatically suggests disabling commonly unnecessary or vulnerable services on production servers (e.g., CUPS, Avahi, Bluetooth, WSDD).
- **Storage Monitoring**: Tracks filesystem usage and lists block devices (`df`, `lsblk`, `fdisk`).

## 📋 Prerequisites

This script uses only the Python 3 standard library. However, it relies on standard Linux system binaries to gather data:
- `ss` or `netstat` (port analysis)
- `lsof` (network process analysis)
- `ufw`, `iptables`, `nft` (firewall analysis)
- `df`, `lsblk`, `fdisk` (disk and partition analysis)
- `systemctl` (service state analysis)

> **Note:** For optimal functionality and complete data collection, running the script with `root` privileges (via `sudo`) is highly recommended.

## 🚀 Installation & Usage

Clone the repository and make the script executable. No `pip install` or external dependencies are required.

```bash
git clone https://github.com/your-username/SecTUI.git
cd SecTUI
chmod +x sectui
```

Run the auditor directly as a native command:

```bash
sudo ./sectui
```

## ⌨️ Navigation

The TUI is designed to be entirely keyboard-driven for a seamless terminal experience.

| Key | Action |
| --- | --- |
| `Tab` or `t` | Switch to the next tab |
| `↑` / `↓` | Scroll up / down within the current tab |
| `r` | Refresh data in real-time |
| `q` | Quit the application |

## 🛡️ Criticality Scoring System

SecTUI calculates an overall criticality score for your system to help prioritize corrective actions. The severity level (GOOD, MEDIUM, CRITICAL) increases based on several risk factors, including:

- **Firewall Status**: Inactive firewall or missing default `deny` policies.
- **Exposure**: High number of ports exposed publicly (`0.0.0.0` or `::`).
- **High-Risk Processes**: Network processes triggering multiple security flags.
- **Disk Space**: Filesystems exceeding 80% or 90% capacity.

*Disclaimer: This scoring system is heuristic and designed for quick reads. It does not replace comprehensive compliance audits, SIEMs, or EDR solutions.*

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! 
Feel free to check the [issues page](https://github.com/your-username/SecTUI/issues).

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

Distributed under the MIT License. See `LICENSE` for more information.
