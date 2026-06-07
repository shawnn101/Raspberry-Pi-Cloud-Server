# Raspberry-Pi-Cloud-Server
# Custom GPIO-Controlled RAM Module for Raspberry Pi

> ## 🚧 Project Status Update
>
> **Physical hardware construction is currently on hold while electronic components are being delivered.**
>
> The memory architecture, component selection, and digital simulations are actively being developed and validated. Once all required components arrive, the project will move into breadboard prototyping, hardware verification, and Raspberry Pi integration.

---

# Overview

Over the past several months, I have been slowly running out of storage space as I have begun saving files, photos, and videos across multiple devices and drives. Although my Raspberry Pi has remained operational for small projects such as my TTC Bus Tracker, I wanted to expand its capabilities beyond simply collecting and displaying transit data. The long-term goal is to transform the Raspberry Pi into a compact home server capable of storing files, hosting services, and running custom applications.

Rather than building a conventional Raspberry Pi server, I wanted to explore a hardware-focused approach that would combine software and digital logic design. This project therefore aims to design and build a custom addressable RAM module using discrete digital logic components and interface it with a Raspberry Pi through GPIO communication.

While the custom RAM module will not replace the Raspberry Pi's onboard system memory, it will serve as an external, hardware-controlled memory device accessible directly by software. The module can be used to store server state information, request counters, status flags, cache-like data, and other frequently accessed values. For example, the server could maintain a hardware-backed visitor counter, track application states, store access control information, or cache small pieces of frequently requested data without relying entirely on software-managed memory structures.

---

# Current Architecture

The current design:

| Specification    | Value             |
| ---------------- | ----------------- |
| Memory Locations | 16                |
| Data Width       | 8 bits            |
| Total Capacity   | 16 bytes          |
| Address Width    | 4 bits            |
| Interface        | Raspberry Pi GPIO |

The memory system uses a shared bus architecture similar to real computer memory systems.

---

# Hardware Components

## Storage

* 16 × 74HC573 Octal Latch ICs

  * Each IC stores one byte (8 bits)
  * 16 latches provide a total of 16 bytes of storage

## Address Selection

* 1 × 74HC154 4-to-16 Decoder

  * Selects which memory location is active

## Bus Control

* 2 × 74HC245 Bus Transceivers

  * Write path control
  * Read path control

## Supporting Components

* 0.1 µF decoupling capacitors (one per IC)
* 220 Ω resistors
* LEDs for debugging and visualization
* Breadboards / prototype PCB
* Jumper wires
* Raspberry Pi GPIO header

---

# Simulation / PCB Progress

Digital simulations are currently being performed using Logisim Evolution, and schematics/prints are being created using KiCad.

Completed work includes:

* Address decoding validation
* Register storage testing
* Shared bus verification
* Initial 2-byte memory prototype
* Curretn expansion planning toward a full 16-byte architecture

The simulation phase is being used to identify design issues before hardware construction begins.

---

# Planned Raspberry Pi Integration

The Raspberry Pi will act as the memory controller by:

* Setting address lines
* Providing data values
* Controlling read/write operations
* Reading stored data from the module


# Repository Contents

```text
/Documentation
    Research notes
    Design reports

/Simulation
    Logisim Evolution files

/KiCad
    Schematics
    PCB layouts

/Software
    Raspberry Pi GPIO control code

/Images
    Diagrams
    Screenshots
    Hardware photos
```

---

