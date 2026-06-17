# IT Support & Help Desk Knowledge Base

## Overview

This repository contains a collection of standardized troubleshooting runbooks, incident reports, and technical documentation based on real-world end-user support scenarios.

The objective of this Knowledge Base (KB) is to establish structured problem-solving workflows, demonstrating methodical triage, root-cause analysis, and clear technical handoff documentation.

## Documentation Standards

All case studies within this repository adhere to standard IT ticketing and KB formats, emphasizing:

* **Symptom Isolation:** Avoiding assumptions by gathering factual system and user data.
* **Non-Destructive Triage:** Applying safe, step-by-step troubleshooting before escalating or altering core system configurations.
* **Root Cause Analysis (RCA):** Identifying the underlying fault rather than just addressing the symptoms.
* **Resolution & Verification:** Documenting the applied fix and the steps taken to validate service restoration.

## Knowledge Base Index

### Endpoint & OS Support

* [Windows Boot Priority & BIOS Configuration](case-studies/windows-boot-priority-issue.md)
* [Windows System Performance & Cleanup](case-studies/windows-slow-performance-cleanup.md)

### Networking & Connectivity

* [Internet & Wi-Fi Connectivity Triage](case-studies/internet-connectivity-troubleshooting.md)

### Mobile Device Support & Management

* [Android Data Migration & Account Sync Resolution](case-studies/android-data-migration-and-contact-sync.md)

### Hardware & Security

* [Anti-Malware Setup & Endpoint Protection](case-studies/anti-malware-endpoint-setup.md)
* [Hardware & Peripheral Lifecycle](case-studies/hardware-peripheral-recommendation.md)

## Supported Environments & Tools

* **Operating Systems:** Windows 10/11, Windows OS / BIOS Firmware, Android OS.
* **Hardware:** Endpoint laptops/desktops, BIOS/UEFI firmware, mobile devices and peripherals.
* **Core Concepts:** Boot sequencing, cloud account synchronization, endpoint troubleshooting, mobile device support and management.

## Repository Structure
This repository is organized to separate active case studies from templates and configuration guidelines:

```text
it-support-knowledge-base/
├── README.md
├── case-studies/
│   ├── windows-boot-priority-issue.md
│   ├── windows-slow-performance-cleanup.md
│   ├── internet-connectivity-troubleshooting.md
│   ├── android-data-migration-and-contact-sync.md
│   ├── anti-malware-endpoint-setup.md
│   └── hardware-peripheral-recommendation.md
└── templates/
    └── troubleshooting-note-template.md
