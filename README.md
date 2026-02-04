# Buffer Overflow in Qualcomm Snapdragon X65 & X70 Basebands

### Satellite Modem Trigger with Remote Attack Surface


**Technical details:** Available in the attached vulnerability report

---

## Plain-Language Summary 

A serious flaw has been identified in widely used cellular chips... specifically the **Qualcomm Snapdragon X65 and X70**... that allows devices to be remotely disrupted without installing malware, clicking links, or requiring user interaction.

In certain conditions, a malicious cellular signal alone, including specially crafted 5G or satellite transmissions, could cause phones, laptops, and connected devices to suddenly lose service or reboot. To everyday users, this would look exactly like a normal carrier outage.

This issue affects the cellular hardware itself, not a specific phone brand or app.

---

## What Is the "Phone Home" Flaw?

Modern smartphones and connected devices contain a dedicated chip that handles cellular and satellite communication. This chip operates independently from apps and the operating system.

The Phone Home Flaw is a defect in how that chip handles internal data when the satellite modem changes state. Under reachable conditions, the chip can enter a failure state that forces the entire device to reset or lose connectivity.

```
┌─────────────────────────────────────────────────────────────┐
│                   HOW THE FLAW WORKS                        │
└─────────────────────────────────────────────────────────────┘

  Malicious Signal          Phone's Chip            What You See
   (from tower or             Crashes                        
    satellite)              
                                                            
       📡                        💥                      📱
        │                        │                       │
        │  Specially crafted     │  Internal             │
        │  transmission          │  failure              │
        ├───────────────────────>│                       │
        │                        │                       │
        │                        ├──────────────────────>│
        │                        │                       │
        │                        │                  ┌────▼────┐
        │                        │                  │ Phone   │
        │                        │                  │ Reboots │
        │                        │                  │   or    │
        │                        │                  │ Loses   │
        │                        │                  │ Service │
                                                    └─────────┘
                                             Advanced exploitation may enable
                                             additional unauthorized access

              NO USER ACTION REQUIRED
        Looks like a normal network outage   
```

**Importantly:**

- The issue exists below iOS, Android, or Windows
- It does not involve spyware, apps, or user data theft
- It is triggered by network signals, not software installed on the phone
- Exploitation can occur through malicious 5G transmissions or satellite signal manipulation

---

## Who Is Affected?

```
╔════════════════════════════════════════════════════════════╗
║         DEVICES USING QUALCOMM SNAPDRAGON X65/X70          ║
╚════════════════════════════════════════════════════════════╝

    📱 Smartphones              💻 Laptops              🏭 IoT Devices
    ─────────────              ──────────              ──────────────
    • iPhone 12-15             • 5G-enabled            • Industrial
      series                     laptops                 equipment
    • Android (recent)                                 • Connected
    • Modern 5G                                          infrastructure
      hotspots                                           

           Multiple manufacturers • Multiple operating systems
```

Because this chip is used across many manufacturers, the issue is not limited to one brand or operating system.

---

## What Could Happen to Users?

If triggered, affected devices may:

- Suddenly lose cellular service
- Reboot unexpectedly (within 1-2 seconds of trigger)
- Display "No Service" or "SOS only"
- Fail to reconnect to the network for a period of time

From the user's perspective, this would look like a carrier network outage, even though the underlying cause is device-level.

**There is no evidence that personal data, messages, or calls are accessed as part of this issue.**

---

## Why This Matters

Most cyberattacks require user interaction: clicking a link, opening a file, installing software.

**This issue is different.**

Because it occurs at the hardware communication layer:

- No user action is required
- Many devices in the same area could be affected at once
- The disruption could be difficult to distinguish from normal network problems

This makes the flaw especially relevant for:

- Emergency communications
- Dense urban areas
- Critical infrastructure that relies on cellular connectivity

---

## About the January 2026 Network Disruption

On January 14, 2026, devices in multiple U.S. regions experienced cellular service disruptions that exhibited crash patterns consistent with this vulnerability.

Independent forensic analysis of affected devices revealed:
- Satellite modem state transitions triggering memory corruption
- System crashes with watchdog timeouts
- Reboot sequences matching the vulnerability signature

While this does not prove malicious activity, it demonstrates how exploitation of this flaw could closely resemble a routine carrier outage.

---

## What This Does NOT Mean

To avoid misunderstanding:

```
❌ This is not proof that a carrier or manufacturer acted improperly
❌ This is not something users can fix themselves
```

It does mean that coordination between chipset vendors, device makers, and carriers is required to fully address the issue.

---

## What Is Being Done?

- The vulnerability has been reported to the responsible vendors
- Coordinated disclosure is underway with CISA oversight
- A fix will require updates at the chipset and device level

---

## Where to Find Technical Details

`Vulnerability Report.md`

This README is intentionally non-technical.




---

## Disclosure Status

| Field | Value |
|-------|-------|
| **Vulnerability name** | Phone Home Flaw |
| **Severity** | Critical |
| **CVE** | Pending assignment |
| **CWE** | CWE-120 (Buffer Overflow) |
| **Affected component** | Qualcomm Snapdragon X65/X70 baseband processor |

---

## Final Note

This report is published in the interest of transparency, responsible security research, and public understanding. Its purpose is to explain risk and impact, not to enable exploitation.
