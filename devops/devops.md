# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Git](#git)
    - [git ref log](#git-ref-log)
    - [merge vs rebase](#merge-vs-rebase)
  - [Docker](#docker)
    - [Dockerfile Example](#dockerfile-example)
  - [Kubernetes](#kubernetes)
    - [Basic structure of a deployment.yaml file](#basic-structure-of-a-deploymentyaml-file)
  - [Linux](#linux)
    - [Describe the general file system hierarchy of a Linux system](#describe-the-general-file-system-hierarchy-of-a-linux-system)
    - [How to list all files, including hidden ones, in a directory?](#how-to-list-all-files-including-hidden-ones-in-a-directory)
    - [What is the Unix/Linux command to remove a directory and its contents?](#what-is-the-unixlinux-command-to-remove-a-directory-and-its-contents)
    - [Which command will show you free/used memory? Does free memory exist on Linux?](#which-command-will-show-you-freeused-memory-does-free-memory-exist-on-linux)
    - [How to search for the string in files of a directory recursively?](#how-to-search-for-the-string-in-files-of-a-directory-recursively)
    - [How to connect to a remote server or what is SSH?](#how-to-connect-to-a-remote-server-or-what-is-ssh)
    - [How to get all environment variables and how can you use them?](#how-to-get-all-environment-variables-and-how-can-you-use-them)
    - [What command will show the available disk space on the Unix/Linux system?](#what-command-will-show-the-available-disk-space-on-the-unixlinux-system)
    - [What commands do you know that can be used to check DNS records?](#what-commands-do-you-know-that-can-be-used-to-check-dns-records)
    - [What Unix/Linux commands will alter a files ownership, files permissions?](#what-unixlinux-commands-will-alter-a-files-ownership-files-permissions)
    - [What does chmod +x FILENAMEdo?](#what-does-chmod-x-filenamedo)
    - [How to add/remove a group from a user?](#how-to-addremove-a-group-from-a-user)
    - [What does CTRL-c do?](#what-does-ctrl-c-do)
    - [What is in /etc/services?](#what-is-in-etcservices)
    - [How to redirect STDOUT and STDERR in bash? (\> /dev/null 2\>\&1)](#how-to-redirect-stdout-and-stderr-in-bash--devnull-21)
    - [What is the diference between Telnet and SSH?](#what-is-the-diference-between-telnet-and-ssh)
    - [What command can be used to view the load averages?](#what-command-can-be-used-to-view-the-load-averages)
    - [What do the following commands do and how would you use them?](#what-do-the-following-commands-do-and-how-would-you-use-them)
    - [What does an \& after a command do?](#what-does-an--after-a-command-do)
    - [What does \& disown after a command do?](#what-does--disown-after-a-command-do)
    - [What is an A record, an NS record, a PTR record, a CNAME record, an MX record?](#what-is-an-a-record-an-ns-record-a-ptr-record-a-cname-record-an-mx-record)
    - [Explain briefly each one of the process states and all signals](#explain-briefly-each-one-of-the-process-states-and-all-signals)
    - [How to know which process listens on a specific port?](#how-to-know-which-process-listens-on-a-specific-port)
  - [References](#references)

## Git

### git ref log

`git reflog` shows a log of all changes made to the tips of branches (like `HEAD`), including those that are no longer visible in `git log`.

It's like a safety net — you can recover lost commits, even after `reset`, `rebase`, or `checkout`.

```bash
git reflog
--------------------------------------------
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
f4e5d6c HEAD@{1}: commit: Add login feature
```
You can restore a commit like this:
```bash
git checkout HEAD@{1}
```

**When to use**:

- You accidentally ran git reset --hard or lost commits after a rebase.
- You want to find an older state of your branch.

---

### merge vs rebase

- **git merge**:  

Combines two branches and keeps the full history.
Results in a merge commit. History stays branchy.
```bash
git checkout main
git merge feature-branch
```
Use merge when you want to preserve context and avoid rewriting history (e.g., in team environments).

- **git rebase**:  

Moves commits from one branch onto another, rewriting history.
Results in a linear history.

```bash
git checkout feature-branch
git rebase main
```

---

Use rebase when you want a clean, linear history, especially before pushing a feature branch.

## Docker

### Dockerfile Example

```Dockerfile
# Use an official Python base image
FROM python:3.11-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Define the default command to run the app
CMD ["python", "app.py"]
```

**How to use it**:

```bash
# Build the Docker image from the Dockerfile in the current directory
docker build -t my-python-app .                    # -t names the image "my-python-app"

# Run a container from the built image
docker run -d -p 5000:5000 my-python-app           # -d runs in background, -p maps port 5000 (host:container)

# List running containers to get the container ID or name
docker ps                                          # shows active containers

# Open an interactive shell in the running container
docker exec -it <container_id_or_name> /bin/bash   # useful for debugging or inspecting the container

```

---

## Kubernetes

### Basic structure of a deployment.yaml file

```yaml
apiVersion: apps/v1                # API version of the Deployment
kind: Deployment                   # Type of Kubernetes resource
metadata:
  name: my-app                     # Name of the deployment
  labels:
    app: my-app                    # Labels for selection and grouping
spec:
  replicas: 2                      # Number of pod replicas
  selector:
    matchLabels:
      app: my-app                  # Select pods with this label
  template:
    metadata:
      labels:
        app: my-app                # Label pods (must match selector)
    spec:
      containers:
        - name: my-container       # Name of the container
          image: nginx:1.21        # Docker image to use
          ports:
            - containerPort: 80    # Port the container exposes
```
**How to use it**:

```bash
kubectl apply -f deployment.yaml   # Create or update
kubectl get deployments            # Verify deployment is created
kubectl get pods                   # See the running pods
kubectl delete -f deployment.yaml  # Delete deployment and its pods
```

---

## Linux

### Describe the general file system hierarchy of a Linux system

`/` - root folder
`/etc` - configuration files provided by the package manager
`/bin` - binaries files
`/sbin` - system binaries files (important binaries for the OS)
`/boot` - Static files for boot processes ( boot loader)
`/dev` - Device files
`/lib` - Essential shared libraries and kernel modules
`/usr` - Secundary hierarchy
`/mnt` - Mounting point for temporary filesystem
`/media` - Mounting point for removable media
`/opt` - Add-on application software packages
`/srv` - Data service provided by this system
`/tmp` - Temporary files
`/var` - Variable data
`/root` - Root user folder
`/home` - Home users folders

---

### How to list all files, including hidden ones, in a directory?
```shell
ls -a
```
or
```shell
find .
```

---

### What is the Unix/Linux command to remove a directory and its contents?

```shell
rm -R
```

---

### Which command will show you free/used memory? Does free memory exist on Linux?

```shell
free
```
Sure exists, but the Linux kernel creates file caches in ram, so when we see the output from free command, sometimes can show us that we are without memory but this memory is cached by the OS.

---

### How to search for the string in files of a directory recursively?

```shell
grep -Rin "string-to-search" /folder
```

---

### How to connect to a remote server or what is SSH?

SSH (secure shell) it's a cryptographic network protocol, used for remote login to computer systems by users.

```shell
ssh user@server
```

### How to get all environment variables and how can you use them?

`env` or `printenv`, will show every variable that login session, we can use setting   
as variables ex.: TEST=something or using export the variable will be global (can be used by all system users).

---

### What command will show the available disk space on the Unix/Linux system?

```shell
df -h
``` 

---

### What commands do you know that can be used to check DNS records?

- `dig +trace`
- `nslookup`
- `whois`
- `host`

---

### What Unix/Linux commands will alter a files ownership, files permissions?

- `chmod`
- `chown`
- `chattr`

---

### What does chmod +x FILENAMEdo?

Add a execute permission to a file for all users

---

### How to add/remove a group from a user?

- `usermod -a -G groupname username` - add a user in a new group`
- `usermod -G <groups> username` - add the user in all groups`
- `newgrp` - updates shell session with new group permissions`

---

### What does CTRL-c do?

send a `SIGINT` to the terminal (it's a polite kill)

---

### What is in /etc/services?

A mapping for services and ports, when a service call a function `getportbyname()` usually this function  
goes in this file to check.
Example the command `netstat` or `ss` without the `-n` parameter

---

### How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)

- `1>` - redirect the STDOUT
- `1>>` - redirect the STDOUT in append mode
- `2>` - redirect the STDERR
- `2>>` - redirect the STDERR in append mode
- `&>` - redirect both STDERR and STDOUT
- `&>>` - redirect both STDERR and STDOUT in append mode
- `2>&1` - redirect STDERR to STDOUT

---
### What is the diference between Telnet and SSH?

- SSH it's encrypted and telnet isn't
- Telnet can ommit authentication
- SSH adds overhead to the bandwidth
 
---

### What command can be used to view the load averages?

The three load averages indicate the processor usage estimated in 1 minute, estimated in 5 minutes and 15 minutes.

- `top`
- `uptime`

---

### What do the following commands do and how would you use them?

- `tee` - copies the STDOUT to a file, but continues to show the STDOUT
- `awk` - awk it's a programming language designed for text processing
- `tr` - tr or translate, it's a command to substitute characters
- `cut` - cut is a command for text processing and extracts a portion of a text
- `tac` - tac it's a reverse cat, pritting the file bottom to up
- `curl` - curl or cURL is a tool to transfer data from or to a server, using one of the supported protocols
- `wget` - wget is a tool for retrieving files using HTTP, HTTPS , or FTP
- `watch` - Watch it's a tool that runs a specified command repeatedly and displays the result on standard output
- `head` - it's a command that shows the first lines of a file, the default it's 10 lines
- `tail` - it's a command that shows the last lines of a file, the default it's 10 lines

---

### What does an & after a command do?

Makes the command run in a background sub shell, and becomes a job.

---

### What does & disown after a command do?

`disown` control jobs that are running in the system, without any paramenter or ID removes the last job on the job table.

---

### What is an A record, an NS record, a PTR record, a CNAME record, an MX record?

- `A` record stands for address, indicates an IP address for a domain
- `NS` stands for Name Server record indicates which DNS server is authoritative for that domain  
( where the actual DNS entries are)
- `CNAME` stands for canonical name and servers to make one domain to another domain name.
- `MX` stands for mail exchange, it's a list of mail exchange servers used by the domain.

---

### Explain briefly each one of the process states and all signals

  - **CREATED** or **NEW STATE**, in this moment the process wait the admission to the ready state, by the scheduler
  - **RUNNING/RUNNABLE** (R) the process has been loaded into main memory and is awaiting execution by the CPU, or it's using CPU core right now
  - **SLEEPING** a sleeping process is a process waiting for a resource to be available, I/O operation to complete for example, or an event to happen. There is two states of SLEEPING process
    - **Interrruptible Sleep** (S) - Process that can be terminated before the wake up condition is fulfilled without any consequences.
    - **Uninterruptible Sleep** (D) - Process that can't be killed, in the example of I/O operation, the act the process it's in uniterruptible sleep (D) until a the I/O operation to complete and wake up.
  - **STOPPED** (T) - A process becomes stopped when it receives the SIGSTOP signal, when stopped the process execution is suspended and only signals it will handle are SIGKILL and SIGCONT
  - **Zombie** (Z) it's a state after completing the execution or being explicitly killed, but the process remains as a zombie until the parent process call the wait system call to read its exit status, and finally ending the process lifetime.
  - Process SIGNALS are one of the ways process communicate among themselves and with the kernel. Exceptionally SIGKILL and SIGSTOP signals cannot be handled or blocked.
    - **SIGTERM** - the default signal sent by kill command, Asks the process to terminate voluntarily
    - **SIGKILL** - unlike SIGTERM, forces the process to terminate, can't be blocked or handled
    - **SIGSTOP** - suspend the process execution, putting in stopped state. In this state, the process will do nothing but accept SIGKILL or SIGCONT.
    - **SIGSTP** - almost identical to SIGSTOP, the only difference is it can be blocked or handled, this is the signal sent when you type `<ctrl>+z` in the terminal
    - **SIGCONT** - if a process is in stopped state, it will put it back in the RUNNING/RUNNABLE state and resume it execution. If the process is in any other state, it's silently ignored.
    - **SIGINT** - generated when the user type `<ctrl>+c` in the terminal, it interrupts the current command processing and wait for user's next command.
    - **SIGQUIT** - generated when eht user type `<ctrl>+\` in the terminal, normally it will force the process to produce a core dump and terminate.
    - **SIGALARM** - signal used to wake up sleeping process, normally scheduled by alarm system call.
    - **SIGCHLD** - sinal send from a child process to its parent process when its state changes.
    - **SIGHUP** - the signal indicates the terminal handling the process has been disconnected and/or parent process terminated. To run a process that won't terminate when the terminal disconnects, you can start it using the command `nohup`.

---

### How to know which process listens on a specific port?

- `lsof -i :$PORT`
- `netstat -lp | grep $port`
- `ss -lp | grep $port`
 
---

## References
 - https://github.com/gracco/sysadmin-interview-questions/blob/master/README.md
    