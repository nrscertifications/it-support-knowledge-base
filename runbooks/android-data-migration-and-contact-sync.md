# Incident Report: Android Data Migration & Contact Synchronization

## Incident Summary

- **Request Type:** Mobile Device Support & Management / Data Migration
- **Environment:** Samsung Android (New Provisioning)
- **Reported Issue:** Post-migration, the end-user reported that unknown contacts belonging to another individual were populating in their device's native Contacts application.

## Triage & Symptoms

* User required data and SIM transfer from a legacy Android device to a newly provisioned Samsung Android device.
* Initial data transfer successfully completed, but contact lists merged with unrelated data.
* Verified the new device was utilizing the correct primary user account, but secondary sync sources were active.

## Root Cause Analysis

The legacy device had previously been utilized by another user. During the data migration process via Samsung Smart Switch, the previous user's Google/Samsung account remained associated with the device profile. This caused the new device to actively synchronize the previous user's cloud-hosted contacts into the local directory.

## Remediation Steps

1. **Initial Provisioning:** Connected both devices to a secure Wi-Fi network and utilized Samsung Smart Switch to migrate target user data.
2. **Hardware Transfer:** Successfully migrated the active SIM card to establish cellular connectivity.
3. **Account Audit:** Upon receiving the merged-contacts report, accessed **Settings > Accounts and backup > Manage accounts**.
4. **Account Removal:** Identified the previous user's Google/Samsung account still bound to the device profile.
5. **Resolution:** Removed the previous user's account from the device management settings, halting the sync.
6. **Data Cleanup:** Confirmed the removal automatically purged the cached local contacts associated with that account.

## Verification & Post-Incident Review

* **Verification:** Opened the Contacts application and confirmed only the current end-user's data was visible.
* **SOP Update / Preventative Action:** Prior to executing device-to-device migrations for repurposed hardware, technicians must manually audit and remove all previous user cloud accounts from the source device to prevent cross-contamination of synchronized cloud data.

