# Linux Directory Structure
### DevOps Study Notes • Linux Series #3 • Cloud With Shipra

---

## What is Linux?
Linux is an Operating System, just like Windows, but it is widely used for servers. In DevOps, Linux is a must-know skill because the servers you manage will commonly run Linux.

**⚠ Important** 
Linux does not use a C: drive or D: drive structure like Windows. Everything starts from one place: / (forward slash) = Root.

---

## FHS - Filesystem Hierarchy Standard
The Filesystem Hierarchy Standard (FHS) defines a common Linux filesystem structure. So, across distributions such as Ubuntu, CentOS and Amazon Linux, you will find a familiar directory layout.

**Easy way to remember**
Learn the standard directory structure once → the same basic idea works across Linux distributions.

### ★ Linux Directory Tree ★
```
  /   ← ROOT (everything starts here!)
  │
  ├── /bin    Basic commands: ls, cp, mv, cat
  ├── /sbin   Admin-only: fdisk, iptables
  ├── /etc    ★ ALL configuration files live here!
  ├── /home   Users' folders: /home/shipra
  ├── /root   Root user's home (different from /)
  ├── /var    Variable data → LOGS are here!
  │   └── /var/log  ← server logs
  ├── /tmp    Temporary files → DELETED on reboot!
  ├── /proc   Virtual filesystem → process info
  ├── /dev    Device files → /dev/null (black hole)
  ├── /usr    Installed programs: python, nginx
  ├── /boot   Bootloader: GRUB + kernel
  ├── /mnt    Manual mount point
  └── /media  Auto-mount: USB, CD-ROM
```

**⭐ Interview Important**
/ is the root directory. Every file and directory in the Linux filesystem exists under this root.

---

## Directory Details - Which Folder Does What?

1- /etc — Configuration
- /etc contains system configuration files such as nginx.conf, sshd_config and /etc/passwd.
- It is used for configuration, not for storing binaries/executables.
- Memory trick: “etc = Every Config is Here”
- ⭐ Very common interview topic.

2- /var → /var/log — Variable Data & Logs
- /var contains data that changes continuously. Server logs are commonly found under /var/log.
- When something goes wrong on a server, checking logs is an important troubleshooting step.
- DevOps tip: tail -f /var/log/syslog can be used for live log monitoring.

3- /tmp — Temporary Files
- /tmp is used for temporary files. The notes' key point: temporary files here are deleted when the system reboots.
- Do not keep important persistent data in /tmp.
- ⭐ Interview question: /var/tmp is different — according to these notes, it survives reboot.

4- /proc — Virtual Filesystem
- /proc is not a normal physical folder on disk. It is a virtual filesystem that provides real-time information about running processes and the kernel.
- Try: cat /proc/cpuinfo and cat /proc/meminfo

5- /dev — Device Files
- Linux represents hardware and devices through device files. Examples from the notes include /dev/sda for a hard disk and /dev/tty for a terminal.
- /dev/null = Linux “black hole” — data redirected there is silently discarded.

6- /home vs /root — Users
- /home contains directories for normal users, for example /home/shipra and /home/john.
- /root is the home directory of the root/admin user. It is different from the / root directory.
- Think: /home = general seating • /root = VIP cabin

7- /bin vs /usr/bin — Commands & Programs
- /bin contains core system commands such as ls, cp and cat. The notes describe these as commands needed early, including during boot/recovery situations.
- /usr/bin contains programs such as python, nginx and git.
- Memory idea: /bin = core/basic commands • /usr/bin = installed programs

---

### **Quick Map**
```
/etc = config
/var = variable data
/var/log = logs
/tmp = temporary
/proc = virtual
/dev = devices
/home = users
/root = root user's home
```

---

### Important Differences ⭐

```
Topic                                                    Key Difference
/ vs /root                                     / is the root of the entire Linux filesystem. /root is specifically the home directory of the root/admin user.
/home vs /root                                 /home contains normal users' directories. /root belongs to the root/admin user.
/tmp vs /var/tmp                               /tmp is temporary and, in these notes, is deleted on reboot. /var/tmp survives reboot.
/bin vs /usr/bin                               /bin contains core system commands. /usr/bin contains programs such as python, nginx and git.
/proc vs normal directories                    /proc is a virtual filesystem that exposes real-time process and kernel information.
/etc vs executable locations                   /etc is for system configuration files, not binaries/executables.
```

---

### Quick Revision
/ → Root of filesystem
/etc → Configuration
/var → Variable/changing data
/var/log → Server logs
/tmp → Temporary files
/proc → Virtual process/kernel info
/dev → Device files
/home → Normal users' folders
/root → Root user's home
/bin → Core commands
/usr/bin → Programs
/boot → GRUB + kernel
/mnt → Manual mount point
/media → Auto-mounted USB/CD-ROM

---

### ★ Interview Questions & Answers
Q1. What is the root directory in Linux?
Answer: / (forward slash) is the root directory. It is the starting point of the entire Linux filesystem, and every file and directory exists under it.

Q2. What is the purpose of /etc?
Answer: /etc contains system configuration files such as nginx.conf, sshd_config and /etc/passwd. The notes emphasize that it is for configuration, not executables/binaries.

Q3. What is the difference between /tmp and /var/tmp?
Answer: /tmp contains temporary files and, according to these notes, its files are deleted after reboot. /var/tmp is also used for temporary data, but its files persist after reboot.

Q4. What is /proc? Is it stored on disk?
Answer: No. /proc is a virtual filesystem. It provides real-time information about running processes and the kernel rather than being a normal physical directory on disk.

Q5. What is /dev/null?
Answer: /dev/null is like a Linux “black hole”. Anything redirected to it is silently discarded. It can be used to suppress unwanted output.

Q6. What is the difference between /bin and /usr/bin?
Answer: /bin contains core system commands such as ls, cp and cat. /usr/bin contains programs such as python, nginx and git.

---

## Practice Commands 💻
Run these commands in your Linux terminal and connect each command with the directory concept you learned.
Practice — Run in Terminal
```
ls / 
ls /etc 
ls /var/log 
cat /proc/cpuinfo 
echo "test" > /dev/null 
ls /home 
cat /proc/meminfo
```
