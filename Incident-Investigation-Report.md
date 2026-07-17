# SECURITY INCIDENT INVESTIGATION REPORT: Host Compromise

## 1. Incident Overview
* **Date & Time Detected:** [July 17, 2026 at 14:15:00]
* **Affected Host Name:** [FIN-LAPTOP-12]
* **Assigned Analyst:** [Fitz F.]
* **Initial Alert Trigger:** [High-severity EDR alert flagging anomalous process spawning and network scanning behavior.]

## 2. Evidence Gathering & Process Tree Analysis
* **Parent Process:** [Microsoft Word]
* **Child Process Spawned:** [cmd.exe]
* **Observed Host Anomalies:** [The CPU usage spiked to 100% and my network logs show that David's laptop is trying to connect to 50 other computers on the company network every second.]

## 3. Containment & Eradication Actions Taken
1. **Network Isolation:** Utilized the EDR management console to immediately isolate the host from the network. This severs all local network connections to stop lateral movement (the malware spreading to other machines) while keeping the host online for analyst forensic review.
2. **Process Termination:** Terminated the malicious PowerShell threads and killed the parent document processes to halt further execution of the download script.
3. **Volatile Memory Capture:** Initiated a remote RAM dump to capture current running processes and volatile encryption keys before conducting a full system remediation.

## 4. Root Cause Analysis (RCA) & Recommendations
* **Root Cause:** The user opened an untrusted macro-enabled document sent via an unverified vector, triggering a living-off-the-land (LotL) execution chain using native Windows administration tools.
* **Strategic Defensive Recommendation:** Implement an explicit Group Policy Object (GPO) across the enterprise domain to block Microsoft Office applications from spawning child shells (`cmd.exe`, `powershell.exe`). Additionally, enforce strict application control to prevent unsigned executables from executing out of user profile directories.
