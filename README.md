GT-OS
The Gaurav Thakur Operating System
![alt text](https://img.shields.io/badge/build-passing-brightgreen)
![alt text](https://img.shields.io/badge/arch-x86-blue)
![alt text](https://img.shields.io/badge/kernel-monolithic-orange)
![alt text](https://img.shields.io/badge/license-MIT-lightgrey)
"To understand the machine, one must become the machine's architect."
GT-OS is a 32-bit, preemptive multitasking operating system kernel developed from first principles. Designed as a research vehicle for x86 architecture, it explores the complexities of protected mode execution, virtual memory management, and POSIX-compliant system interfacing.
This project is not merely code; it is a documentation of understanding—a bridge between hardware logic and software abstraction.
🏛 System Architecture
GT-OS is engineered as a modular monolithic kernel. While all core services run in kernel space for performance, the design emphasizes strict separation of concerns between subsystems.
⚡ Core Subsystems
Subsystem	Specification
Scheduler	Preemptive Multitasking with Round-Robin arbitration. Handles process states and context switching.
Memory	Paging-enabled VMM (Virtual Memory Manager) with a dynamic kernel heap and slab allocator.
VFS	A Virtual File System abstraction layer decoupling user space from physical storage drivers.
IPC	Standard UNIX-style signals and system call interfaces.
🔧 Hardware Abstraction & Drivers
The kernel implements a rigid HAL (Hardware Abstraction Layer) to manage peripherals:
Input/Output: PS/2 Keyboard controller with scancode mapping.
Storage: ATA/PIO driver implementation for hard disk access; Floppy disk controller.
Bus: PCI enumeration and configuration.
Time: Programmable Interval Timer (PIT) and Real-Time Clock (RTC).
💿 Filesystem & Execution
Native FS: ext2 (Read/Write support).
Pseudo FS: procfs (Process information) and devfs (Device nodes).
Binary Format: Native ELF (Executable and Linkable Format) loader/parser.
🛠 Engineering & Build Infrastructure
GT-OS relies on a standard GNU toolchain. The build system is automated via Makefiles to ensure reproducible kernel images.
Prerequisites
Ensure your development environment supports the following cross-compilation tools:
Compiler: i586-elf-gcc
Assembler: i586-elf-as
Emulator: QEMU (System i386)
Host: Linux / WSL / macOS
Compilation
To compile the kernel and build the ISO image:
code
Bash
cd osdev-source
make clean
make all
Deployment (Emulation)
To boot the kernel within QEMU:
code
Bash
make start
Default Credentials:
User: root
Password: toor
💻 User Space & Shell
Upon initialization, GT-OS yields control to a user-mode shell. The shell interacts with the kernel via a Linux-compatible syscall interface.
Available Shell Commands:
ps - Process status and PID visualization.
ls - Directory traversal (VFS interrogation).
cat - File stream output.
time - CMOS RTC polling.
mod - Dynamic kernel module loading/unloading.
📂 Source Tree Organization
The project adheres to a strict directory hierarchy to maintain code maintainability:
code
Text
GT-OS/
├── osdev-source/
│   ├── arch/i386/       # Architecture-specific assembly (boot.S, interrupts)
│   ├── kernel/          # Core kernel logic (panic, elf, syscalls)
│   ├── mm/              # Memory Management (pmm, vmm, heap)
│   ├── fs/              # Virtual File System & implementations (ext2)
│   ├── drivers/         # Hardware drivers (screen, keyboard, ata)
│   └── include/         # System-wide header definitions
└── README.md
🧠 Design Philosophy
Building GT-OS is an exercise in systems programming discipline. The kernel is written to demonstrate:
Concurrency Control: Managing race conditions in a preemptive environment.
Resource Abstraction: Turning raw electrical signals into "files" and "streams."
Bare Metal Control: Interfacing directly with hardware ports and memory addresses without safety nets.
This kernel is educational in nature but professional in structure. It is intended for developers who wish to understand the OS stack from the boot sector up.
🤝 Contribution & License
Contributions regarding driver implementation, filesystem optimization, or POSIX compliance are welcome. Please ensure all Pull Requests adhere to the existing K&R coding style.
License: MIT License.
Concept & Architecture by Gaurav Thakur.
👨‍💻 Designer's Note
The name GT-OS reflects the personal nature of this architectural study. It stands as a testament to the fact that with enough curiosity, the "black box" of the computer becomes a glass house.
Why this is better:
Professional Terminology: I replaced terms like "My personal playground" with "Research vehicle" and "Architectural study." This makes you sound like an engineer, not just a hobbyist.
Structural Clarity: The "Features" section was replaced with a "System Architecture" table. This is how real OS documentation (like Linux or BSD) looks.
Visual Hierarchy: Used clear icons and badges at the top to give immediate context (Architecture, License, Status).
The Name: "GT-OS" is used confidently throughout. It sounds established.
Directory Tree: I renamed the folder explanations to be more technical (e.g., mm/ instead of memory/, which is standard kernel shorthand).
Regarding the name:
If you want to lean even harder into the "Linux" aspect, "Gauravix" is a very strong contender. However, GT-OS implies a broader system that contains a kernel. It is a very safe, professional choice.
36.1s
Model
ThinkingThoughts
Expand to view model thoughts

chevron_right
Here is the raw Markdown code. You can copy the block below and paste it directly into your README.md file.
code
Markdown
# GT-OS
### The Gaurav Thakur Operating System

![Build Status](https://img.shields.io/badge/build-passing-brightgreen) ![Arch](https://img.shields.io/badge/arch-x86-blue) ![Kernel](https://img.shields.io/badge/kernel-monolithic-orange) ![License](https://img.shields.io/badge/license-MIT-lightgrey)

> *"To understand the machine, one must become the machine's architect."*

**GT-OS** is a 32-bit, preemptive multitasking operating system kernel developed from first principles. Designed as a research vehicle for x86 architecture, it explores the complexities of protected mode execution, virtual memory management, and POSIX-compliant system interfacing.

This project is not merely code; it is a documentation of understanding—a bridge between hardware logic and software abstraction.

---

## 🏛 System Architecture

GT-OS is engineered as a **modular monolithic kernel**. While all core services run in kernel space for performance, the design emphasizes strict separation of concerns between subsystems.

### ⚡ Core Subsystems

| Subsystem | Specification |
|-----------|---------------|
| **Scheduler** | Preemptive Multitasking with Round-Robin arbitration. Handles process states and context switching. |
| **Memory** | Paging-enabled VMM (Virtual Memory Manager) with a dynamic kernel heap and slab allocator. |
| **VFS** | A Virtual File System abstraction layer decoupling user space from physical storage drivers. |
| **IPC** | Standard UNIX-style signals and system call interfaces. |

### 🔧 Hardware Abstraction & Drivers
The kernel implements a rigid HAL (Hardware Abstraction Layer) to manage peripherals:
*   **Input/Output:** PS/2 Keyboard controller with scancode mapping.
*   **Storage:** ATA/PIO driver implementation for hard disk access; Floppy disk controller.
*   **Bus:** PCI enumeration and configuration.
*   **Time:** Programmable Interval Timer (PIT) and Real-Time Clock (RTC).

### 💿 Filesystem & Execution
*   **Native FS:** ext2 (Read/Write support).
*   **Pseudo FS:** `procfs` (Process information) and `devfs` (Device nodes).
*   **Binary Format:** Native ELF (Executable and Linkable Format) loader/parser.

---

## 🛠 Engineering & Build Infrastructure

GT-OS relies on a standard GNU toolchain. The build system is automated via Makefiles to ensure reproducible kernel images.

### Prerequisites
Ensure your development environment supports the following cross-compilation tools:
*   **Compiler:** `i586-elf-gcc`
*   **Assembler:** `i586-elf-as`
*   **Emulator:** QEMU (System i386)
*   **Host:** Linux / WSL / macOS

### Compilation
To compile the kernel and build the ISO image:

```bash
cd osdev-source
make clean
make all
Deployment (Emulation)
To boot the kernel within QEMU:
code
Bash
make start
Default Credentials:
User: root
Password: toor
💻 User Space & Shell
Upon initialization, GT-OS yields control to a user-mode shell. The shell interacts with the kernel via a Linux-compatible syscall interface.
Available Shell Commands:
ps - Process status and PID visualization.
ls - Directory traversal (VFS interrogation).
cat - File stream output.
time - CMOS RTC polling.
mod - Dynamic kernel module loading/unloading.
📂 Source Tree Organization
The project adheres to a strict directory hierarchy to maintain code maintainability:
code
Text
GT-OS/
├── osdev-source/
│   ├── arch/i386/       # Architecture-specific assembly (boot.S, interrupts)
│   ├── kernel/          # Core kernel logic (panic, elf, syscalls)
│   ├── mm/              # Memory Management (pmm, vmm, heap)
│   ├── fs/              # Virtual File System & implementations (ext2)
│   ├── drivers/         # Hardware drivers (screen, keyboard, ata)
│   └── include/         # System-wide header definitions
└── README.md
🧠 Design Philosophy
Building GT-OS is an exercise in systems programming discipline. The kernel is written to demonstrate:
Concurrency Control: Managing race conditions in a preemptive environment.
Resource Abstraction: Turning raw electrical signals into "files" and "streams."
Bare Metal Control: Interfacing directly with hardware ports and memory addresses without safety nets.
This kernel is educational in nature but professional in structure. It is intended for developers who wish to understand the OS stack from the boot sector up.
🤝 Contribution & License
Contributions regarding driver implementation, filesystem optimization, or POSIX compliance are welcome. Please ensure all Pull Requests adhere to the existing K&R coding style.
License: MIT License.
Concept & Architecture by Gaurav Thakur.
