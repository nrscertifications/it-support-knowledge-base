# Incident Report: Internet & Wi-Fi Connectivity Triage

## Incident Summary

* Request Type: Network Connectivity / End-User Support
* Environment: Windows endpoint, Wi-Fi router/modem, SOHO network
* Reported Issue: User reported intermittent or failed internet access affecting normal device use and online services.

## Triage & Symptoms

* Confirmed whether the issue affected one device, multiple devices, or the entire local network.
* Checked Wi-Fi connection status, signal strength, and whether the endpoint was connected to the correct network.
* Verified basic network configuration, including IP address assignment, default gateway, and DNS behavior.
* Reviewed router/modem status indicators and confirmed whether the internet service was active.
* Tested connectivity using browser access, local gateway reachability, and alternate devices where available.

## Root Cause Analysis

The connectivity issue was isolated to the local network path rather than the user application itself. Possible causes included unstable Wi-Fi association, stale DHCP lease, DNS resolution failure, router/modem instability, incorrect network selection, or ISP-side disruption. The troubleshooting workflow focused on separating endpoint-level issues from router/modem or provider-side issues.

## Remediation Steps

1. Confirmed the scope of impact by testing connectivity on the affected device and another available device.
2. Verified the endpoint was connected to the correct Wi-Fi network.
3. Checked network adapter status and refreshed the Wi-Fi connection.
4. Reviewed IP configuration to confirm valid DHCP assignment.
5. Restarted the endpoint network adapter where appropriate.
6. Power-cycled the router/modem after confirming no active critical use.
7. Tested connectivity to the local gateway and external websites.
8. Reviewed DNS behavior and tested alternate browser/application access.
9. Documented whether the issue was endpoint-specific, router/modem-related, or likely ISP-related.
10. Escalated or advised ISP follow-up when local troubleshooting did not restore stable service.

## Verification & Post-Incident Review

* Verification: Internet access was restored or the fault was isolated to the appropriate layer for escalation.
* User Confirmation: User confirmed whether web access and required online services were functioning again.
* Technical Note: Connectivity issues should be isolated by scope first. Determining whether the fault affects one device, multiple devices, or the entire network prevents unnecessary endpoint changes and improves escalation quality.
