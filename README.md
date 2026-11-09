# Wireshark SOC Labs — Week 1 Extra Project (Networkwalks)

Six browser based SOC analyst labs completed as part of the Networkwalks Cybersecurity internship, Week 1 Extra Module. Each lab provides a network capture and 10 investigative tasks, working as a SOC analyst to trace attacker activity, recover hidden data, and spot credential exposure using Wireshark.

## Project Overview

This module simulates real SOC analyst work: given a packet capture with no prior context, identify what happened on the network using packet level evidence alone. Each lab isolates a different investigative skill, reconnaissance detection, session reconstruction, credential exposure, brute force detection, and VoIP traffic analysis, built around realistic attack and exposure scenarios.

## Labs Completed

| Lab | Focus | Score |
|---|---|---|
| Lab 3 | Identify the Attacker's IP | 100/100 |
| Lab 4 | Follow TCP Stream 1 | 100/100 |
| Lab 5 | Follow TCP Stream, Part 2 | 100/100 |
| Lab 6 | HTTP Plain Text Credentials | 100/100 |
| Lab 7 | Catch the Brute Force Attacker | 100/100 |
| Lab 8 | Catch the Call Scammer (VoIP) | 100/100 |

## What Each Lab Covered

### Lab 3: Identify the Attacker's IP
Filtered a capture down to SYN packets only to isolate connection attempts, then identified the source IP running a port scan against a target, which ports were open versus closed based on the response pattern (SYN-ACK vs RST), and classified the activity as reconnaissance.

### Lab 4: Follow TCP Stream 1
Reconstructed a full TCP conversation using Wireshark's Follow Stream feature to read an application level chat session end to end, identifying who initiated the conversation, the relevant stream number, and sensitive information exchanged in plain text during the session.

### Lab 5: Follow TCP Stream, Part 2
Applied the same stream reconstruction technique to a more layered capture, locating a specific HTTP exchange inside a larger set of streams, extracting a hidden value embedded in the traffic, and identifying the HTTP status code and downloaded resource tied to that stream.

### Lab 6: HTTP Plain Text Credentials
Identified an HTTP POST request carrying login credentials in cleartext, traced it to the originating host and login page, and counted the number of login attempts made. The lab's final task was identifying the fix: moving authentication traffic to HTTPS so credentials are never exposed on the wire.

### Lab 7: Catch the Brute Force Attacker
Analyzed a capture showing repeated authentication attempts against a single service, correlating failed response codes to count the number of failed logins before isolating the single successful authentication and classifying the activity as a brute force attack.

### Lab 8: Catch the Call Scammer (VoIP)
Investigated a VoIP capture by identifying the call setup protocol and voice codec in use, tracing the caller's extension and identity, and reconstructing the call's audio to confirm fraudulent intent, demonstrating that sensitive data exposure isn't limited to web traffic, voice traffic carries the same risk when unencrypted.

## Key Findings Across the Module

- Plaintext protocols (HTTP, unencrypted VoIP signaling) expose credentials and sensitive data to anyone capturing traffic on the path, the fix in every case was encryption in transit (HTTPS, SRTP/TLS for VoIP).
- Reconnaissance (port scanning) and brute force attempts both leave a distinct, repeatable packet pattern, a burst of SYNs with no completed handshake for scanning, repeated authentication attempts with the same failure code for brute forcing, that stands out clearly once you know what to filter for.
- Wireshark's Follow TCP Stream feature is the fastest way to go from raw packets to a readable application level conversation, essential for incident reconstruction, not just protocol analysis.

## Tools Used

- [Wireshark](https://www.wireshark.org/) (browser based lab environment)
- Networkwalks SOC Lab platform

## Author

Tunde Oduola
[LinkedIn](https://www.linkedin.com/in/tunde-oduola-2855a5239)

## Project Information

- **Internship/Program:** Networkwalks, Cybersecurity and Ethical Hacking Class
- **Week:** 1 (Extra Module)
- **Project:** Wireshark SOC Labs (6 labs, 60 tasks total)
- **Organization:** Networkwalks