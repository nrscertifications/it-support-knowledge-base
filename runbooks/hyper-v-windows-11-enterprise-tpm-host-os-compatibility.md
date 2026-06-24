# Incident Report: Hyper-V Windows 11 Enterprise TPM & Host OS Compatibility

## Incident Summary

* **Request Type:** Virtualization / Windows Deployment Support
* **Environment:** Windows 11 host device, Hyper-V, Windows 11 Enterprise VM, Generation 2 virtual machine, Secure Boot, virtual TPM
* **Reported Issue:** Windows 11 Enterprise VM failed to install or initialize correctly in Hyper-V. The installer reported a TPM requirement even though virtual TPM was enabled in the VM settings and TPM was enabled in the physical system BIOS.

## Triage & Symptoms

* Windows 11 Enterprise installation presented a TPM-related requirement during setup.
* Hyper-V VM failed to initialize correctly during startup.
* VM was configured as a Generation 2 virtual machine.
* Secure Boot was enabled in the VM security settings.
* Trusted Platform Module was enabled in the VM security settings.
* Windows 11 Enterprise ISO was attached to the VM.
* VM firmware boot order was reviewed to confirm the ISO/DVD drive was available during startup.
* Physical BIOS showed TPM installed and enabled.
* Physical BIOS showed UEFI and Secure Boot enabled.
* VM memory and processor allocation were reviewed.
* Issue persisted after confirming both physical BIOS security settings and VM-level security settings.
* Host operating system edition was reviewed as part of the compatibility check.

## Root Cause Analysis

The issue was caused by an unsupported host operating system edition for the intended Hyper-V virtualization workflow.

The physical system BIOS had TPM, UEFI, and Secure Boot enabled, and the virtual machine was correctly configured with Generation 2, Secure Boot, and virtual TPM. However, the host operating system was running Windows 11 Home, which did not provide the required Hyper-V support for this Windows 11 Enterprise virtual machine deployment.

The root cause was not the Windows 11 Enterprise ISO, physical TPM configuration, or VM security configuration. The issue was isolated to the host operating system edition.

## Remediation Steps

* **BIOS Validation:** Reviewed the physical system BIOS to confirm TPM was installed and enabled.
* **Secure Boot Check:** Confirmed UEFI and Secure Boot were enabled at the physical system level.
* **VM Generation Review:** Verified that the virtual machine was created as a Generation 2 VM.
* **VM Security Review:** Confirmed Secure Boot and Trusted Platform Module were enabled in Hyper-V VM settings.
* **Boot Order Review:** Checked VM firmware settings to confirm the Windows 11 Enterprise ISO/DVD drive was available during startup.
* **Resource Review:** Confirmed the VM had sufficient memory and processor allocation for Windows 11 Enterprise deployment.
* **Host vs Guest Isolation:** Separated physical BIOS configuration from VM-level configuration to avoid unnecessary firmware changes.
* **Host OS Edition Check:** Identified that the host system was running Windows 11 Home.
* **Compatibility Correction:** Upgraded the host operating system from Windows 11 Home to Windows 11 Pro.
* **Hyper-V Retest:** Restarted the system, reopened Hyper-V, and launched the Windows 11 Enterprise VM again.
* **Deployment Validation:** Confirmed the VM was able to start and proceed with Windows 11 Enterprise installation.

## Verification & Post-Incident Review

* **Verification:** Windows 11 Enterprise VM successfully started in Hyper-V after the host operating system was upgraded to Windows 11 Pro.
* **User Confirmation:** Windows 11 Enterprise deployment proceeded after the compatibility issue was resolved.
* **Technical Note:** When troubleshooting Windows 11 VM installation or TPM errors, technicians should separate physical hardware requirements from virtual machine requirements. TPM enabled in the physical BIOS does not automatically confirm that the host operating system and Hyper-V configuration fully support the deployment. Always validate host OS edition, VM generation, Secure Boot settings, virtual TPM settings, ISO attachment, boot order, and resource allocation before assuming hardware or installation media failure.

