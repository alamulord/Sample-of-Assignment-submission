TryHackMe Secure Lab — Open Port Reconnaissance Report
https://catbox.moe/
Activity: Network reconnaissance / open-port enumeration
Platform: TryHackMe
Environment: Authorized vulnerable-machine laboratory
Assessment Type: Controlled security testing
Purpose: Identify exposed network services and document the reconnaissance process
Status: Completed in an authorized lab environment

1. Executive Summary

This report documents a network reconnaissance exercise performed against a vulnerable machine provided within a TryHackMe controlled laboratory environment.

The objective of the activity was to identify open TCP ports and determine which network services were exposed by the target machine. The reconnaissance was performed using standard network-scanning techniques, primarily Nmap.

The activity demonstrates the following security-testing capabilities:

Identifying the target machine's IP address.
Verifying network connectivity to the target.
Performing TCP port discovery.
Identifying services associated with discovered ports.
Collecting scan output as evidence.
Documenting findings in a reproducible manner.
Assessing the potential security relevance of exposed services.

Evidence note: Replace every screenshots/... reference below with screenshots captured during your actual TryHackMe session.

2. Scope and Authorization

The reconnaissance was conducted exclusively against a machine intentionally provided for security testing within a TryHackMe laboratory.

Scope
Item	Description
Target	TryHackMe vulnerable laboratory machine
Target IP	43.23.1832.12
Tester	Fatima
Platform	TryHackMe
Activity	TCP port and service reconnaissance
Date	2026-08-12
Time	<11:15 UTC>
Authorization	Controlled TryHackMe lab environment

No scanning of systems outside the authorized laboratory scope was intended or performed.

3. Objectives

The primary objectives were:

Determine whether the target was reachable.
Identify open TCP ports.
Determine the services running on discovered ports.
Record the evidence produced by the reconnaissance process.
Evaluate whether exposed services could represent potential attack surfaces.
Produce a reproducible technical record of the activity.
4. Tools Used
Nmap

Nmap
 was used to perform network reconnaissance and identify open ports and services.

Example command:

nmap  fuo.edu.ng

For broader TCP port discovery:

nmap -p- fuo.edu.ng


For service/version detection:

nmap -sV <TARGET_IP>


A combined reconnaissance command can be used where appropriate:

nmap -sV -p- <TARGET_IP>


Only run these commands against systems that are explicitly within your authorized testing scope.

5. Laboratory Setup

The testing workstation was connected to the TryHackMe laboratory network, and the assigned vulnerable machine was started before reconnaissance began.

Environment
Tester Machine
      |
      |  Authorized TryHackMe Lab Network
      |
      v
+-------------------------+
| Vulnerable Target       |
| IP: <TARGET_IP>         |
+-------------------------+

Evidence — TryHackMe Target

Figure 1: TryHackMe laboratory target and assigned machine information.

6. Procedure
Step 1 — Identify the Target

The target machine was started through the TryHackMe laboratory interface.

The assigned IP address was recorded before beginning the scan.

Target IP: <TARGET_IP>

Evidence

Figure 2: Target IP address assigned by the TryHackMe laboratory.

Step 2 — Verify Connectivity

Connectivity to the target was verified before performing port enumeration.

Example:

ping -c 4 <TARGET_IP>


Expected evidence includes successful responses or another indication that the target was reachable.

Evidence

Figure 3: Connectivity verification against the target machine.

Step 3 — Perform Initial Port Scan

An initial Nmap scan was performed to identify commonly exposed TCP ports.

nmap <TARGET_IP>


The scan results were reviewed to identify ports reported as open.

Evidence

Figure 4: Initial Nmap scan showing discovered TCP ports.

Step 4 — Perform Full TCP Port Enumeration

To avoid relying only on Nmap's default port selection, a full TCP port scan was performed.

nmap -p- <TARGET_IP>


The -p- option instructs Nmap to scan TCP ports from 1 through 65535.

Evidence

Figure 5: Full TCP port enumeration results.

Step 5 — Identify Services and Versions

After identifying open ports, service/version detection was performed.

nmap -sV -p <OPEN_PORTS> <TARGET_IP>


For example:

nmap -sV -p 22,80,443 <TARGET_IP>


This step helps associate open ports with services and, where possible, their detected versions.

Evidence

Figure 6: Nmap service/version detection results.

7. Results

The discovered ports should be recorded below using the actual output from your scan.

Port	Protocol	State	Service	Version	Notes
<PORT>	TCP	Open	<SERVICE>	<VERSION>	<OBSERVATION>
<PORT>	TCP	Open	<SERVICE>	<VERSION>	<OBSERVATION>
<PORT>	TCP	Open	<SERVICE>	<VERSION>	<OBSERVATION>
Example Format

The following is an example format only, not evidence from the assessment.

Port	Protocol	State	Service	Version
22	TCP	Open	SSH	<detected version>
80	TCP	Open	HTTP	<detected version>
8. Key Findings
Finding 1 — Open TCP Ports Identified

