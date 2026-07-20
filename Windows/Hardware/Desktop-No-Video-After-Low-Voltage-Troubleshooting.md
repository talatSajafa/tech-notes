# Restoring a Desktop That Displayed "No Signal" After a Low-Voltage Power Event

## Overview

This document describes how I diagnosed and resolved a desktop computer that failed to display video after an unexpected low-voltage power event.

Rather than immediately replacing hardware, I systematically eliminated possible causes before identifying the solution.

---

## System Information

| Component | Information |
|-----------|-------------|
| Device | Desktop Computer |
| Display Connection | VGA |
| Initial Issue | No video output after a low-voltage event |

---

## Problem

Following a period of unstable electrical power where the household lights flickered and the desktop shut down unexpectedly, the computer would no longer display video after being powered on.

### Symptoms

- The desktop appeared to receive power.
- The monitor displayed **"VGA: No Signal."**
- No video output was detected.
- Restarting the computer did not resolve the issue.

---

## Investigation

Since the issue occurred immediately after an unstable power event, I decided to troubleshoot the system by eliminating the simplest and most likely causes first.

---

### Attempt 1: Verify Monitor Input

The monitor displayed the message:

> **VGA: No Signal**

To determine whether the issue was caused by an incorrect input source, I opened the monitor's on-screen display (OSD) menu and checked the available input options.

The monitor supported:

- VGA
- DVI
- Auto Input Detection

I manually selected both **VGA** and **DVI**, then enabled **Auto Input Detection**.

#### Result

None of the available input modes detected a video signal.

This confirmed that the monitor itself was functioning correctly but was not receiving video output from the desktop.

---

### Attempt 2: Inspect the Display Cable

Next, I disconnected the VGA cable from both the monitor and the desktop.

After reconnecting it securely, I tightened the connector screws to ensure proper electrical contact.

#### Result

The monitor continued displaying **"No Signal."**

This suggested that a loose display cable was unlikely to be the cause.

---

### Attempt 3: Inspect and Reseat the RAM

Since memory issues can prevent a system from completing POST and producing video output, I opened the desktop case and removed the RAM modules.

The modules were cleaned using a dry, lint-free cloth and then securely reinstalled.

> **Important**
>
> Never use water or liquid cleaning products on RAM modules or their electrical contacts.

#### Result

The problem remained unchanged.

---

### Next Planned Step

Since the issue had not yet been resolved, my next troubleshooting step was to test each RAM module individually.

The planned procedure was:

1. Remove one RAM module.
2. Attempt to boot the system using only the remaining module.
3. Repeat the process using the other RAM module.

This would help determine whether one of the memory modules had failed.

Before performing this test, however, I reconsidered the events leading up to the failure.

The desktop had stopped working immediately after an unstable power event, so I decided to perform a complete power drain before continuing with additional hardware testing.

---

## Final Solution: Perform a Power Drain

To discharge any residual electrical charge stored within the system:

1. Shut down the computer.
2. Disconnect the power cable.
3. Press and hold the power button for approximately **15 seconds**.
4. Reconnect the power cable.
5. Start the computer normally.

#### Result

The desktop booted successfully, and the monitor immediately detected the video signal.

No additional hardware repairs were required.

---

## Key Takeaways

### Begin With the Simplest Checks

Testing monitor settings and cable connections first helped eliminate common external causes before opening the computer.

---

### Troubleshoot Methodically

Each troubleshooting step ruled out a possible cause, reducing the number of remaining possibilities.

This made the investigation more systematic instead of relying on guesswork.

---

### Consider Recent Events

The timing of a problem often provides valuable clues.

In this case, the issue occurred immediately after a low-voltage power event, which ultimately led to the correct solution.

---

### Use the Least Invasive Solution First

Before removing additional hardware or assuming component failure, consider whether a simpler recovery procedure may resolve the issue.

Performing a power drain avoided unnecessary hardware testing.

---

### Handle Hardware Safely

Always disconnect power before opening a computer.

Hold RAM modules by their edges and avoid touching the electrical contacts.

---

## Concepts Practiced

- Step-by-step hardware troubleshooting
- Fault isolation
- Monitor input configuration
- Video signal troubleshooting
- RAM inspection and reseating
- Power drain procedures
- Considering environmental factors during diagnosis
- Logical problem-solving

---

**Status:** Complete

*Last Updated: July 2026*
