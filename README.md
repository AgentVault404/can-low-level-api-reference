# CAN Low Level (CL2) API Reference

CAA Can Low Level Extern Library Documentation

**Version:** 3.5.16.0  
**Source:** CODESYS GmbH / Schneider Electric Machine Expert V2.1  
**Library:** CAA_CanL2_Extern  

---

## Overview

This library contains functions for accessing the CAN field bus. Layer 7 applications (such as CANopen, J1939, DeviceNet and many others) can be realized based on this library.

> **Note:** The library can be used to access the CANbus in parallel to other CAN applications (e.g. CANopenStack), even if they use the same port. All functions are thread-safe and can be used from several tasks in parallel.

---

## Sections

- **Enums** — BUSSTATE, ERROR
- **Basic Functions** (15) — CloneMessage, CreateMessage, Read, Write, DriverOpenH, etc.
- **Diagnostic Information** (16) — GetBusState, GetBusload, GetBaudrate, error counters, etc.
- **Extended Functionality** — EnableSyncService, DisableSyncService
- **Indicator Services** — GetCiAState, SetCiAState
- **Message Information** (10) — GetMessageId, GetMessageLength, GetTimeStamp, etc.
- **Structures** — DIAGNOSIS_INFO
- **Global Variables** — IndicatorConstants
- **Internal Functions** (61) — Full internal API reference

**Total:** 96 entries across 13 categories, 68KB documentation.

---

See [CAN_Low_Level_CL2_API_Reference.md](CAN_Low_Level_CL2_API_Reference.md) for the full API reference.
