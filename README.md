<div align="center">

# 🚀 GT-OS

### *The Gaurav Thakur Operating System*

![Build Status](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge)
![Architecture](https://img.shields.io/badge/arch-x86-blue?style=for-the-badge)
![Kernel Type](https://img.shields.io/badge/kernel-monolithic-orange?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=for-the-badge)

> *"To understand the machine, one must become the machine's architect."*

**A 32-bit preemptive multitasking operating system kernel built from scratch**

[Features](#-features) • [Architecture](#-system-architecture) • [Quick Start](#-quick-start) • [Documentation](#-documentation)

---

</div>

## 📖 About

**GT-OS** is a research-grade operating system kernel developed from first principles for the x86 architecture. This project explores the intricate world of protected mode execution, virtual memory management, and POSIX-compliant system interfaces.

This isn't just code—it's a journey into the heart of how computers work, bridging the gap between raw hardware and elegant software abstraction.

### 🎯 Purpose

- **Educational**: Designed for developers who want to understand OS internals from the boot sector up
- **Research**: A platform for exploring kernel design patterns and low-level systems programming
- **Professional**: Built with production-grade structure and engineering discipline

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🔄 Process Management
- Preemptive multitasking
- Round-robin scheduling
- Context switching
- Process state management

### 💾 Memory Management
- Paging-enabled VMM
- Dynamic kernel heap
- Slab allocator
- Protected mode execution

</td>
<td width="50%">

### 📁 File Systems
- **ext2** read/write support
- Virtual File System (VFS) layer
- **procfs** for process info
- **devfs** for device nodes

### 🔧 Hardware Support
- PS/2 keyboard controller
- ATA/PIO disk driver
- PCI bus enumeration
- RTC & PIT timers

</td>
</tr>
</table>

---

## 🏛 System Architecture

GT-OS follows a **modular monolithic kernel** design, where core services run in kernel space for performance while maintaining strict separation of concerns.

```
┌─────────────────────────────────────────┐
│         User Space Applications         │
├─────────────────────────────────────────┤
│          System Call Interface          │
├─────────────────────────────────────────┤
│                                         │
│  ┌──────────┬──────────┬──────────┐   │
│  │Scheduler │   VFS    │   IPC    │   │
│  ├──────────┼──────────┼──────────┤   │
│  │   VMM    │  Heap    │  Slab    │   │
│  └──────────┴──────────┴──────────┘   │
│            Kernel Core                  │
├─────────────────────────────────────────┤
│     Hardware Abstraction Layer (HAL)    │
├─────────────────────────────────────────┤
│  PS/2  │  ATA  │  PCI  │  RTC  │  PIT  │
└─────────────────────────────────────────┘
```

### Core Subsystems

| Subsystem | Description |
|-----------|-------------|
| **Scheduler** | Preemptive multitasking with round-robin arbitration, process state tracking, and context switching |
| **Memory Manager** | Paging-enabled Virtual Memory Manager with dynamic kernel heap and slab allocator |
| **VFS** | Virtual File System abstraction decoupling userspace from physical storage |
| **IPC** | UNIX-style signals and system call interfaces for inter-process communication |

---

## 🚀 Quick Start

### Prerequisites

Ensure you have the following tools installed:

```bash
# Required Tools
- i586-elf-gcc      # Cross-compiler
- i586-elf-as       # Assembler
- QEMU (i386)       # Emulator
- make              # Build system
- Linux/WSL/macOS   # Host environment
```

### Building GT-OS

```bash
# Clone the repository
git clone https://github.com/yourusername/GT-OS.git
cd GT-OS/osdev-source

# Clean previous builds
make clean

# Compile the kernel
make all
```

### Running in QEMU

```bash
# Boot the kernel
make start
```

**Default Login:**
- Username: `root`
- Password: `toor`

---

## 💻 User Space Interface

Upon boot, GT-OS drops you into a user-mode shell that communicates with the kernel through a Linux-compatible syscall interface.

### Available Commands

| Command | Description |
|---------|-------------|
| `ps` | Display running processes and PIDs |
| `ls` | List directory contents (VFS query) |
| `cat <file>` | Output file contents to stdout |
| `time` | Poll CMOS RTC for current time |
| `mod <module>` | Load/unload kernel modules dynamically |

---

## 📂 Project Structure

```
GT-OS/
├── osdev-source/
│   ├── arch/i386/          # x86 architecture-specific code
│   │   ├── boot.S          # Bootstrap assembly
│   │   └── interrupts.S    # Interrupt handlers
│   ├── kernel/             # Core kernel subsystems
│   │   ├── panic.c         # Kernel panic handler
│   │   ├── elf.c           # ELF binary loader
│   │   └── syscalls.c      # System call dispatcher
│   ├── mm/                 # Memory management
│   │   ├── pmm.c           # Physical memory manager
│   │   ├── vmm.c           # Virtual memory manager
│   │   └── heap.c          # Kernel heap allocator
│   ├── fs/                 # File system implementations
│   │   ├── vfs.c           # Virtual File System
│   │   └── ext2.c          # ext2 driver
│   ├── drivers/            # Hardware drivers
│   │   ├── screen.c        # VGA text mode
│   │   ├── keyboard.c      # PS/2 keyboard
│   │   └── ata.c           # ATA/PIO disk
│   └── include/            # System-wide headers
└── README.md
```

---

## 🧠 Design Philosophy

GT-OS embodies three core principles of systems programming:

### 1. **Concurrency Control**
Managing race conditions and synchronization in a preemptive multitasking environment

### 2. **Resource Abstraction**
Transforming raw electrical signals into elegant abstractions like files, streams, and processes

### 3. **Bare Metal Mastery**
Direct hardware interfacing through port I/O and memory-mapped registers—no safety nets

> This kernel is educational in nature but professional in structure, demonstrating that with curiosity and discipline, the computer's "black box" becomes a glass house.

---

## 🛠 Technical Specifications

<table>
<tr>
<td>

**Architecture**
- x86 (32-bit)
- Protected mode
- Ring 0/3 separation

</td>
<td>

**Binary Format**
- ELF loader
- Dynamic linking support
- Symbol resolution

</td>
<td>

**Interrupts**
- IDT management
- ISR handlers
- IRQ routing

</td>
</tr>
</table>

---

## 🤝 Contributing

Contributions are welcome! Areas of interest include:

- 🔌 Additional hardware drivers
- 📁 Filesystem optimization
- 🔧 POSIX compliance improvements
- 📚 Documentation enhancements

### Code Style
Please adhere to **K&R coding style** for consistency.

### Pull Request Process
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Gaurav Thakur**

*Concept, Architecture & Implementation*

> The name **GT-OS** reflects the personal nature of this architectural study. It stands as a testament to the fact that with enough curiosity and determination, the "black box" of the computer becomes transparent.

---

## 🌟 Acknowledgments

- The OSDev community for their invaluable resources
- The GNU toolchain developers
- QEMU project for excellent emulation
- Everyone who believes in understanding technology from the ground up

---

<div align="center">

### ⭐ Star this repo if you find it interesting!

**Built with passion for operating systems and low-level programming**

[Report Bug](https://github.com/yourusername/GT-OS/issues) • [Request Feature](https://github.com/yourusername/GT-OS/issues)

</div>
