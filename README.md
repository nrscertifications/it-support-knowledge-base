# IT Support & Help Desk Knowledge Base

## Overview

This repository contains standardized troubleshooting runbooks and incident-style documentation for common IT Support and Help Desk scenarios.

The purpose of this knowledge base is to document clear triage steps, likely causes, remediation actions, verification checks, and support handoff notes. The examples demonstrate practical troubleshooting judgment, clear escalation boundaries, and repeatable technical handoffs rather than command-only fixes.

The repository also includes step-by-step support guides that convert resolved incidents into reusable troubleshooting procedures for technicians.

---

## Documentation Standards

Each runbook follows a consistent support format:

* **Incident Summary:** Clear description of the reported issue and affected environment.
* **Triage & Symptoms:** Observable symptoms, user impact, and initial checks.
* **Root Cause Analysis:** Likely cause or confirmed fault where available.
* **Remediation Steps:** Safe, ordered troubleshooting actions.
* **Verification & Post-Incident Review:** How the fix was confirmed and what should be documented for future prevention.

Step-by-step guides expand selected incidents into reusable troubleshooting workflows with decision points, screenshots, verification steps, and escalation criteria.

The focus is on non-destructive troubleshooting, clear documentation, and realistic support escalation language.

---

## Knowledge Base Index

### Endpoint & OS Support

* [Windows Boot Priority & BIOS Configuration](runbooks/windows-boot-priority-issue.md)
* [Windows System Performance & Cleanup](runbooks/windows-slow-performance-cleanup.md)
* [Hyper-V Windows 11 Enterprise TPM / Host OS Compatibility](runbooks/hyper-v-windows-11-enterprise-tpm-host-os-compatibility.md)

### Networking & Connectivity

* [Internet & Wi-Fi Connectivity Troubleshooting](runbooks/internet-connectivity-troubleshooting.md)

### Mobile Device Support

* [Android Data Migration & Account Sync Resolution](runbooks/android-data-migration-and-contact-sync.md)

### Hardware, Printing & Endpoint Security

* [Anti-Malware Setup & Endpoint Protection](runbooks/anti-malware-endpoint-setup.md)
* [Hardware & Peripheral Lifecycle Recommendation](runbooks/hardware-peripheral-recommendation.md)
* [HP Smart Printing Cancellation Error](runbooks/hp-smart-printing-cancellation-error.md)
* [Keyboard Backspace Key Not Responding](runbooks/keyboard-backspace-key-not-responding.md)

---

## Step-by-Step Support Guides

### Printing & Peripheral Support

* [Troubleshooting Windows Printer Cancellation Errors](guides/windows-printer-cancellation-troubleshooting.md)
* [Troubleshooting a Single Keyboard Key Not Responding in Windows](guides/windows-keyboard-key-not-responding.md)

---

## Supported Environments & Tools

* **Operating Systems:** Windows 10/11, Windows Server fundamentals, Android OS, Ubuntu/Linux basics
* **Endpoint Support:** Laptops, desktops, BIOS/UEFI firmware, printers, keyboards, peripherals, mobile devices
* **Networking Concepts:** Wi-Fi/Ethernet troubleshooting, DNS/DHCP basics, gateway validation, network adapter checks
* **Security Concepts:** Anti-malware setup, endpoint protection, user awareness, safe remediation practices
* **Documentation:** Incident reports, troubleshooting runbooks, step-by-step support guides, RCA notes, Markdown, Git/GitHub

---

## Core Competencies Demonstrated

* Documented real-world style support scenarios using structured runbook formatting.
* Practiced symptom isolation before applying fixes or escalating.
* Used non-destructive triage steps to protect user data and system stability.
* Wrote remediation steps that can be followed by another support technician.
* Converted resolved incidents into reusable troubleshooting guides with clear decision points.
* Included verification steps so incidents are not closed without proof of resolution.
* Organized technical documentation in a GitHub repository for portfolio review.

---

## Repository Structure

```text
it-support-knowledge-base/
├── README.md
├── guides/
│   ├── windows-keyboard-key-not-responding.md
│   └── windows-printer-cancellation-troubleshooting.md
├── images/
│   ├── hp-smart-printing-cancellation/
│   │   ├── 01-hp-smart-print-dialog.png
│   │   ├── ...
│   │   └── 23-remove-hp-smart-printing-virtual-printer.png
│   └── keyboard-backspace-key/
│       ├── 01-backspace-key-no-response.png
│       ├── 02-on-screen-keyboard-backspace-test.png
│       └── 03-keyboard-checker-backspace-not-detected.png
└── runbooks/
    ├── android-data-migration-and-contact-sync.md
    ├── anti-malware-endpoint-setup.md
    ├── hardware-peripheral-recommendation.md
    ├── hp-smart-printing-cancellation-error.md
    ├── hyper-v-windows-11-enterprise-tpm-host-os-compatibility.md
    ├── internet-connectivity-troubleshooting.md
    ├── keyboard-backspace-key-not-responding.md
    ├── windows-boot-priority-issue.md
    └── windows-slow-performance-cleanup.md
```