The reconnaissance identified the following TCP ports as open:

<PORT>/<tcp> — <SERVICE>
<PORT>/<tcp> — <SERVICE>
<PORT>/<tcp> — <SERVICE>


These ports represent network-accessible services running on the target.

Finding 2 — Service Identification

Nmap service detection was used to determine the services associated with the discovered ports.

<PORT>  <SERVICE>  <VERSION>
<PORT>  <SERVICE>  <VERSION>

Finding 3 — Potential Attack Surface

Every externally accessible service represents a potential attack surface.

The presence of an open port does not, by itself, prove that the service is vulnerable. Further investigation would be required to determine whether the detected service contains configuration weaknesses, outdated software, authentication weaknesses, or known vulnerabilities.

9. Evidence Summary

The following evidence should be included with the final report:

Evidence	Description	File
Screenshot 1	TryHackMe target machine	screenshots/01-target-machine.png
Screenshot 2	Target IP address	screenshots/02-target-ip.png
Screenshot 3	Connectivity test	screenshots/03-connectivity-test.png
Screenshot 4	Initial Nmap scan	screenshots/04-initial-nmap-scan.png
Screenshot 5	Full TCP scan	screenshots/05-full-port-scan.png
Screenshot 6	Service/version detection	screenshots/06-service-detection.png
10. Raw Scan Evidence

For reproducibility, the raw Nmap output should be preserved alongside the screenshots.

Example:

$ nmap -sV -p- <TARGET_IP>

Starting Nmap ...
Nmap scan report for <TARGET_IP>

PORT      STATE    SERVICE    VERSION
<PORT>    open     <SERVICE>  <VERSION>
<PORT>    open     <SERVICE>  <VERSION>

Nmap done: 1 IP address ...


Replace the example output above with the exact output generated during your own scan.

A copy of the raw scan can also be saved with:

nmap -sV -p- <TARGET_IP> -oN nmap-results.txt


This creates a text file that can be submitted as additional evidence.

11. Security Relevance

Open ports provide information about the services exposed by a host.

During a security assessment, this information can be used to:

Establish the target's network attack surface.
Identify potentially interesting services.
Determine which services require further investigation.
Identify software versions for subsequent vulnerability research.
Detect unnecessarily exposed services.
Support security-hardening recommendations.

The reconnaissance stage should be followed by appropriate validation and vulnerability assessment within the authorized scope.

12. Limitations

The results documented in this report are limited to the reconnaissance performed during the specified laboratory session.

Important limitations include:

A port reported as open does not automatically indicate a vulnerability.
Service/version detection can occasionally produce inaccurate or incomplete results.
Firewall rules may affect scan results.
UDP services may not be identified by a TCP-only scan.
The scan represents the state of the target at the time of testing.
Only systems within the authorized TryHackMe laboratory environment were considered in scope.
13. Conclusion

The reconnaissance exercise successfully demonstrated the process of identifying network-accessible services on an authorized vulnerable machine.

The workflow consisted of:

Starting the assigned TryHackMe target.
Recording the target IP address.
Verifying connectivity.
Performing an initial Nmap scan.
Performing full TCP port enumeration.
Identifying services and versions.
Recording the results and preserving screenshots as evidence.

The resulting port and service information provides a foundation for subsequent security assessment activities within the authorized laboratory environment.

14. Evidence Integrity Checklist

Before submitting this report, verify that:

 The TryHackMe target screenshot is included.
 The target IP is visible in the evidence.
 The Nmap command is visible in at least one screenshot.
 The Nmap results are clearly readable.
 All discovered ports are recorded accurately.
 Service/version information matches the actual scan output.
 Screenshots have not been altered in a way that changes their meaning.
 Raw Nmap output is preserved where possible.
 The date and time of the activity are recorded.
 <TARGET_IP> and other placeholders have been replaced with actual information.
 Example results have been removed or clearly marked as examples.
 Only authorized laboratory activity is documented.
15. Suggested Repository Structure
tryhackme-recon/
├── README.md
├── report.md
├── nmap-results.txt
└── screenshots/
    ├── 01-target-machine.png
    ├── 02-target-ip.png
    ├── 03-connectivity-test.png
    ├── 04-initial-nmap-scan.png
    ├── 05-full-port-scan.png
    └── 06-service-detection.png


GitHub-compatible image syntax used in this report:

![Description of image](https://files.catbox.moe/xuti4x.png)


This is preferable to embedding screenshots as raw HTML when you want the Markdown to render cleanly in GitHub's editor and repository view.

16. Attestation

I confirm that the reconnaissance activity documented in this report was performed against a machine provided within an authorized TryHackMe laboratory environment.

Tester: <YOUR_NAME>
Date: <YYYY-MM-DD>
Lab/Room: <TRYHACKME_ROOM_NAME>
Target: <TARGET_IP>

Signature/Identifier: <OPTIONAL_IDENTIFIER>

End of Report
