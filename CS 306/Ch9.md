### Computer Peripheral Devices

#### Definition

* A **peripheral** is a device connected to a computer but **not part of the core architecture**.
* **Core components**: CPU, motherboard, power supply, and computer case.
* **Peripherals** enhance functionality but often depend on the computer system to operate.

#### Purpose and Dependency

* **Examples**: Printers, monitors, keyboards, mice, etc.
* Most peripherals are **non-functional without a computer** (e.g., a printer can't operate independently).
* Peripherals can be **external** (printer, keyboard) or **internal** (optical drive, sound card).

#### Categories of Peripherals

1. **Input Devices** – Send data to the computer

   * Examples: Keyboard, mouse, scanner, microphone
2. **Output Devices** – Receive data from the computer

   * Examples: Monitor, printer, speakers
3. **Storage Devices** – Store and retrieve data

   * Examples: Hard drives, flash drives, CD/DVD drives

*Note*: Some devices, like CD drives, serve as both input (read) and output (write).

#### Internal vs. External Peripherals

* **Internal (Integrated) Peripherals**:

  * Installed inside the computer (e.g., hard drives, optical drives, expansion cards)
  * Connected to the motherboard via expansion slots
* **External Peripherals**:

  * Connected via wired (USB, HDMI) or wireless (Bluetooth, Wi-Fi) methods

#### Connection Methods

* **Wired Connections**:

  * Most common: **USB**
  * Others: HDMI, Thunderbolt, Ethernet
* **Wireless Connections**:

  * **Bluetooth**: Short-range, used for mice, keyboards
  * **Wi-Fi**: Longer-range, enables wireless printing and file transfers

#### Example System Components

* **Internal Peripherals**:

  * Hard disk drive
  * Optical disc drive
  * Video/sound cards
* **External Peripherals**:

  * Monitor, printer, keyboard, mouse, speakers, scanner, webcam, external drives

#### Summary

* **Peripherals enhance computer capability**.
* Some are **critical** (monitor, keyboard), while others are **optional** (printer, scanner).
* They can be **internal or external**, and connect via **wired or wireless** methods.
* Understanding peripherals helps in **building or upgrading** a computer system effectively.


### Input/Output (I/O) in Computer Systems

#### Definition

* I/O refers to **any interaction between a data-processing system and the outside world**.
* **Example**: A touch-screen soda machine where you select a drink (input) and receive it in a cup (output).
* In computing, **input** is data received from an external source, and **output** is data sent to an external destination.

#### Basics of I/O in Computers

* For every **input**, there is a corresponding **output**.
* I/O includes **devices**, **programs**, and **operations** that facilitate **data exchange** between computers and external sources.
* **Examples**:

  * **Input**: Keyboard (press key → character appears)
  * **Output**: Printer (prints file to paper)
  * **Input/Output**: Modem (receives internet signal and provides connectivity)

#### I/O Ports

* Devices connect to computers through **I/O ports** such as:

  * **USB**
  * **VGA**
  * **HDMI**, etc.

#### Types of I/O Control Methods

1. **Programmed I/O**

   * CPU **constantly checks** devices for input.
   * Device signals → CPU processes → output occurs.
   * **Example**: Sending a print job from the computer to the printer.

2. **Interrupt-Based I/O**

   * CPU **performs other tasks** until interrupted by an I/O signal.
   * Improves efficiency.
   * **Example**: Keyboard input pauses CPU to handle keystroke.

3. **Direct Memory Access (DMA)**

   * **Transfers data directly** between memory and device without involving the CPU.
   * **Reduces CPU load** for large transfers.
   * **Example**: Moving photos from a camera to the computer.

4. **Channel I/O**

   * Used in **mainframes and servers**.
   * Multiple processors **handle multiple I/O devices simultaneously**.
   * **Example**: Enterprise servers servicing hundreds of user requests.

#### Read & Write Order of Operations

**I/O Read Sequence**:

1. Processor signals I/O device.
2. CPU reads data from the device.
3. Data is transferred to computer.
4. Data is stored in memory.

**I/O Write Sequence**:

1. Processor signals the target I/O device.
2. CPU prepares data from memory.
3. CPU sends data to the device.
4. Device writes the data.

#### Summary

* I/O involves communication between a system and external sources.
* Four main I/O control methods:

  * **Programmed I/O**
  * **Interrupt-Based I/O**
  * **DMA**
  * **Channel I/O**
* Efficient I/O is essential for **performance**, especially in high-demand systems like servers.
* Proper **read/write sequences** ensure successful data transfer between devices and the computer.

### Computer System & System Bus

#### Computer System Overview

* **CPU (Central Processing Unit):** Acts as the control center where all decisions are made.
* **Addressable Memory:** Stores data at specific physical addresses for later access.
* **Input/Output Devices:** Allow interaction with data (e.g., keyboard, screen, printer).

#### What Is a System Bus?

* The **system bus** connects the CPU, memory, and I/O devices.
* Functions like a **data highway** or **internal train track** system.
* Carries three types of information:

  * **Data:** Digital information being transferred.
  * **Address:** Location info for where data is stored or headed.
  * **Control:** Instructions for managing data flow and routing.

#### Components of the System Bus

* **Data Bus:** Transfers actual data between components.
* **Address Bus:** Specifies source and destination memory locations.
* **Control Bus:** Directs operations (e.g., read/write, timing, direction).

#### System Bus Operation Example

* Playing a song from disk:

  * **Address bus** locates MP3 file and sound card.
  * **Control bus** sets up communication.
  * **Data bus** transfers song data to be played.

#### System Bus Performance Factors

* **Bus Width:** Number of bits transferred simultaneously.
* **Bus Speed:** Speed at which data moves—measured in MHz.
* **Front-Side Bus (FSB):** Connects CPU to main memory.
* **Back-Side Bus (BSB):** Connects CPU to cache memory (on-chip, faster access).

#### Importance of Bus Speed

* A fast CPU and large memory are only useful if **FSB is also fast**.
* **FSB speed** is a key performance metric in modern systems.

#### Key Terms & Definitions

| **Term**             | **Definition**                                                           |
| -------------------- | ------------------------------------------------------------------------ |
| CPU                  | Central processing unit; routes and processes all instructions           |
| Addressable Memory   | Storage with specific physical addresses                                 |
| Input/Output Devices | Interfaces for user interaction (keyboard, mouse, monitor)               |
| System Bus           | Set of pathways that connect CPU, memory, and peripherals                |
| Motherboard          | Main circuit board housing the system bus and components                 |
| USB                  | Universal Serial Bus; standard interface for connecting external devices |
| Data                 | Actual digital information to be processed or transferred                |
| Address              | Location information for data routing                                    |
| Control              | Instructions that manage and direct data transfer                        |
| Bus Width            | Number of bits a bus can handle at once                                  |
| Bus Speed            | Frequency at which data is transferred (measured in MHz)                 |
| Cache Memory         | Fast memory built into CPU for quick access                              |

### Don't Be Late For the Bus!

#### System Bus Operations

In computer systems, the **system bus** operates similarly to public transportation — getting from point A to B involves several steps. When performing operations:

* The **Direct Memory Access (DMA)** circuit initiates the process by asserting (raising) the **Request** and **Write** signals.
* The **bus controller** checks the **address line**.
* If the controller sees its address and the disk is writable, it sends a **Ready** signal.
* Once the Ready line is active, the bus is in use.
* The **Request flag** is then lowered, triggering the **disk controller** to transfer a byte of data.
* Finally, the controller lowers the Ready signal.

This back-and-forth is managed by **bus timing diagrams** to visually represent the sequence and timing of events.

#### Flag Signaling — Like Ships at Sea

Bus signaling is often compared to **raising flags** on ships:

* **"Asserted"** signals mean the flag (or line) is raised.
* Lowered lines mean the flag is dropped.
* Timing diagrams show when signals go **high (on)** or **low (off)** over time.

For example:

* The **Request** line might assert just after time t1 and lower again after t4.

#### Understanding Bus Timing Diagrams

Timing diagrams help visualize multiple signals over time:

* **Y-axis:** Shows signal lines (Request, Address, Read/Write, Ready, Data, Clock).
* **X-axis:** Represents time (t0 to t10).
* **Up = signal on**, **Down = signal off**.
* The **Clock line** shows ticks:

  * On the **rise** of each tick, an **address** is sent.
  * On the **fall**, a **read/write** action is carried out.

#### Memory Read/Write Operations

Zooming in, we look at how **read** and **write** memory operations occur in a full **bus cycle** (the time to complete one read or write):

* Each **vertical dashed line** = one **clock cycle**.
* The entire diagram = one **bus cycle**.

**READ Operation Sequence:**

1. CPU broadcasts the address, asserts **REQUEST** and **READ**.
2. CPU waits for the memory to transfer data.
3. CPU copies data to its register.
4. CPU clears the request and address.

**WRITE Operation Sequence:**

1. CPU asserts **REQUEST** and **WRITE**, sends address and data.
2. CPU waits for write completion.
3. CPU clears all values and the write request.

This timing prevents overlaps in reading and writing and ensures data consistency.

#### Lesson Summary

* A **bus timing diagram** is a visual representation of how signals change over time during data transfer operations.
* It shows **when** signals are raised or lowered, similar to **flags on a ship**.
* **Clock cycles** represent the system’s rhythm, while **bus cycles** show the full duration of a read or write operation.
* Delays in asserting/deasserting signals, even if small, **accumulate** and impact overall performance.
* These diagrams help architects design and debug systems to ensure efficient memory and bus usage.

### Types of Computer Storage

#### Magnetic Storage

* **Overview**: One of the earliest storage technologies. Uses magnetic fields to store data.
* **Examples**:

  * **Magnetic tapes**: Early mainframe backups.
  * **Floppy disks**:

    * 5¼-inch floppy: \~360 KB (text-only).
    * 3½-inch floppy: \~1.44 MB (\~750 pages).
  * **ZIP drives**: 100 MB to 500 MB, but suffered from poor backward compatibility.
  * **Hard drives**: Now store 1+ TB; compact and portable.

#### Optical Storage

* **Technology**: Uses **lasers** to read/write data. More durable than magnetic media.
* **Examples**:

  * **CDs**: \~700 MB (1 hour of music).
  * **DVDs**: \~4.7 GB (a standard movie).
  * **Blu-rays**: Larger capacity; used for HD content.

#### Semiconductor Storage

* **Technology**: Uses silicon chips and electrical charge.
* **Examples**:

  * **Flash drives (USB)**: Highly portable, now up to 1+ TB.
  * **RAM**: Volatile memory used during active processing.
  * **Other Devices**: MP3 players, smartphones, digital cameras.

#### Wireless & Network Storage

* **External Drives**: Can connect via **Bluetooth** or **Wi-Fi** through a router.
* **Network Access**: Allows multiple devices to access the drive wirelessly.

#### Cloud Storage

* **Definition**: Stores files via the Internet on remote servers.
* **Characteristics**:

  * Perceived as intangible, but data resides on physical servers.
  * Offers free storage (\~2–10 GB) with paid upgrade options.
* **Difference from Cloud Computing**:

  * **Cloud storage**: Used for file backup and access.
  * **Cloud computing**: Uses web-based apps to create files, which may also be stored locally.

#### Lesson Summary

* **Three main types**: Magnetic, optical, and semiconductor storage.
* **Trend**: Rapid evolution in capacity, portability, and access methods.
* **Modern Storage**: Includes local physical media and remote cloud solutions.
* **Outlook**: Continued innovation and integration with wireless and cloud-based technologies.

### Flash Memory: What You Need to Know

#### What Is Flash Memory?

* **Definition**: Flash memory is a **non-volatile**, **solid-state** data storage technology that retains data even when power is off.
* **Structure**: Made up of memory chips mounted on a circuit board, with **no moving parts**.
* **Form Factors**: Found in devices from USB thumb drives to full-size computer drives.

#### Benefits of Flash Memory

* **Efficient Erasing**: Deletes data in **blocks** instead of one bit at a time — making updates faster.
* **Versatile Usage**: Can be used in smartphones, cameras, laptops, tablets, and more.
* **Silent Operation**: No mechanical parts = **no noise**.
* **Durability**: More resistant to physical shock (good for portable devices and motion-heavy activities).
* **Lower Power Consumption**: Uses less power, which improves **battery life**.
* **Less Heat Output**: Reduced heat generation helps maintain comfort and performance.
* **Compact and Lightweight**: Smaller and lighter than traditional hard drives.

#### Comparing Flash Memory to Spinning Hard Drives

* **Spinning Drives**:

  * Use **magnetic platters** and read/write heads.
  * Can be noisy and generate heat.
  * Vulnerable to movement and shock.
  * Lower cost per GB (e.g., \~\$50 for 1TB as of 2016).
* **Flash Drives (e.g., SSDs)**:

  * Faster access and data transfer speeds.
  * More durable and power-efficient.
  * More expensive (5–6x cost of HDDs per GB at the time).

#### Decision Making: What Jonas Learned

Jonas learned that although flash storage is **more expensive**, it provides significant benefits in terms of:

* **Speed**
* **Battery efficiency**
* **Physical durability**
* **Noise and heat reduction**

He decided the upgrade was worth it — even considering similar upgrades for other electronics.

#### Lesson Summary

* **Flash memory** is a reliable, fast, and efficient data storage solution.
* **Non-volatile and solid-state**, it excels in modern portable devices and computing.
* It outperforms traditional hard drives in most categories, except **cost per storage unit**.
* Ideal for users seeking **speed, portability, and efficiency** despite the higher price tag.

### RAID: Redundant Array of Independent Disks

#### What Is RAID?

* **RAID** stands for **Redundant Array of Independent Disks**.
* It's a method of combining multiple hard drives into a single system to:

  * Improve **performance** (faster reads/writes).
  * Increase **reliability** (prevent data loss due to drive failure).
* Appears to the operating system as one single drive.
* Originally known as "Inexpensive Disks", the term later changed to "Independent".

#### Why Use RAID?

* **Single drive limitations**:

  * Hard drives **will fail** eventually — the timing is uncertain.
  * Disk read/write speeds are **limited**, especially with large files or multiple requests.
* **RAID addresses both** reliability and performance concerns.

---

#### Key Concept: Striping

* **Striping** breaks data into **blocks** and spreads them across multiple disks.
* Example with 3 disks:
  Block 1 → Disk 1
  Block 2 → Disk 2
  Block 3 → Disk 3
  Block 4 → Disk 1 (repeats)
* Creates "stripes" across disks, improving performance.

---

#### RAID 0 – Performance

* Uses **striping**, **no redundancy**.
* Pros:

  * Fast read/write speeds.
  * Ideal for performance-heavy tasks.
* Cons:

  * **No fault tolerance** — if one disk fails, data is lost.

---

#### RAID 1 – Reliability

* Uses **disk mirroring**: data is duplicated across two or more disks.
* Pros:

  * High reliability — one disk can fail without data loss.
  * Faster **read** performance (from either disk).
* Cons:

  * Slower **write** performance (must write to both disks).
  * **Storage efficiency** is 50% (2×500GB = 500GB usable).

---

#### Higher RAID Levels (e.g., RAID 5, 6, 10)

* Combine **striping and redundancy** for:

  * Improved speed.
  * Fault tolerance.
* Typically requires **3–5 or more disks**.
* Example scenario:

  * If a drive fails, it can be swapped out and **data rebuilt** automatically.

---

#### Disadvantages of RAID

* **Storage Loss**: Redundancy reduces usable capacity.
* **No Replacement for Backups**: RAID protects from hardware failure, not disasters (e.g., fire, theft).
* **Complex Setup**: RAID level selection and configuration require technical understanding.
* **Additional Costs**: Requires **hardware/software RAID controllers**.

---

#### RAID vs. Modern Alternatives

* **SSDs (Solid State Drives)**:

  * Much faster and more reliable than spinning drives.
* **Cloud Storage**:

  * Easier, scalable, and backup-friendly.
* **Software Solutions**:

  * New tools reduce dependence on traditional RAID setups.

Yet RAID (especially **RAID 1**) remains popular for local redundancy.

---

#### Lesson Summary

* **RAID** is a data storage strategy using multiple hard drives to appear as one.
* It improves:

  * **Reliability** (protection from hardware failure).
  * **Performance** (faster data access).
* **RAID Levels**:

  * **RAID 0** – Speed only.
  * **RAID 1** – Redundancy.
  * **Higher levels** – Balance of both.
* RAID is evolving, but still relevant — especially when combined with **SSDs**, **cloud**, and **software solutions**.

### Get on the Bus!

#### Introduction to Bus Architecture

A **bus** in a computer is a communication pathway between key components like the **CPU**, **memory**, and **I/O devices**. It acts like a set of **train tracks**, transmitting:

* **Data** (actual information)
* **Address** (location of the data)
* **Control** (management of transfers)

#### USB Architecture

The **Universal Serial Bus (USB)** was developed to provide a **standardized way to connect peripherals** to computers.

Inside the USB device:

* A **Serial Interface Engine** handles sending/receiving data.
* The **Function Layer** represents the USB device’s internal software.

#### USB Connector Pins

| Pin | Color | Name | Use             |
| --- | ----- | ---- | --------------- |
| 1   | Red   | VBUS | Power (5 volts) |
| 2   | White | D-   | Data -          |
| 3   | Green | D+   | Data +          |
| 4   | Black | GND  | Ground          |

* **D+ and D-** control binary data transmission using voltages.
* When a binary `1` is sent, **Data+** is active; a `0` activates **Data-**.

#### USB Timing Diagram & NRZI Encoding

Timing diagrams help visualize the state of signals over time. For USB:

* **1 = idle**, **0 = active**
* **NRZI (Non-Return to Zero Invert)** is used for encoding data more efficiently.
* **Bit stuffing** is used to insert logic 1s during long idle sequences to maintain synchronization.

---

#### SCSI Architecture

**SCSI** stands for **Small Computer System Interface** (pronounced *skuzzy* or *skuz-ee*). It’s a high-performance standard used for connecting devices like:

* DVD drives
* RAID systems
* Scanners

#### Layers of SCSI

* **Kernel Layer** (hardware level)
* **Lower Layer**: drivers for SCSI/non-SCSI buses
* **Mid Layer**: binds communication layers
* **Upper Layer**: disk drivers (SD), CD/DVD (SR), tape (ST), generic (SG)

#### SCSI Pin Configuration

SCSI connectors (e.g., Type A) can have up to **50 pins**, including:

* **Data lines** (D0 to D7)
* **I/O lines**
* **Ground wires**
* **Signal selectors and acknowledgements**

#### SCSI Timing Diagram

The SCSI timing diagram demonstrates:

* **BSY (Busy)** and **SEL (Select)** signals
* Devices (e.g., D1, D2) competing for selection
* Timing events measured in nanoseconds
* Device 2 wins selection after asserting SEL

---

#### Lesson Summary

* **Bus systems** like USB and SCSI connect peripheral devices to computers.
* **USB** is widely used, simple, and uses **4 pins** (power, 2 data lines, ground).
* **SCSI** is more complex with **50 pins**, allowing for higher performance and multi-device communication.
* **Timing diagrams** are crucial tools to visualize and analyze bus activity, data synchronization, and device control.

### What Is Amdahl's Law?

#### Concept Introduction

Imagine Sam, Jack, and Harry all going to a party. They must arrive separately but enter together. Sam drives, Jack uses a motorcycle, and Harry walks. Despite Sam and Jack being fast, they all must wait for Harry. **Harry is the bottleneck** — the limiting factor in performance.

This metaphor illustrates **Amdahl's Law**, which states that **the overall performance improvement of a system is constrained by the portion that cannot be improved**. In computing, while processors get faster, I/O devices like memory and storage often lag behind, limiting system-wide speed gains.

---

#### Amdahl’s Law Formula

Amdahl’s Law is mathematically defined as:

```
Smax = 1 / [(1 - p) + (p / s)]
```

Where:

* `Smax` = Maximum overall speedup
* `p` = Proportion of the system that *can* be improved
* `s` = Speedup factor for the improved portion

---

#### Examples of Amdahl’s Law in Action

**Example 1:**
If 25% of a system can be improved and that portion is made twice as fast (`s = 2`):

```
Smax = 1 / [(1 - 0.25) + (0.25 / 2)]
     = 1 / [0.75 + 0.125]
     = 1 / 0.875
     = ~1.14 (14% improvement)
```

**Example 2:**
If 75% of the system can be improved and is also made twice as fast:

```
Smax = 1 / [(1 - 0.75) + (0.75 / 2)]
     = 1 / [0.25 + 0.375]
     = 1 / 0.625
     = 1.6 (60% improvement)
```

**Insight:** Even with the same speedup factor, improving a larger portion of the system leads to greater overall performance gains.

---

#### Application of Amdahl's Law

Let’s compare improvements on two components:

**Component 1:**

* 85% of it can be improved
* Speedup factor = 1.5 (50% faster)

```
Smax = 1 / [(1 - 0.85) + (0.85 / 1.5)]
     = 1 / [0.15 + 0.567]
     = 1 / 0.717
     = ~1.40 (40% improvement)
```

**Component 2:**

* 20% can be improved
* Speedup factor = 4

```
Smax = 1 / [(1 - 0.20) + (0.20 / 4)]
     = 1 / [0.80 + 0.05]
     = 1 / 0.85
     = ~1.18 (18% improvement)
```

**Conclusion:** Even though Component 2 is sped up *more*, Component 1 offers *greater overall performance gains* due to its larger share of the system.

---

#### Lesson Summary

* **Amdahl’s Law** helps identify which parts of a system should be optimized.
* The **formula**: `Smax = 1 / [(1 - p) + (p / s)]`
* **Key takeaway**: The **larger the portion of the system that cannot be improved**, the **less the overall benefit** from performance enhancements.
* Designers should focus improvements on the **largest contributors to system execution time**, even if the speedup factor is modest.
