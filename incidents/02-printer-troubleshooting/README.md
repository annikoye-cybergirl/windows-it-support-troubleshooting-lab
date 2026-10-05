# Incident 02 — Printer Troubleshooting

## Incident Overview

This lab simulates a common Windows IT Support incident where a user is unable to print because the Windows Print Spooler service has stopped.

The issue was intentionally reproduced in a controlled Windows 11 virtual machine environment. The Print Spooler service was stopped, the resulting printer error was investigated, the service was restarted, and printing was successfully verified.

---

## User Report

**Reported Issue:**
User is unable to print a document using Microsoft Print to PDF.

**Error Message:**

> Your printer has experienced an unexpected configuration problem.

---

## Environment

* **Operating System:** Windows 11 Pro
* **Device:** WIN-ITLAB01
* **Virtualization:** Oracle VirtualBox
* **Printer:** Microsoft Print to PDF
* **Lab Type:** Windows IT Support Troubleshooting Lab

---

## Initial Symptoms

Before reproducing the issue, Microsoft Print to PDF was tested successfully.

A test document was printed and Windows successfully prompted for a location to save the PDF.

This confirmed that the printer was initially functioning correctly.

---

## Troubleshooting Methodology

The following troubleshooting approach was used:

1. Establish a known-good baseline.
2. Reproduce the printer failure in a controlled environment.
3. Observe the error message.
4. Check Windows printer-related services.
5. Identify the Print Spooler service as the likely cause.
6. Restart the affected service.
7. Retest printing.
8. Confirm successful resolution.

---

## Investigation

The Windows **Print Spooler** service was intentionally stopped using the Windows Services management console.

After the service was stopped, an attempt was made to print using Microsoft Print to PDF.

Windows displayed the following error:

> Your printer has experienced an unexpected configuration problem.

The **Print Spooler** service was then checked in:

`services.msc`

The service status was found to be:

**Stopped**

---

## Root Cause

The root cause of the printing failure was the **Print Spooler service being stopped**.

The Print Spooler service is responsible for managing print jobs and communication between Windows and installed printers.

When the service was stopped, Windows could not process the print request correctly.

---

## Resolution

The following corrective action was performed:

1. Opened `services.msc`.
2. Located **Print Spooler**.
3. Started the service.
4. Confirmed that the service status changed to **Running**.
5. Retested Microsoft Print to PDF.
6. Successfully printed and saved the document as a PDF.

---

## Verification

After restarting the Print Spooler service, Microsoft Print to PDF was tested again.

The document was successfully processed and saved as a PDF.

This confirmed that the printer functionality had been restored.

---

## Evidence

### 1. Print Spooler Stopped

The Print Spooler service was stopped during the incident and the printer produced an error.

![Print Spooler Stopped](../../screenshots/incident-02/incident-02-spooler-stopped.png)

### 2. Print Spooler Running

The Print Spooler service was restarted and confirmed to be running.

![Print Spooler Running](../../screenshots/incident-02/incident-02-spooler-running.png)

### 3. Successful Print Test

Microsoft Print to PDF successfully processed the test document after the Print Spooler service was restarted.

![Successful Print](../../screenshots/incident-02/incident-02-print-success.png)

---

## Lessons Learned

This incident demonstrated the importance of checking Windows services when troubleshooting printer problems.

A printer error does not always indicate a problem with the physical or virtual printer itself. Windows services such as the Print Spooler can directly affect printing functionality.

A structured troubleshooting process helps isolate the cause efficiently.

---

## Technical Skills Demonstrated

* Windows 11 troubleshooting
* Printer troubleshooting
* Microsoft Print to PDF
* Windows Services
* Print Spooler troubleshooting
* Service management
* Error analysis
* Root cause identification
* Incident documentation
* Troubleshooting methodology
* Technical documentation
* GitHub documentation

---

## Outcome

**Status:** Resolved

**Root Cause:** Print Spooler service was stopped.

**Resolution:** Restarted the Print Spooler service.

**Verification:** Microsoft Print to PDF successfully printed and saved the test document.

**Result:** Printer functionality restored successfully.
