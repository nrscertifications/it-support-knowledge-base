# Incident Report: HP Smart Printing Cancellation Error

## Incident Summary

* **Request Type:** Printer / Peripheral Support
* **Environment:** Windows 11 endpoint, HP LaserJet M110w, HP Smart Printing virtual printer, HP Print Support Application
* **Reported Issue:** Print jobs submitted through HP Smart Printing were repeatedly canceled and did not print. The physical printer was visible to Windows and HP Smart, but the HP Print Support Application returned a "Print canceled" notification.

## Triage & Symptoms

* Reproduced the issue by submitting the affected PDF through **HP Smart Printing**.
* HP Smart initially reported the HP LaserJet M110w as **Out of paper**, even though paper was present in the input tray.
* Verified the physical paper tray and re-seated the paper. HP Smart subsequently reported the printer as **Ready**.
* Retested the same print job after the printer returned to Ready status. The HP Print Support Application still returned **Print canceled**.
* Power-cycled the printer by turning it off, disconnecting power for approximately 30 seconds, reconnecting power, and waiting for the printer and wireless connection to stabilize. The issue persisted.
* Printed a Windows Printer Test Page successfully from the physical HP LaserJet printer queue.
* Printed the original PDF successfully by selecting the direct Windows queue, **HP LaserJet M109-M112 [NPI1AB250] / HP LaserJet M110w**.
* Repeated the same PDF test through **HP Smart Printing - Virtual Printer for PSA**. The print job was canceled again.
* This A/B comparison isolated the failure to the HP Smart Printing / HP Print Support Application path rather than the physical printer, document, or native Windows printer queue.

![HP Smart Print Support Application reporting a canceled print job](../images/hp-smart-printing-cancellation/16-hp-smart-print-cancelled-reproduced.png)

## Root Cause Analysis

The issue was isolated to the **HP Smart Printing virtual printer/queue**.

The physical HP LaserJet M110w was able to print a Windows Test Page and the original PDF through its direct Windows printer queue. The same document repeatedly failed only when routed through HP Smart Printing. Repairing and resetting the HP Print Support Application did not resolve the failure. Removing the HP Smart Printing virtual printer and allowing HP Smart to recreate it restored normal printing.

Based on the observed behavior and successful remediation, the likely root cause was a **stale or corrupted HP Smart Printing virtual printer/queue configuration**. The physical printer hardware, paper feed, original PDF, and direct Windows printer path were not the root cause.

## Remediation Steps

1. **Issue Reproduction:** Submitted the affected PDF through HP Smart Printing and confirmed the HP Print Support Application returned a canceled-print notification.
2. **Paper & Device Status Check:** Verified paper was physically loaded, re-seated the paper, and confirmed HP Smart changed from **Out of paper** to **Ready**.
3. **Power Cycle:** Powered off the printer, disconnected power for approximately 30 seconds, reconnected power, powered the printer back on, and waited for connectivity to stabilize. Retesting still produced the cancellation error.
4. **Windows Test Page Validation:** Opened the HP LaserJet printer settings in Windows and printed a test page successfully, confirming the printer could receive and complete a Windows print job.
5. **Direct Document Validation:** Reopened the original PDF and printed it directly to **HP LaserJet M109-M112 [NPI1AB250] / HP LaserJet M110w**. The page printed successfully.
6. **A/B Print Path Isolation:** Printed the same PDF through **HP Smart Printing - Virtual Printer for PSA**. The job was canceled again, isolating the failure to the HP Smart virtual-print path.
7. **Application Repair:** Opened **Settings > Apps > Installed apps > HP Print Support Application > Advanced options** and ran **Repair**. Retesting did not resolve the issue.
8. **Application Reset:** Reset the HP Print Support Application from Advanced options, reopened the HP software, and retested. The print job was still canceled.
9. **Virtual Printer Recreation:** Opened **Settings > Bluetooth & devices > Printers & scanners > HP Smart Printing**, removed only the HP Smart Printing virtual printer, and left the working physical HP LaserJet queue intact.
10. **HP Smart Reinitialization:** Closed and reopened HP Smart so the HP Smart Printing virtual printer could be recreated.
11. **Final Retest:** Reopened the same PDF, selected the recreated HP Smart Printing destination, and submitted the job again. The document printed successfully.

![Windows HP Smart Printing settings showing the virtual printer removal option](../images/hp-smart-printing-cancellation/23-remove-hp-smart-printing-virtual-printer.png)

## Verification & Post-Incident Review

* **Verification:** The original PDF printed successfully through the recreated HP Smart Printing virtual printer after the previous HP Smart Printing queue was removed and recreated.
* **User Confirmation:** The client confirmed that printing was restored and the previously failing document completed successfully.
* **Technical Note:** When a printer can successfully print a Windows Test Page and the same document through its direct printer queue, avoid unnecessary hardware or driver replacement. Compare the working native queue against any application or virtual printer path, then remediate only the failing layer. Repair and reset are appropriate intermediate steps before recreating a virtual printer queue.
