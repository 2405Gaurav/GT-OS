# 🚀 Cuttrix

> *Where operating systems meet passion, and code becomes art.*

Hey there! 👋 Welcome to **Cuttrix** — my personal playground for exploring the depths of operating system development. If you're here, you're probably curious about what goes on under the hood of computers, or maybe you're just as fascinated by low-level programming as I am. Either way, you're in the right place!

---

## 🌟 What's This All About?

This repository is home to **LevOS** — a custom operating system kernel I've been building from scratch. It's not just another OS project; it's a journey into understanding how computers really work, from the bootloader to user space.

### The Heart of It All: LevOS

**LevOS** (version 4.0) is a fully functional, albeit experimental, operating system kernel that runs on x86 architecture. It's built with passion, curiosity, and a whole lot of late-night coding sessions. Here's what makes it special:

#### ✨ Core Features

- **🔄 Multitasking** - Round-robin scheduling with preemptive multitasking
- **💾 Memory Management** - Full paging support with dynamic memory allocation
- **📁 Virtual File System** - A beautiful abstraction layer supporting multiple filesystems
- **💿 Filesystem Support** - ext2 (read/write), procfs, devfs
- **⌨️ Hardware Support** - Keyboard, ATA drives, floppy disks, PCI, RTC
- **🎯 ELF Execution** - Run compiled programs on the kernel
- **🔌 Module System** - Load and unload kernel modules dynamically
- **📞 System Calls** - Linux-like syscall interface
- **🎨 Text Mode Display** - Beautiful console with printf support

#### 🛠️ Technical Highlights

- **Multiboot compliant** bootloader
- **GDT/IDT** setup for protected mode
- **Interrupt handling** with PIC/PIT
- **DMA support** for efficient data transfer
- **Device abstraction layer** for hardware management
- **Process management** with PID tracking

---

## 🎯 Why Should You Care?

Whether you're:
- **A student** learning OS internals
- **A developer** curious about low-level programming
- **A hobbyist** fascinated by how computers boot
- **Someone** who just stumbled here by accident

...this project offers insights into the beautiful complexity of operating systems. Every line of code here was written with the goal of understanding, not just implementing.

---

## 🚦 Getting Started

### Prerequisites

You'll need:
- A cross-compiler toolchain (`i586-elf-gcc`, `i586-elf-as`)
- QEMU for emulation
- A Unix-like environment (WSL works great on Windows!)
- Curiosity and patience 😊

### Building LevOS

```bash
cd osdev-source
make all
```

### Running It

```bash
make start
```

This will launch QEMU with the kernel. You'll be greeted by a login screen — use `root` / `toor` to log in.

### Available Commands

Once you're in, try these commands:
- `help` - Show available commands
- `ps` - List running processes
- `ls` - List directory contents
- `cat <file>` - Display file contents
- `time` - Show current time
- `clear` - Clear the screen
- `reboot` - Reboot the system

---

## 📂 Project Structure

```
cuttrix/
├── osdev-source/          # The main OS kernel source
│   ├── arch/              # Architecture-specific code (x86)
│   ├── drivers/           # Hardware drivers
│   ├── fs/                # Filesystem implementations
│   ├── kernel/            # Core kernel functionality
│   ├── memory/            # Memory management
│   └── ...
├── apply_rewrite.py       # Git history tools
└── README.md              # You are here!
```

---

## 💭 A Personal Note

Building an operating system is one of the most challenging and rewarding projects you can undertake. It forces you to understand:
- How CPUs really work
- How memory is managed
- How hardware communicates
- How software layers interact

This project represents countless hours of learning, debugging, and discovery. It's not perfect, and it's not meant to be production-ready. It's a learning journey, and I'm sharing it with you in the hopes that it might inspire your own exploration.

---

## 🤝 Contributing

Found a bug? Have a suggestion? Want to add a feature? I'd love to hear from you! Feel free to:
- Open an issue
- Submit a pull request
- Share your thoughts

This is a learning project, and collaboration makes it better for everyone.

---

## 📚 Learning Resources

If you're interested in OS development, here are some resources that helped me:
- [OSDev Wiki](https://wiki.osdev.org/) - The ultimate OS development resource
- [JamesM's kernel tutorials](https://web.archive.org/web/20160412174753/http://www.jamesmolloy.co.uk/tutorial_html/)
- [Bran's Kernel Development Tutorial](https://www.osdev.org/forum/viewtopic.php?t=10247)

---

## ⚠️ Disclaimer

This is experimental software. It's not meant for production use, and running it on real hardware could potentially cause issues. Always use emulation (QEMU) for testing.

---

## 📝 License

This project is open source and available for educational purposes. Feel free to learn from it, modify it, and share your improvements!

---

## 🌈 Final Thoughts

If you've made it this far, thank you for taking the time to explore this project. Whether you're here to learn, contribute, or just satisfy your curiosity, I hope you find something interesting.

Remember: every expert was once a beginner. Every operating system started with a single line of code. This is my contribution to that journey, and I'm excited to see where it leads.

Happy coding! 🎉

---

*Made with ❤️ and lots of ☕*
