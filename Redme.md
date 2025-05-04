
# Assignment Scripts Documentation

This repository contains setup scripts for **Assignment 10**, **Assignment 11**, and **Assignment 12**. Each script automates the installation and configuration of a web server and deployment environment for Node.js applications.

---

## 📁 Assignment 10

### 🔧 Script Overview

This script installs and starts the Nginx web server, installs Git, and sets up Node.js version 18.

### 🖥️ Script

```bash
#!/bin/bash
apt-get update
apt-get upgrade
apt-get install -y nginx
systemct1 start nginx
systemct1 enable nginx
apt-get install -y git
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
apt-get install -y nodejs
````

### ⚠️ Notes

* There is a **typo** in the script: `systemct1` should be `systemctl`. Make sure to correct it before running.
* This script **does not run any app**, it only sets up the environment.

---

## 📁 Assignment 11 & 12

### 🔧 Script Overview

This script builds upon Assignment 10 by:

* Installing required packages
* Cloning a GitHub repository
* Installing Node.js dependencies
* Running a Node.js application

### 🖥️ Script

```bash
#!/bin/bash
apt-get update
apt-get upgrade
apt-get install -y nginx
systemctl start nginx
systemctl enable nginx
apt-get install -y git
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
apt-get install -y nodejs
git clone https://github.com/dhOOpmon/ASS-9.git
cd ASS-9
npm install
node index.js
```

### 📦 Repository Used

* [`ASS-9`](https://github.com/dhOOpmon/ASS-9): A Node.js project that is cloned and executed by the script.

### ✅ Output

If successful, this script will start a Node.js server using the `index.js` file in the `ASS-9` repository.

---

## 💡 Tips

* Always run the scripts with `sudo` if needed.
* Ensure the system has network access to download packages and clone the repository.

