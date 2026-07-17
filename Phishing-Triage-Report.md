# PHISHING TRIAGE REPORT: Case #2026-0717A

## 1. Executive Summary
* **Reported By:** Sarah (HR Representative)
* **Triage Finding:** Malicious (Credential Harvesting Phish)
* **Summary of Event:** [Sarah recieved a malicious email with the display email name and the email address not matching. There's a link that says "Verify Account" but has a suspicious url, Sarah clicked the link and begin entering her username but got suspicious and closed the browser before entering her password.]

## 2. Email Details & Headers
* **Sender Display Name:** [Microsoft Security Team]
* **Envelope Sender Address:** [no-reply@micros0ft-update-portal[.]com]
* **Subject Line:** [URGENT: Verify your account now to prevent suspension]
* **Sender Spoofing Assessment:** This is a clear lookalike/typosquatted domain. The attacker replaced the letter 'o' with a zero ('0') in the word Microsoft to deceive the recipient.

## 3. Indicators of Compromise (IoCs)
* **Suspicious Link Destination:** [hxxps://login.microsoft.com.attacker-domain[.]xyz/secure]

## 4. Remediation Steps Taken
1. **Account Auditing:** Because the Sarah clicked the link and entered her username, we initiated a forced sign-out of Sarah's active sessions and checked Azure/Okta identity logs for any successful, anomalous logins from unexpected locations.
2. **Email Internal Purge:** Searched the Secure Email Gateway (SEG) for all incoming messages containing the sender address or the malicious URL destination to locate and permanently delete matching emails from other employee inboxes.
3. **Network Perimeter Blocking:** Added the malicious destination URL and its hosting IP address to our corporate firewall and DNS blocklists to prevent any other internal network assets from communicating with the threat actor's site.
