# TryHackMe — Pre-Security: Operating Systems, Windows & Linux Basics

**Date:** June 10, 2026
**Path:** Pre-Security — in progress
**Status:** 🔄 In progress

---

## What is an Operating System?
The OS sits between user, applications, and hardware — the invisible
manager keeping everything running as one unified system.

**Airport analogy:**
- Hardware = runways, planes, fuel systems
- Applications = airlines and passengers
- OS = air traffic control system

---

## System Privilege Layers

| Layer | What it is | Access |
|-------|-----------|--------|
| Kernel Space | Core OS — manages hardware directly | Unrestricted — CPU, memory, storage |
| User Space | Where apps run | Restricted — must make system calls |

**System calls** = apps requesting the kernel to act on their behalf
(open file, play sound, connect to WiFi)

---

## OS Core Responsibilities

| Responsibility | What it does | Example |
|---------------|-------------|---------|
| Process Management | Schedules and prioritizes running programs | Multitasking without freezing |
| Memory Management | Allocates RAM, isolates processes, uses virtual memory | Multiple apps open at once |
| File System Management | Organizes files, handles permissions and metadata | Saving files, setting read-only |
| User Management | Handles accounts, authentication, permissions | Login keeping your files private |
| Device Management | Loads drivers, provides hardware abstraction | Plugging in a mouse and it works |

---

## OS Security Functions
Before any antivirus or firewall — the OS already handles:
- **Authentication** — verifies identity via login/biometrics
- **Permissions** — controls what each user and app can read/write/execute
- **Isolation** — keeps processes in protected boxes
- **System Protection** — safeguards critical system files

---

## GUI vs CLI

| | GUI | CLI |
|-|-----|-----|
| Interaction | Click icons and menus | Type text commands |
| Precision | Lower | Higher |
| Speed | Slower for complex tasks | Faster for advanced tasks |
| Learning curve | Easy | Requires command knowledge |

---

## OS Types

| Type | Use Case | Examples |
|------|---------|---------|
| Desktop | Personal computers, gaming | Windows 11, macOS, Ubuntu |
| Server | Web hosting, databases, cloud | Windows Server, Ubuntu Server, Red Hat |
| Mobile | Smartphones, tablets | Android, iOS |
| Embedded | IoT, cars, routers | FreeRTOS, OpenWrt |
| Virtual/Cloud | VMs, containers, cloud | Alpine Linux, Amazon Linux |

---

## Windows Basics

### Account Types
| Type | Access Level |
|------|-------------|
| Guest | Minimal — temporary access only |
| Standard | Everyday tasks, no system-wide changes |
| Administrator | Full control — install software, manage users |

### Windows Desktop Components
1. **Desktop** — main workspace with shortcuts
2. **Taskbar** — access to apps, settings, notifications
3. **Start Menu** — quick access to all apps, settings, power
4. **Search** — find apps, files, settings
5. **Task View** — see all open windows
6. **Task Manager** — monitor running processes and performance

### Task Manager Tabs
| Tab | Purpose |
|-----|---------|
| Processes | Running apps and background processes + resource usage |
| Performance | CPU, memory, network graphs |
| Users | Currently logged-in users |
| Details | Technical view with Process IDs (PIDs) |
| Services | Windows services and their status |

### Windows File System
- Hierarchical folder structure
- Common locations: Desktop, Documents, Downloads
- Full path example: `C:\Users\Administrator\Desktop\Folder`

### Installing/Updating Apps
- **Microsoft Store** — curated safe installs
- **From internet** — .exe or .msi installer from vendor website
- **Windows Update** — keeps OS and native apps updated
- **Uninstall** — via Settings → Add/Remove Programs or Control Panel

### Windows Security Tools
| Tool | Purpose |
|------|---------|
| Virus & Threat Protection | Real-time malware detection and scans |
| Firewall & Network Protection | Controls incoming/outgoing traffic |
| App & Browser Control | Blocks unsafe apps and websites |
| Device Security | Hardware-based system protection |

### Windows Defender Firewall Profiles
| Profile | When used |
|---------|----------|
| Domain | Connected to organization's domain network |
| Private | Trusted networks — home or lab |
| Public | Untrusted networks — public WiFi |

---

## Linux CLI Basics

### Why CLI in Cybersecurity?
- Faster than clicking around
- More control and precision
- Most security tools only run in terminal

### Core Navigation Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `pwd` | Print working directory — shows where you are | `/home/ubuntu` |
| `ls` | List files and folders in current directory | `ls` |
| `ls -l` | Detailed list with permissions, size, dates | `ls -l` |
| `ls -al` | Show all files including hidden ones | `ls -al` |
| `cd <dir>` | Change directory | `cd Documents` |
| `cd ..` | Go back one level | `cd ..` |
| `find ~ -name <file>` | Find file by name starting from home | `find ~ -name mission_brief.txt` |
| `cat <file>` | Read and display file contents | `cat mission_brief.txt` |

### Hidden Files in Linux
- Files starting with `.` are hidden by default
- Use `ls -al` to see them
- They're not secret — just hidden from regular `ls`

### Linux File Path Structure
- `~` = home directory shortcut
- `/home/ubuntu` = full path to home
- Navigate with `cd` and confirm location with `pwd`

---

## Key Takeaways
- OS manages hardware, memory, processes, files, users, and devices
- Kernel space has full hardware access — user space does not
- System calls are how apps communicate with the kernel
- GUI = clicks, CLI = commands — both do the same things
- Windows has three account types — Administrator has full control
- Task Manager shows real-time system and process information
- Linux CLI is essential for cybersecurity work
- `pwd`, `ls`, `cd`, `find`, `cat` are your first 5 Linux commands
- Hidden files in Linux start with `.` — use `ls -al` to see them
