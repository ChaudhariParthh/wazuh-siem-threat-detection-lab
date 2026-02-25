# Wazuh Installation using VirtualBox (OVA Method)

## Overview

This guide explains the installation and initial setup of the **Wazuh SIEM Server** using the official **Wazuh OVA file** in **Oracle VirtualBox**. This method provides a quick and efficient way to deploy a fully configured Wazuh server for security monitoring and threat detection labs.

This setup is part of the **Wazuh SIEM Threat Detection Lab**.

---

## Lab Environment

| Component         | Value                                    |
| ----------------- | ---------------------------------------- |
| Hypervisor        | Oracle VirtualBox                        |
| Wazuh Server      | Wazuh OVA                                |
| Host OS           | Windows 10 
| OS Version        | 64 bit
| Network Adapter 1 | Host-Only Adapter                        |
| Network Adapter 2 | NAT Adapter                              |
| RAM               | Configured based on host system capacity |
| CPU               | Configured based on host system capacity |

---

## Step 1: Download Requirements

### Download VirtualBox

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Download and install according to your host operating system.

---

### Download Wazuh OVA

[https://documentation.wazuh.com/current/deployment-options/virtual-machine/virtual-machine.html](https://documentation.wazuh.com/current/deployment-options/virtual-machine/virtual-machine.html)

---

## Step 2: Import Wazuh OVA into VirtualBox

1. Open VirtualBox

2. Click: File → Import Appliance

3. Click: Choose

4. Select the downloaded: Wazuh OVA file

5. Click: Next

6. Click: Finish

Wazuh virtual machine will be imported.

---

## Step 3: Configure System Resources

Before starting the VM, configure hardware based on your laptop specifications.

Right Click Wazuh VM → Settings

---

### Configure RAM

Go to: System → Motherboard

Set Base Memory:

Recommended:

| Host RAM | Set Wazuh RAM |
| -------- | ------------- |
| 8 GB     | 4 GB          |
| 16 GB    | 8 GB          |
| 32 GB    | 12-16 GB      |

Do not allocate all memory to VM. Leave RAM for host OS.

---

### Configure CPU

Go to:

System → Processor

Recommended:

| Host CPU Cores | Set VM CPU |
| -------------- | ---------- |
| 4 cores        | 2 cores    |
| 8 cores        | 4 cores    |
| 12+ cores      | 6 cores    |

Enable:

PAE/NX (optional but recommended)

---

## Step 4: Configure Network

Go to:

Settings → Network

---

### Adapter 1: Host-Only Adapter

Purpose:

Communication between Host and Wazuh Server

Configuration:

Enable Network Adapter ✓

Attached to:

Host-Only Adapter

Name:

VirtualBox Host-Only Ethernet Adapter

---

### Adapter 2: NAT Adapter

Purpose:

Internet access for Wazuh server

Configuration:

Enable Network Adapter ✓

Attached to:

NAT

---

## Why Two Network Adapters?

| Adapter   | Purpose                          |
| --------- | -------------------------------- |
| Host-Only | Access Wazuh Dashboard from host |
| NAT       | Internet access for updates      |

---

## Step 5: Start Wazuh Server

Click:

Start

Wait for boot process to complete.

---

## Step 6: Login to Wazuh Server

Default credentials:

Username:

wazuh-user

Password:

wazuh

(Note: Change password after first login for security)

---

## Step 7: Check Wazuh Server IP Address

Run command:

```
ip a
```

Look for:

Host-Only Adapter IP

Example:

```
192.168.56.101
```

---

## Step 8: Access Wazuh Web Dashboard

Open browser on Host Machine

Visit:

```
https://<WAZUH-IP>
```

Example:

```
https://192.168.56.101
```

---

## Step 9: Login to Dashboard

Default credentials:

Username:

admin

Password:

admin

After login, Wazuh Dashboard will open.

---

## Step 10: Verify Wazuh Services

Run on server:

```
sudo systemctl status wazuh-manager
```

```
sudo systemctl status wazuh-dashboard
```

```
sudo systemctl status wazuh-indexer
```

All services should be:

active (running)

---

## Architecture Overview

Host Machine
│
├── VirtualBox
│
└── Wazuh Server VM
│
├── Wazuh Manager
├── Wazuh Indexer
└── Wazuh Dashboard

---

## Screenshots

Dashboard

VirtualBox Settings
<img width="1473" height="842" alt="image" src="https://github.com/user-attachments/assets/582f1e97-41ef-44d7-b03e-c7ad2afab3df" />

---

## Common Issues and Fixes

---

### Cannot access dashboard

Check:

```
ip a
```

Verify correct IP Check firewall

---

### VM slow performance

Increase: RAM

CPU

---

### No Internet inside VM

Check:

NAT Adapter enabled

---
## Next Steps

Install agents:

* Windows Agent
* Linux Agent

Configure:

* Log monitoring
* Configuration assessment
* Threat detection rules

---

## Author

Parth Chaudhari

Cybersecurity Enthusiast


