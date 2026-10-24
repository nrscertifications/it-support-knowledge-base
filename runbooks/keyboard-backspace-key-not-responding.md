# Incident Report: Keyboard Backspace Key Not Responding

## Incident Summary

* **Request Type:** Hardware / Peripheral Support
* **Environment:** Windows 11 endpoint, Royal Kludge RK L75 mechanical keyboard, USB/HID keyboard input
* **Reported Issue:** The physical Backspace key stopped responding during normal use. Other keyboard input remained available, but pressing Backspace produced no action in Windows applications.

## Triage & Symptoms

* Reproduced the issue in a text-entry application and confirmed that pressing the physical Backspace key did not remove characters.
* Verified that Windows itself could still process a Backspace command by opening the Windows On-Screen Keyboard and testing Backspace through the software keyboard.
* Opened an online keyboard tester and pressed the physical Backspace key. The tester did not register the keypress while other keyboard keys were detected normally.
* These tests isolated the issue away from the Windows Backspace function itself and toward the physical keyboard/device input path.

![Windows On-Screen Keyboard used to validate Backspace input](../images/keyboard-backspace-key/02-on-screen-keyboard-backspace-test.png)

![Keyboard tester showing the physical Backspace key was not detected](../images/keyboard-backspace-key/03-keyboard-checker-backspace-not-detected.png)

## Root Cause Analysis

The fault was isolated to the physical keyboard/device input path rather than the Windows Backspace function or the active text-entry application.

Windows successfully processed Backspace through the On-Screen Keyboard, while the online keyboard tester did not detect the physical Backspace keypress. Disconnecting and reconnecting the Royal Kludge keyboard restored normal Backspace operation.

The exact underlying root cause was not definitively confirmed. Based on the observed behavior and successful remediation, the issue was consistent with a temporary keyboard connection, HID communication, or device-state problem rather than a confirmed failed key switch, Windows configuration fault, or driver failure.

## Remediation Steps

1. **Issue Reproduction:** Opened a text-entry application, entered test characters, and confirmed that pressing the physical Backspace key did not remove them.
2. **Windows Input Validation:** Opened the Windows On-Screen Keyboard using **Windows + Ctrl + O** and verified that Windows could still process Backspace through the software keyboard.
3. **Physical Key Detection Test:** Used an online keyboard tester to determine whether Windows received the physical keypress. Other keys registered, while Backspace did not respond.
4. **Keyboard Power/Connection Reset:** Disconnected the Royal Kludge keyboard, waited approximately 10–15 seconds, reconnected it, and allowed Windows to recognize the device again.
5. **Final Retest:** Tested the physical Backspace key again after reconnection. Backspace resumed normal operation.

## Verification & Post-Incident Review

* **Verification:** The physical Backspace key successfully removed characters after the keyboard was disconnected and reconnected.
* **User Confirmation:** Normal keyboard operation was restored without reinstalling drivers, resetting the keyboard, replacing the key switch, or disassembling the device.
* **Technical Note:** When a single physical key stops responding, first separate Windows/application behavior from physical-key detection. A software keyboard can confirm whether the operating system still processes the expected input, while a keyboard tester can determine whether the physical keypress is reaching Windows. Use non-destructive connection and power-state remediation before moving to driver, firmware, switch, or hardware replacement steps.
