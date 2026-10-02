# Windows Endpoint Telemetry & Audit Optimization Lab

## 🎯 Objective
To engineer and validate a local endpoint security logging pipeline using Microsoft Sysmon inside a resource-constrained virtualization environment (8GB RAM host).

## 💻 Infrastructure Architecture
- **Host Machine:** 8GB RAM | 256GB SSD
- **Target Endpoint VM:** Windows 10 Enterprise (Allocated: 2.5GB RAM via VMware Workstation)
- **Log Collection Agent:** Microsoft Sysmon v15.21 utilizing specialized XML rule filters.

## 🛠️ Implementation Walkthrough
1. **Privilege Escalation:** Bypassed default shell limitations to initialize an elevated administrative workspace via an absolute keyboard shortcut matrix (`Ctrl+Shift+Enter`).
2. **Sensor Deployment:** Successfully initialized `Sysmon64.exe` utilizing a specialized logging template to isolate system modifications while conserving system memory.
3. **Telemetry Sanitization:** Purged historical log noise using `wevtutil cl` to establish a perfectly sterile baseline (0 active events) for targeted threat hunting.
4. **Adversary Simulation:** Executed an aggressive external SMB discovery probe from a Kali Linux VM utilizing Nmap targeting Port 445.
5. **Log Triage:** Analyzed event logs inside Windows Event Viewer to isolate **Event ID 1 (Process Create)**, successfully tracing how the inbound network probe forced the execution of `SearchProtocolHost.exe` to handle the traffic hooks.

## 📊 Technical Evidence (Live Capture)
<img width="500" height="100" alt="Annotation 2026-08-31 140225" src="Screenshot 1.png" />
<img width="600" height="300" alt="Annotation 2026-08-31 140225" src="Screenshot 2.png" />
<img width="600" height="300" alt="Annotation 2026-08-31 140225" src="screenshot 3.png" />
<img width="600" height="300" alt="Annotation 2026-08-31 140225" src="screenshot 4.png" />
<img width="600" height="300" alt="Annotation 2026-08-31 140225" src="https://github.com/user-attachments/assets/6f617bc6-8608-42e3-bda3-9770afecfa85" />
