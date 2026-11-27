# soc-home-lab
# SOC Home Lab

A virtual Security Operations Center (SOC) lab built to practise alert triage:
analysing security alerts and deciding whether they are true positives or false positives.

## Goal
Learn SOC analyst skills by building the environment myself, attacking it,
and investigating the alerts the SIEM produces.

## Architecture
```
Host: Windows laptop (16 GB RAM) running VirtualBox
 └── NAT Network "soclab" (10.0.2.0/24)
      ├── Ubuntu Server 26.04  → Wazuh SIEM (manager, indexer, dashboard)
      ├── Windows 11           → victim endpoint (Wazuh agent + Sysmon)
      └── Kali Linux 2026.2    → attacker
```

## Tools
| Tool | Purpose |
|---|---|
| VirtualBox | Virtualisation |
| Wazuh | SIEM / XDR: log collection, detection rules, alerts |
| Sysmon | Detailed Windows event logging |
| Kali Linux | Attack simulation |
| Atomic Red Team | Attack techniques mapped to MITRE ATT&CK |

## Progress
- [x] Lab network (VirtualBox NAT Network)
- [x] Kali attacker VM
- [x] Ubuntu server VM
- [ ] Wazuh installation
- [ ] Windows endpoint + Wazuh agent + Sysmon
- [ ] Attack simulations
- [ ] Alert triage reports
- [ ] Custom detection rules

## Repository structure
| Folder | Content |
|---|---|
| `01-lab-setup` | VirtualBox, network and VM setup |
| `02-wazuh-install` | Wazuh all-in-one installation |
| `03-windows-agent-sysmon` | Endpoint setup and log collection |
| `04-attack-simulations` | Attacks run, with MITRE ATT&CK IDs |
| `05-alert-triage` | One investigation report per alert |
| `06-detection-rules` | Custom Wazuh rules and tuning |
| `troubleshooting.md` | Problems I hit and how I fixed them |
