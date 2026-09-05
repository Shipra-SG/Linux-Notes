# Linux Basic File Commands

## Part 1 — Check Your Current Location

### pwd — Print Working Directory
```
pwd
```
Before working with directories, first check where you are. pwd means Print Working Directory. It tells you the current location in the Linux filesystem.
```
/home/shipra
```
If the output is /home/shipra, that means the current directory is /home/shipra. From this location, we can start learning ls.

---

## Part 2 — ls Command

### 1. Basic ls
```
ls
```
ls is used to list the files and directories available inside the current directory.
```
Desktop
Documents
Downloads
Pictures
test.txt
```
So, ls basically answers: “What is available inside my current directory?”

### 2. ls -l — Long Listing Format
```
ls -l
```
Normal ls mainly shows names. With -l, we get detailed information such as permissions, owner, group, size and modification time.
```
-rw-r--r-- 1 shipra shipra  1250 Sep  5 10:20 test.txt
drwxr-xr-x 2 shipra shipra  4096 Sep  5 10:25 Documents
```
**Meaning**
```
-rw-r--r--	Permissions
shipra	Owner
shipra	Group
1250	Size
Sep 5 10:20	Last modification time
test.txt	File name
```
⭐ Interview Important
Remember ls -l = long listing / detailed information. Permissions will be covered separately, so for now focus on recognizing the fields.

### 3. ls -a — Show Hidden Files
```
ls -a
```
-a means all. It shows hidden files and directories as well. In Linux, files and directories beginning with . are normally hidden.
```
.
..
.bashrc
.profile
.config
Documents
Downloads
```
For example, .bashrc may not appear with normal ls, but it appears with ls -a.

### 4. ls -lh — Human-Readable Sizes
```
ls -lh
```
Here, -h means human-readable. It is commonly used together with -l so that detailed file information is shown with easier-to-read file sizes.

### 5. ls -lt — Sort by Modification Time
```
ls -lt
```
-t sorts files according to their modification time. Recently modified files generally appear near the top.

- Linux command options can be combined when you need multiple behaviors at the same time.
```
ls -lht
```
Flag	Meaning
-l	Long / detailed listing
-h	Human-readable sizes
-t	Sort by modification time

```
ls -la
```
Flag	Meaning
-l	Detailed listing
-a	Include hidden files

---

## Part 3 — cd Command
cd — Change Directory
```
cd
```
cd means Change Directory. It is used to move from the current directory into another directory.

First, check the current location:
```
pwd
```
```
/home/shipra
```

Now move into the Documents directory:
```
cd Documents
pwd
```
```
/home/shipra/Documents
```
We moved from /home/shipra into /home/shipra/Documents.

### cd .. — Move to Parent Directory
```
cd ..
```
.. represents the parent directory. If you are here:

```
/home/shipra/Documents
```

then:
```
cd ..
```

takes you back to:
```
/home/shipra
```

### cd / — Go to Root
```
cd /
pwd
```
```
/
```
This takes you directly to the Linux root directory, represented by /.

### cd ~ — Go to Home Directory
```
cd ~
pwd
```
~ generally represents the current user's home directory. For the example user shipra, it represents:
```
/home/shipra
```
So cd ~ can be used to return directly to your home directory.

---

## Part 4 — Absolute Path vs Relative Path
This is an important concept when using cd. The difference is based on where the path starts from.

### Absolute Path
Suppose you want to go to:
```
/home/shipra/Documents
```

You can specify the complete path:
```
cd /home/shipra/Documents
```
This is an absolute path. It starts from /, the root of the filesystem, and specifies the complete location.

### Relative Path
Suppose you are already here:
```
/home/shipra
```

and you want to enter Documents:
```
cd Documents
```
This is a relative path because the current directory is used as the starting point.

```
Absolute Path	                                                                 Relative Path
cd /home/shipra/Documents 	                                                     cd Documents
Starts from / and gives the complete location. 	                             Starts from the current directory.
Describes a fixed location from the filesystem root. 	                       Describes a location relative to where you currently are.
```

---

## Part 5 — mkdir Command

### mkdir — Make Directory
```
mkdir
```
mkdir means Make Directory. It is used to create a new directory.

Basic Example
```
mkdir linux-practice
ls
```
After running the command, linux-practice should appear in the listing. This means the new directory has been created successfully.

Enter the New Directory-
```
cd linux-practice
pwd
```
Now you are inside the newly created directory.

### mkdir -p — Create Nested Directories
-p is an important option when you want to create a directory structure where the parent directories may not already exist.

Suppose you want this structure:
```
project
└── linux
    └── commands
```
If the parent directories do not already exist, this may fail:
```
mkdir project/linux/commands
```

In that situation, use:
```
mkdir -p project/linux/commands
```
The -p option creates the required parent directories as needed. So the command can create the complete nested structure:
```
project
   ↓
linux
   ↓
commands
```

---

## Final Practical — Complete Mini Exercise
Now combine the commands from this lesson into one small practice exercise.

Step 1 — Go to your home directory
```
cd ~
```

Step 2 — Create the directory structure
```
mkdir -p linux-practice/day1
```

Step 3 — Enter the new directory
```
cd linux-practice/day1
```

Step 4 — Check your current location
```
pwd
```

Step 5 — List the directory
```
ls
```

Step 6 — Move to the parent directory
```
cd ..
```

Step 7 — Check your location again
```
pwd
```

Step 8 — Show hidden files too
```
ls -la
```

Step 9 — Detailed listing with readable sizes
```
ls -lh
```

Step 10 — Sort by modification time
```
ls -lt
```

---

## Quick Revision

- pwd	= Print Working Directory → shows your current location
- ls = List files and directories
- ls -l =	Detailed/long listing
- ls -a	= Show hidden files and directories
- ls -lh = Detailed listing + human-readable sizes
- ls -lt = Sort by modification time
- ls -lht	= Detailed + human-readable + time sorting
- ls -la	= Detailed listing + hidden files
- cd directory	= Move into a directory
- cd ..	= Move to parent directory
- cd /	= Move to root directory
- cd ~	= Move to current user's home directory
- mkdir	= Create a new directory
- mkdir -p	= Create nested directories with required parent directories

---

## Important Interview Questions & Answers
Q1. What is the use of the ls command?
Answer: ls is used to list the files and directories in the current directory.

Q2. What is the difference between ls -l and ls -a?
Answer: ls -l gives a detailed listing, while ls -a also shows hidden files and directories.

Q3. What is the use of ls -lh?
Answer: -l provides a detailed listing and -h displays file sizes in a human-readable format.

Q4. What does ls -lt do?
Answer: It sorts files according to their modification time, generally showing recently modified files near the top.

Q5. What does cd .. do?
Answer: It moves from the current directory to its parent directory.

Q6. What is the difference between an absolute path and a relative path?
Answer: An absolute path starts from the root / and specifies the complete location. A relative path uses the current directory as its starting point.

Q7. What is the use of mkdir -p?
Answer: mkdir -p creates the required parent directories as well, making it useful for creating nested directory structures.
